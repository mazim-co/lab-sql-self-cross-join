-- 3.01 Lab | SQL Self and cross join
-- Get all pairs of actors that worked together.
SELECT fa1.actor_id, fa1.film_id
FROM sakila.film_actor fa1
JOIN sakila.film_actor fa2
ON fa1.actor_id <> fa2.actor_id AND fa1.film_id = fa2.film_id
WHERE fa1.film_id=1 WHERE fa1.actor_id != fa2.actor_id AND fa2.actor_id > fa1.actor_id;



-- Get all pairs of customers that have rented the same film more than 3 times.
SELECT i.film_id, r1.customer_id, count(*)
FROM sakila.rental r1
JOIN sakila.rental r2
ON r1.rental_id = r2.rental_id
JOIN sakila.inventory i 
ON r1.inventory_id = i.inventory_id
GROUP BY i.film_id, r1.customer_id
HAVING COUNT(*) = 3
ORDER BY customer_id, film_id;


-- Get all possible pairs of actors and films.
SELECT concat(a.first_name,' ',a.last_name) AS ActorName, f.title 
FROM sakila.actor a 
CROSS JOIN sakila.film f;
