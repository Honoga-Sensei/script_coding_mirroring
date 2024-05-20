Il seguente script serve a riconoscere se l'attuale utente è `root`. Con il costrutto `if [ "$UID" -eq "$ROOT_UID" ]` 
il dispositivo mette in confronto `ROOT_UID` impostato prima a 0 per indentificare il numero id di root, con  
`$UID` che rappresente l'attuale id nell'utente, cercando un uguaglianza grazie all'operatore `-eq`.
In caso quest'uguaglianza avvenga il terminale ritornerà lopzione `then` senno avremmo un esecuzione di `else`.

Nel secondo caso invece di confrontare il numero id, viene messo a confronto il nome con l'operatore `=`.

```
#!/bin/bash
# am-i-root.sh:   Am I root or not?
 
ROOT_UID=0   # Root has $UID 0.
 
if [ "$UID" -eq "$ROOT_UID" ]  # Will the real "root" please stand up?
then
  echo "You are root."
else
  echo "You are just an ordinary user (but mom loves you just the same)."
fi
 
exit 0
 
# ============================================================= #
# Code below will not execute, because the script already exited.
 
# An alternate method of getting to the root of matters:
 
ROOTUSER_NAME=root
 
username=`id -nu`              # Or...   username=`whoami`
if [ "$username" = "$ROOTUSER_NAME" ]
then
  echo "Rooty, toot, toot. You are root."
else
  echo "You are just a regular fella."
fi
```
