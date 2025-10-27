#Fiz a mutação do resíduo pelo pymol, pela opção mutagenesis (escolher a melhor posição do novo resíduo, ou seja, a que tiver menos impedimentos estericos)

#Renumerar o scFv e definir como cadeia A
gmx24 editconf -f ofa-Y105A.pdb -o ofa-Y105A-resnr.pdb -label A -resnr 1

#Gerei uma nova topologia para o scFv mutado
gmx24 pdb2gmx -f ofa-Y105A-resnr.pdb -i -o conf.gro -ss -his -ter

#Editei a topologia gerada aplicando as restrições como estavam definidas do arquivo de restrição gerado pelo charmmgui para o scFv nativo (com atenção para os átomos correspondentes aos resíduo
s mutados)
#Inclui a topologia do scFv mutado na topologia geral do sistema topol.top
#Incluir as coordenadas do scFv corretamente no arquivo PDB geral, para não dar problema posteriormente com o match com a topologia na ordem dos átomos

#Transformando o pdb para gro
gmx24 trjconv -f ofa-Y105A-cd20-md7.pdb -s ofa-Y105A-cd20-md7.pdb -o ofa-Y105A-cd20-md7.gro

#Definindo as dimensões da caixa, eixos X e Y com as mesmas dimensões do .gro gerado pelo CHARMM-GUI, alterei apenas o eixo Z
gmx24 editconf -f ofa-Y105A-cd20-md7.gro -box 13.26009  13.26009  17.00000 -o out.gro

#Definindo os centros da caixa, no eixo Z desci um pouco
gmx24 editconf -f out.gro -center 6.67361 6.67361  11.0000 -o out1.gro

#Minimizacao com steep
gmx24 grompp -f step6.0_minimization.mdp -c out1.gro -p topol.top -o em1.tpr -r out1.gro -maxwarn 1
gmx24 mdrun -nice 4 -s em1.tpr -deffnm em1 -v

Steepest Descents converged to Fmax < 1000 in 460 steps
Potential Energy  = -8.1062445e+04
Maximum force     =  7.7347839e+02 on atom 62669
Norm of force     =  1.7768636e+01

#Minimizacao com cg
gmx24 grompp -f step6.1_minimization.mdp -c em1.gro -p topol.top -o em2.tpr -r em1.gro -maxwarn 1
gmx24 mdrun -nice 4 -s em2.tpr -deffnm em2 -v

Polak-Ribiere Conjugate Gradients converged to Fmax < 1000 in 0 steps
Potential Energy  = -8.1011594e+04
Maximum force     =  6.5327527e+02 on atom 21948
Norm of force     =  1.0835828e+02

#Minimizacao com steep
gmx24 grompp -f step6.2_minimization.mdp -c em2.gro -p topol.top -o em3.tpr -r em2.gro -maxwarn 1
gmx24 mdrun -nice 4 -s em3.tpr -deffnm em3 -v

Steepest Descents converged to Fmax < 1000 in 5 steps
Potential Energy  = -8.1510336e+04
Maximum force     =  7.3701074e+02 on atom 62158
Norm of force     =  6.8954527e+01

#Solvatar o sistema (fiz essa etapa no cluster, sem entrar no nó)
/local/softs/gromacs-513/bin/gmx solvate -cp em3.gro -cs -o em3-solvatado.gro -p topol.top -radius 0.5

#Gerar um tpr para tratar o .gro e gerar um pdb
gmx grompp -f step6.2_minimization.mdp -c em3-solvatado.gro -p topol.top -o em3-solv.tpr -r em3-solvatado.gro -maxwarn 1

#Tratar e gerar um pdb
gmx trjconv -f em3-solvatado.gro -s em3-solv.tpr -o em3.pdb -pbc cluster -center
gmx trjconv -f em3.pdb -s em3-solv.tpr -o em3.pdb -pbc mol -center