La prima cosa che notiamo all'interno dello script è la presenza di alcuni `echo` vuoti, quseti servono 
sper spaziare ciò che verrà printato a schermo dallo script.

Dopodichè troviamo vari metodi di assegnazione variabile: il primo è la classica assegnazione con 
uguaglianza `a=879`, questo metodo assegna dirattamente un valore preimpostato alla variabile;  

dopodiche abbimno `let a=16+5`, il `let` che precede la variabile permette di assegnare delle 
espressioni matematichead essa che se printata con un `echo` risultera nel risultato;      

infine vediamo il `read` che permette all'utente di assegnare il valore alla variabile tramite imput 
da tastiera durante l'esecuzione dello script.

```
#!/bin/bash
# Naked variables
 
echo
 
# When is a variable "naked", i.e., lacking the '$' in front?
# When it is being assigned, rather than referenced.
 
# Assignment
a=879
echo "The value of \"a\" is $a."
 
# Assignment using 'let'
let a=16+5
echo "The value of \"a\" is now $a."
 
echo
 
# In a 'for' loop (really, a type of disguised assignment):
echo -n "Values of \"a\" in the loop are: "
for a in 7 8 9 11
do
  echo -n "$a "
done
 
echo
echo
 
# In a 'read' statement (also a type of assignment):
echo -n "Enter \"a\" "
read a
echo "The value of \"a\" is now $a."
 
echo
 
exit 0
```
