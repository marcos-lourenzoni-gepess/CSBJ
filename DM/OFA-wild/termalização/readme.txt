gmx make_ndx -f ../minimizacao/em3-solvatado.gro -o index.ndx
para criar os grupos PROT, MEMB e SOL

#NPT
gmx grompp -f npt1.mdp -c ../minimizacao/em3-solvatado.gro -p ../minimizacao/topol.top -o pr1.tpr -n index.ndx -maxwarn 1 -r ../minimizacao/em3-solvatado.gro
gmx mdrun -nice 4 -s pr1.tpr -deffnm pr1 -v
gmx trjconv -f pr1.gro -s pr1.tpr -o pr1.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr1.pdb -s pr1.tpr -o pr1.pdb -pbc mol -center -n index.ndx

gmx grompp -f npt2.mdp -c pr1.gro -p ../minimizacao/topol.top -o pr2.tpr -n index.ndx -maxwarn 1 -r pr1.gro
gmx mdrun -nice 4 -s pr2.tpr -deffnm pr2 -v
gmx trjconv -f pr2.gro -s pr2.tpr -o pr2.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr2.pdb -s pr2.tpr -o pr2.pdb -pbc mol -center -n index.ndx

gmx grompp -f npt3.mdp -c pr2.gro -p ../minimizacao/topol.top -o pr3.tpr -n index.ndx -maxwarn 1 -r pr2.gro
gmx mdrun -nice 4 -s pr3.tpr -deffnm pr3 -v
gmx trjconv -f pr3.gro -s pr3.tpr -o pr3.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr3.pdb -s pr3.tpr -o pr3.pdb -pbc mol -center -n index.ndx

#NVT
gmx grompp -f nvt4.mdp -c pr3.gro -p ../minimizacao/topol.top -o pr4.tpr -r pr3.gro -n index.ndx -maxwarn 1
gmx mdrun -nice 4 -s pr4.tpr -deffnm pr4 -v
gmx trjconv -f pr4.gro -s pr4.tpr -o pr4.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr4.pdb -s pr4.tpr -o pr4.pdb -pbc mol -center -n index.ndx

gmx grompp -f nvt5.mdp -c pr4.gro -p ../minimizacao/topol.top -o pr5.tpr -r pr4.gro -n index.ndx -maxwarn 1
gmx mdrun -nice 4 -s pr5.tpr -deffnm pr5 -v
gmx trjconv -f pr5.gro -s pr5.tpr -o pr5.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr5.pdb -s pr5.tpr -o pr5.pdb -pbc mol -center -n index.ndx

gmx grompp -f nvt6.mdp -c pr5.gro -p ../minimizacao/topol.top -o pr6.tpr -r pr5.gro -n index.ndx -maxwarn 1
gmx mdrun -nice 4 -s pr6.tpr -deffnm pr6 -v
gmx trjconv -f pr6.gro -s pr6.tpr -o pr6.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr6.pdb -s pr6.tpr -o pr6.pdb -pbc mol -center -n index.ndx

#NPT

gmx grompp -f npt7.mdp -c pr6.gro -p ../minimizacao/topol.top -o pr7.tpr -r pr6.gro -n index.ndx -maxwarn 1
gmx mdrun -nice 4 -s pr7.tpr -deffnm pr7 -v
gmx trjconv -f pr7.gro -s pr7.tpr -o pr7.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr7.pdb -s pr7.tpr -o pr7.pdb -pbc mol -center -n index.ndx

gmx grompp -f npt8.mdp -c pr7.gro -p ../minimizacao/topol.top -o pr8.tpr -r pr7.gro -n index.ndx -maxwarn 1
gmx mdrun -nice 4 -s pr8.tpr -deffnm pr8 -v
gmx trjconv -f pr8.gro -s pr8.tpr -o pr8.pdb -pbc cluster -center -n index.ndx
gmx trjconv -f pr8.pdb -s pr8.tpr -o pr8.pdb -pbc mol -center -n index.ndx

#Adicionando ions
gmx grompp -f ions.mdp -c pr8.gro -p sistema.top -o ions.tpr
gmx genion -s ions.tpr -p sistema.top -o sistema-ion.gro -np 179 -pname SOD -nn 185 -nname CLA -neutral

#Criar um novo index para incluir os ions e criar um novo grupo SOL_IONS
gmx make_ndx -f sistema-ion.gro -o index-1.ndx

#Ultimas etapas de termalizacao em NPT
gmx grompp -f npt9.mdp -c sistema-ion.gro -p sistema.top -o pr9.tpr -r sistema-ion.gro -n index-1.ndx
gmx mdrun -nice 4 -s pr9.tpr -deffnm pr9 -v
gmx trjconv -f pr9.gro -s pr9.tpr -o pr9.pdb -pbc cluster -center -n index-1.ndx
gmx trjconv -f pr9.pdb -s pr9.tpr -o pr9.pdb -pbc mol -center -n index-1.ndx

gmx grompp -f npt10.mdp -c pr9.gro -p sistema.top -o pr10.tpr -r pr9.gro -n index-1.ndx
gmx mdrun -nice 4 -s pr10.tpr -deffnm pr10 -v
gmx trjconv -f pr10.gro -s pr10.tpr -o pr10.pdb -pbc cluster -center -n index-1.ndx
gmx trjconv -f pr10.pdb -s pr10.tpr -o pr10.pdb -pbc mol -center -n index-1.ndx