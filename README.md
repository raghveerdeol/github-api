# github-api

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

- **Milestones**
    
    **Milestone 1**
    Fare la ricerca solo per repository.
    La ricerca deve partire al click di un pulsante “Cerca”.
    Mostrare in pagina i nomi dei repository, anche con una grafica minima.
    
    **Milestone 2**
    Permettere di scegliere il tipo di ricerca: repository oppure utenti/organizzazioni.
    Dare un layout grafico curato alle card.
    L’aspetto della card dovrà variare in base al risultato mostrato: repository o user/organization.
    
    **Milestone 3**
    Integriamo una validazione minimale: la ricerca deve partire solo se l’utente ha digitato almeno 3 caratteri.
    Mostriamo un messaggio in caso non venga restituito nessun risultato (es. non esiste una repo con il nome che è stato cercato).
    Aggiungiamo un loader che sarà mostrato mentre siamo in attesa di ottenere i risultati.
    
    **Bonus 1**
    Implementiamo un **debounce**: appena l’utente smette di digitare nell’input, dopo 700ms parte la chiamata di ricerca all’API.
    
    ****Bonus 2**
    La chiamata API base restituisce solo 30 risultati. Integriamo una funzionalità base di paginazione: due pulsanti (avanti / indietro) che ci permettano di navigare tra le pagine.
