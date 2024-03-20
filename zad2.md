


```lubi(j,p).
lubi(p,k).
lubi(p,j).
lubi(jan, anna).
lubi(anna, jan).
lubi(piotr, sara).
lubi(sara, piotr).

lubi(darek,marek).
lubi(marek,darek).
lubi(darek,marcin).
lubi(marcin,darek).
lubi(jan,darek).

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
plec(marek, male).
plec(darek, male).


przyjazn(X,Y) :-
    lubi(X,Y),
    lubi(Y,X).

loves(X,Y) :-
    \+ (przyjazn(X,Z), Z \= Y),
    \+ (przyjazn(Y,Z), Z \= X),
    \+(X = Y),
    przyjazn(X,Y).


true_love(X,Y) :-
    loves(X,Y),
    plec(X, male),
    plec(Y, female); 
    plec(X, female),
    plec(Y, male).

```

# zad 1
### A:
Rodzenstwo
### B:
Kuzyni
### C:
Dziakowie
### D:
Rodzic przyrodni/macocha/ojczym
### E
Rodzenstwo przyrodnie
### F
Szwagier/bratowa
### G
Brat z watpliwego malzenstwa

## zad 1_2

# zad 2


    











