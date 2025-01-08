1. Selezionare tutti gli studenti nati nel 1990 (160)
   SELECT \*
   FROM `university`.`students`
   WHERE YEAR(`date_of_birth`) = "1990";

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
   SELECT \*
   FROM `university`.`courses`
   WHERE `cfu` > "10";

3. Selezionare tutti gli studenti che hanno più di 30 anni
   SELECT \*, TIMESTAMPDIFF(YEAR, CURRENT_TIMESTAMP, `date_of_birth`)
   FROM `university`.`students`
   WHERE TIMESTAMPDIFF(YEAR, CURRENT_TIMESTAMP, `date_of_birth`) >= 30;

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
   laurea (286)
   SELECT \*
   FROM `university`.`courses`
   WHERE `period` = "I semestre" AND `year` = "1";

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
   20/06/2020 (21)
   SELECT \*
   FROM `university`.`exams`
   WHERE HOUR(`hour`) >= "14"
   AND `date` = "2020-06-20";

6. Selezionare tutti i corsi di laurea magistrale (38)
   SELECT \*
   FROM `university`.`degrees`
   WHERE `level` = "magistrale";

7. Da quanti dipartimenti è composta l'università? (12)
   SELECT COUNT(`id`)
   FROM `university`.`departments`;

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
   SELECT COUNT(`id`)
   FROM `university`.`teachers`
   WHERE `phone` IS NULL;

9. Inserire nella tabella degli studenti un nuovo record con i propri dati (per il campo
   degree_id, inserire un valore casuale)
   INSERT INTO `university`.`students`
   VALUES (DEFAULT, "61", "Simone", "Chiodo", "2005-09-28", "CHDSMN05P28L750R", "2024-09-11", "620504", "simochi.05@gmail.com");

10. Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126
    UPDATE `university`.`teachers`
    SET `office_number` = "126"
    WHERE `id` = "58";

11. Eliminare dalla tabella studenti il record creato precedentemente al punto 9
    DELETE FROM `university`.`students`
    WHERE `id` = "5003";
