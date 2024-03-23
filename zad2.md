


```
lubi(j,p).
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

```
kobieta(X) :- osoba(X),\+mezczyzna(X).
ojciec(X,Y) :- mezczyzna(X) , rodzic(X,Y).
matka(X,Y):-kobieta(X),rodzic(X,Y).
corka(X,Y) :- kobieta(X),rodzic(Y,X).
brat_rodzony(X,Y) :- mezczyzna(X),rodzic(Z,X),rodzic(Z,Y),X \= Y.
brat_przyrodni(X,Y) :- rodzic(Z,X),rodzic(W,Y),mezczyzna(X), X != Y , W != Z.
kuzyn(X,Y):- rodzic(Z,X),rodzic(W,Y) ,brat_rodzony(Z,W),mezczyzna(X).
dziadek_od_strony_ojca(X,Y):- rodzic(X,Z),rodzic(Z,Y),mezczyzna(Z),mezczyzna(X).
dziadek_od_strony_matki(X,Y):- rodzic(X,Z),rodzic(Z,Y),kobieta(Z),mezczyzna(X).
dziadek(X,Y) :- rodzic(X,Z),rodzic(Z,Y),mezczyzna(X).
babcia(X,Y) :- :- rodzic(X,Z),rodzic(Z,Y),kobieta(X).
wnuczka(X,Y) :- babcia(Y,X),kobieta(X).
przodek_do2pokolenia_wstecz(X, Y) :- rodzic(X, Z), rodzic(Z, Y).
przodek_do3pokolenia_wstecz(X, Y) :- rodzic(X, Z), przodek_do2pokolenia_wstecz(Z, Y).  


```

### zad 2_Dla_Chetnych

```
a) Przedstawienie stwierdzeń w języku logiki predykatów:

czlowiek(markus).
pompejanczyk(markus).
rzymianin(X) :- pompejanczyk(X).
wladca(cezar).
lojalny(X, cezar) :- rzymianin(X), \+ nienawidzi(X, cezar).
nienawidzi(X, cezar) :- rzymianin(X), \+ lojalny(X, cezar).
lojalny(X, Y) :- czlowiek(X), czlowiek(Y).
probuje_zamachu(X, Y) :- czlowiek(X), wladca(Y), \+ lojalny(X, Y).
probuje_zamachu(markus, cezar).

b) Czy Markus był lojalny wobec Cezara?

?- lojalny(markus, cezar).

c) Formuły w postaci koniunkcyjnej normalnej (CNF):

czlowiek(markus).
pompejanczyk(markus).
rzymianin(X) :- pompejanczyk(X).
wladca(cezar).
lojalny(X, cezar) :- rzymianin(X), \+ nienawidzi(X, cezar).
nienawidzi(X, cezar) :- rzymianin(X), \+ lojalny(X, cezar).
lojalny(X, Y) :- czlowiek(X), czlowiek(Y).
probuje_zamachu(X, Y) :- czlowiek(X), wladca(Y), \+ lojalny(X, Y).
probuje_zamachu(markus, cezar).

d) Dowód metodą rezolucji:

?- \+ (lojalny(markus, cezar), probuje_zamachu(markus, cezar)).
```



```
a) Wyrażenie zdań w języku logiki predykatów:

1. lubi(jan, X) :- pozywienie(X).
2. pozywienie(jablka).
3. pozywienie(kurczak).
4. pozywienie(X) :- je(Y, X), zyje(Y).
5. je(adam, orzeszki), zyje(adam).
6. je(basia, X) :- je(adam, X).

b) Przekształcenie formuł do postaci koniunkcyjnej normalnej (CNF):

1. lubi(jan, X) :- pozywienie(X).
2. pozywienie(jablka).
3. pozywienie(kurczak).
4. pozywienie(X) :- je(Y, X), zyje(Y).
5. je(adam, orzeszki).
6. zyje(adam).
7. je(basia, X) :- je(adam, X).

c) Udowodnienie, że Jan lubi orzeszki:

?- lubi(jan, orzeszki).

d) Odpowiedź na pytanie, jakie pożywienie je Basia:

?- je(basia, X).
```

```
urodzony(markus, 40).
max_wiek(150).
zyje(X, Y2) :- urodzony(X, Y1), max_wiek(MaxWiek), Y2 - Y1 =< MaxWiek.


?- zyje(markus, 2021).
```






