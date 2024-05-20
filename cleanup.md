# Cleanup

Il seguente codice permette di ripulire i file `messages` e `wtmp` sostituendo il loro contenuto con 
quello del file `/dev/null` grazie all'operatore `>`. Questo è possibile perchè il file `/dev/null` 
rappresenta un dispositivo virtuale che non memorizza i datti che che gli vengono scritti e di conseguenza 
risultya sempre vuoto.

```
# Cleanup
# Run as root, of course.
 
cd /var/log
cat /dev/null > messages
cat /dev/null > wtmp
echo "Log files cleaned up."
```
