# Esercizio Modellazione Database Università

## Descrizione

L'obiettivo di questo esercizio è progettare la struttura di un database per gestire i dati di un'università, considerando le seguenti entità e relazioni:

- **Dipartimenti**: rappresentano le grandi aree disciplinari (es. Lettere e Filosofia, Matematica, Ingegneria).
- **Corsi di Laurea**: ogni Dipartimento offre diversi corsi di laurea (es. Informatica, Civiltà e Letterature Classiche).
- **Corsi**: ogni corso di laurea prevede vari corsi specifici (es. Sistemi Operativi 1, Analisi Matematica 2).
- **Insegnanti**: possono tenere più corsi.
- **Appelli d’Esame**: ogni corso ha più appelli.
- **Studenti**: iscritti ad un solo corso di laurea ma possono partecipare a più appelli d’esame.
- **Risultati Esame**: per ogni appello a cui uno studente partecipa, si memorizza il voto, anche se insufficiente.
