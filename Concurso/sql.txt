SELECT 
    c.name,
    cast(cast (
      sum((s.math * 2) + (s.specifica * 3) + (s.project_plan * 5))/10
      as decimal(10,2)
    ) as varchar)as mediaPonderada
FROM candidate c
INNER JOIN score s
ON c.id=s.candidate_id 
GROUP BY c.name
ORDER BY mediaPonderada DESC