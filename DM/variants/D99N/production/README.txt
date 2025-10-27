gmx24 grompp -f md1.mdp -c ../termalizacao/pr11.gro -p ../termalizacao/sistema.top -n ../index-1.ndx  -o md1.tpr
nohup gmx24 mdrun -nb gpu -nice 4 -s md1.tpr -deffnm md1 -v -nt 5 -pme gpu -gpu_id 4 -pin off >& saida-md
1.log&
gmx24 grompp -f md2.mdp -c md1.gro -p ../termalizacao/sistema.top -n ../index-1.ndx  -o md2.tpr
nohup gmx24 mdrun -nb gpu -nice 4 -s md2.tpr -deffnm md2 -v -nt 5 -pme gpu -gpu_id 4 -pin off >& saida-md
2.log&


