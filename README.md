# cs583-project1

Implement: Msapriori (excluding rule generation)

Consider: multiple minimum supports, support difference constraint, and item constraints
Item constraints: Two types

Cannotbe-together: sets of items cannot be in the same itemsets (pairwise), 

e.g., {1, 2, 3} and {6, 7, 9 10}
Must-have: every itemset must have, 
e.g., 1 or 2

Algorithm MSapriori(T, MS, fai)	// fai is for support difference constraint
	M <- sort(I, MS); 	
	L <- init-pass(M, T);  	
	F1 <- {{i} | i in L, i.count/n >= MIS(i)}; 	
	for (k = 2; Fk-1 is not empty; in T) do		
		if k=2 then  transaction c in Ck do
		   Ck <- level2-candidate-gen(L, fai) 
		else Ck <- MScandidate-gen(Fk-1, fai);
		end;
		for each transaction t in T do	
		    for each candidate c in Ck do  	
		         if c is contained in t then			
			 c.count++; 
		         if c - {c[1]} is contained in t then			
			c.tailCount++	
		    end	
		end	
	       Fk <- {c in Ck | c.count/n >= MIS(c[1])} 	
	end	
	return F <- UkFk;
