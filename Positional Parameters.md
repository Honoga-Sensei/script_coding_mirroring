Lo cript inizia impostando una variabile che servirà poi come valore minimo di paramentri da dare allo 
script. Dopodichè utilizza `$0`, questa variabile di sistema assume il valore dello script in cui si trova 
riportando in questo caso nell'echo in nome dello script stesso.   

Dopodiche troviamo l'utilizzo di variabili simili com numeri superiori a 0, queste assumono il valore del 
paramtro corrispondente: `$1` equivale al primo paramentro inserito, `$2` al secondo e così via.

Insieme alle variabili sopracitate troviamo anche l'operatore `-n` che serve a verificare che la lunghezza di 
una stringa sia maggiore di 0, dunque non vuota. Mentre il `-lt` sta per "less then" cioè controlla che una variabile
sia inferiore di un'altra.

```
#!/bin/bash
 
# Call this script with at least 10 parameters, for example
# ./scriptname 1 2 3 4 5 6 7 8 9 10
MINPARAMS=10
 
echo
 
echo "The name of this script is \"$0\"."
# Adds ./ for current directory
echo "The name of this script is \"`basename $0`\"."
# Strips out path name info (see 'basename')
 
echo
 
if [ -n "$1" ]              # Tested variable is quoted.
then
 echo "Parameter #1 is $1"  # Need quotes to escape #
fi
 
if [ -n "$2" ]
then
 echo "Parameter #2 is $2"
fi
 
if [ -n "$3" ]
then
 echo "Parameter #3 is $3"
fi
 
# ...
 
 
if [ -n "${10}" ]  # Parameters > $9 must be enclosed in {brackets}.
then
 echo "Parameter #10 is ${10}"
fi
 
echo "-----------------------------------"
echo "All the command-line parameters are: "$*""
 
if [ $# -lt "$MINPARAMS" ]
then
  echo
  echo "This script needs at least $MINPARAMS command-line arguments!"
fi 
 
echo
 
exit 0
```
