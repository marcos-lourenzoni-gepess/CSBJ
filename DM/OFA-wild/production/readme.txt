
gmx grompp -f md1.mdp -c ../termalizacao/pr10.gro -p sistema.top -o md1.tpr -n index-1.ndx
gmx mdrun -nice 4 -s md1.tpr -deffnm md1 -v

gmx grompp -f md1.mdp -c md1.gro -p sistema.top -o md2.tpr -n index-1.ndx
gmx mdrun -nice 4 -s md2.tpr -deffnm md2 -v

gmx grompp -f md1.mdp -c md2.gro -p sistema.top -o md3.tpr -n index-1.ndx
gmx mdrun -nice 4 -s md3.tpr -deffnm md3 -v

gmx grompp -f md1.mdp -c md3.gro -p sistema.top -o md4.tpr -n index-1.ndx
gmx mdrun -nice 4 -s md4.tpr -deffnm md4 -v

gmx grompp -f md1.mdp -c md4.gro -p sistema.top -o md5.tpr -n index-1.ndx
gmx mdrun -nice 4 -s md5.tpr -deffnm md5 -v

gmx grompp -f md1.mdp -c md5.gro -p sistema.top -o md6.tpr -n index-1.ndx
gmx mdrun -nice 4 -s md6.tpr -deffnm md6 -v

**700 ns
gmx grompp -f md1.mdp -c md6.gro -p sistema.top -o md7.tpr -n index-1.ndx
gmx mdrun -nice 4 -s md7.tpr -deffnm md7 -v