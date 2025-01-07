1. Contare quanti iscritti ci sono stati ogni anno:
   SELECT YEAR(`enrolment_date`), COUNT(`id`)
   FROM `university`.`students`
   GROUP BY YEAR(`enrolment_date`);

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio:
   SELECT `office_address`, COUNT(`id`)
   FROM `university`.`teachers`
   GROUP BY `office_address`;

3. Calcolare la media dei voti di ogni appello d'esame:
   SELECT `exam_id`, AVG(vote)
   FROM `university`.`exam_student`
   GROUP BY `exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento:
   SELECT `department_id`, COUNT(`id`)
   FROM `university`.`degrees`
   GROUP BY `department_id`;
