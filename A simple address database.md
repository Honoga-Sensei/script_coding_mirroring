Questo script crea un array tramite il `declare -A address` che dichiara un array associativo chiamto address
in cui ogni elemento dell'array ha a sua volta un valora assegnato.

Si può riportare individualmente il valore di un elemento dell'arrey tramite `echo ${array[elemento_array]}` 
oppure richiamere gli elementi ma non i valori a loro assegnati, tramite `echo ${!array[@]}` che utilizza il 
`!` proprio a tale scopo e la `@` per indicare tutti gli elementi.

```
#!/bin/bash4
# fetch_address.sh
 
declare -A address
#       -A option declares associative array.
 
address[Charles]="414 W. 10th Ave., Baltimore, MD 21236"
address[John]="202 E. 3rd St., New York, NY 10009"
address[Wilma]="1854 Vermont Ave, Los Angeles, CA 90023"
 
 
echo "Charles's address is ${address[Charles]}."
# Charles's address is 414 W. 10th Ave., Baltimore, MD 21236.
echo "Wilma's address is ${address[Wilma]}."
# Wilma's address is 1854 Vermont Ave, Los Angeles, CA 90023.
echo "John's address is ${address[John]}."
# John's address is 202 E. 3rd St., New York, NY 10009.
 
echo
 
echo "${!address[*]}"   # The array indices ...
# Charles John Wilma
```
