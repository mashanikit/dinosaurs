SELECT COUNT(id) from dinos;

SELECT name from dinos
WHERE period = 'Jurassic';

SELECT SUM(length)
from dinos
WHERE period = 'Cretaceous';

SELECT name, species from dinos
WHERE period = 'Jurassic' OR period = 'Cretaceous'
ORDER BY species;

Saurischians are the "lizard hipped" order of dinosaurs, and one of the two main branches. All carnivorous dinosaurs are Saurischians, but not all Saurischians are carnivorous. Find all the dinosaurs from the t_order Saurischia that are Herbivorous.

SELECT name, t_order, diet from dinos
WHERE t_order = 'Saurischia' AND diet = 'Carnivorous';

Dinosaur names are hard to remember. Find the shortest dinosaur, and rename it Shortie.

SELECT name, length from dinos
WHERE length in(SELECT MIN(length) from dinos);

UPDATE dinos
SET name = 'Shortie'
WHERE length in(SELECT MIN(length) FROM dinos);

It's the first day of Dino School, and we're doing roll call. Find the alphabetically first dinosaur, so we can make sure they're present for class.

SELECT name from dinos
ORDER BY name
LIMIT 1;

Rename the five longest dinosaurs The Famous Five.

UPDATE dinos
Set name = 'The Famous Five'
WHERE length in(SELECT length FROM dinos WHERE length > 0 ORDER BY length DESC LIMIT 5);
