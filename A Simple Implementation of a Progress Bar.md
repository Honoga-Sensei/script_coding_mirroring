Questo script avvia 2 processi diversi, il mprimo definito all'interno delle `{}` che avvia un loop 
`while` per printare `.` ogni secondo come dichiarato dal comando `sleep` con 2 secondi prima di avviarsi,
per poi venir mandato in bac kground grazie a `&`.
Il secondo è il processo che usa come `sleep` la variabile `long_interval`, che quindi si interrompe per 10 
secondi prima di fare l'`echo` di finished, fare un `kill` richiamando `USR1` che indando il trap dell'altro
processo lo chiude per poi chiudere definitivamente lo script

In oltre tutto il processo può essere interrotto con `^C` che stamperà un `!`, per poi interrompere anche il 
processo in background grazie al `kill -USR1 $pid` che chiude il processo e `wait $pid` che attende la normale 
interruzione di esso.

```
#! /bin/bash
# progress-bar2.sh
# Author: Graham Ewart (with reformatting by ABS Guide author).
# Used in ABS Guide with permission (thanks!).
 
# Invoke this script with bash. It doesn't work with sh.
 
interval=1
long_interval=10
 
{
     trap "exit" SIGUSR1
     sleep $interval; sleep $interval
     while true
     do
       echo -n '.'     # Use dots.
       sleep $interval
     done; } &         # Start a progress bar as a background process.
 
pid=$!
trap "echo !; kill -USR1 $pid; wait $pid"  EXIT        # To handle ^C.
 
echo -n 'Long-running process '
sleep $long_interval
echo ' Finished!'
 
kill -USR1 $pid
wait $pid              # Stop the progress bar.
trap EXIT
 
exit $?
```
