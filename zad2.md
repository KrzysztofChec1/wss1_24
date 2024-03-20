
lubi(j,p).
lubi(p,k).
lubi(p,j).
lubi(j,b).
lubi(b,j).
lubi(jan, anna).
lubi(anna, jan).
lubi(piotr, sara).
lubi(sara, piotr).


niep(X,Y):-
    lubi(X,Y);
    lubi(Y,X).

    
nie_lubi(a,b).
nie_lubi(b,a).
nie_lubi(a,c).
nie_lubi(c,k).

hate(X,Y) :-
    nie_lubi(X,Y),
	nie_lubi(Y,X).


niby_przyjazn(X,Y) :-
    lubi(X,Y),\+
    lubi(Y,X);
    
    \+lubi(X,Y),
    lubi(Y,X).


plec(jan, male).
plec(anna, female).
plec(peter, male).
plec(sara, female).


przyjazn(X,Y) :-
    lubi(X,Y),
    lubi(Y,X).

loves(X,Y) :-
    \+(przyjazn(X,W \= Y)),
    \+(przyjazn(Y,W \= X)),
    \+(X = Y),
    przyjazn(X,Y).


true_love(X,Y) :-
    loves(X,Y),
    plec(X, male),
    plec(Y, female); 
    plec(X, female),
    plec(Y, male).




    











