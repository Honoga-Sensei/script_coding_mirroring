Il valore `$?` all'interno dello script si riverisce equivale a 0 o no a seconda se il comando 
precedentemetne eseguito ha emesso uno `standard output` `0`,uno `standard error` `1`, o numeri diversi 
per casi particolari, come `2` per utilizzo imporoprio di comandi o `130` che rappresenta un fatal error.

```
#!/bin/bash
 
echo hello
echo $?    # Exit status 0 returned because command executed successfully.
 
lskdf      # Unrecognized command.
echo $?    # Non-zero exit status returned -- command failed to execute.
 
echo
 
exit 113   # Will return 113 to shell.
           # To verify this, type "echo $?" after script terminates.
 
#  By convention, an 'exit 0' indicates success,
#+ while a non-zero exit value means an error or anomalous condition.
#  See the "Exit Codes With Special Meanings" appendix.
```
