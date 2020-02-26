# MySQL Countries

1. Paises que hablan Sloveno, ordenados de manera descendente de acuerdo al porcentaje de la población que habla el idioma.
```
SELECT country.Name, countrylanguage.Language, countrylanguage.Percentage
FROM country
JOIN countrylanguage ON country.code = countrylanguage.CountryCode
WHERE countrylanguage.language = 'Slovene' 
ORDER BY Percentage DESC;
```
2. Cantidad total de ciudades por país, ordenadas de manera descendente.
```
SELECT country.name as Country_Name, COUNT(city.countrycode) as Total_Cities 
FROM city
JOIN country ON city.countrycode = country.code
GROUP BY country.name
ORDER BY Total_Cities DESC
```
3. Cantidad de ciudades de México que poseen más de 500.000 habitantes.
```
SELECT country.name as Country_Name, COUNT(city.countrycode) AS Total_Cities
FROM city
JOIN country ON city.countrycode = country.code
WHERE city.population > 500000 AND country.code = 'MEX'
GROUP BY country.name
```
4. Idiomas de cada país con un porcentaje de habla por habitante mayor a un 89% ordenados de manera descendente.
```
SELECT country.name as Country_Name, countrylanguage.Language, countrylanguage.Percentage
FROM countrylanguage
JOIN country ON countrylanguage.countrycode = country.code
WHERE countrylanguage.percentage > 89
ORDER BY countrylanguage.percentage DESC 
```
5. Todos los paises que poseen un área inferior a 501 y población superior a 100.000 habitantes.
```
SELECT name FROM country
WHERE SurfaceArea < 501 AND Population > 100000
```
6. Todos los países que poseen Monarquía Consitutcional con un capital superior a 200 y una esperanza de vida superior a 75 años?
```
SELECT name, governmentform FROM country
WHERE capital > 200 AND LifeExpectancy >75 AND governmentform = 'Constitutional Monarchy'
ORDER BY name ASC
```
7. Todas las ciudades de Argentina dentro del distrito de Buenos Aires y tener una población superior a 500.000, ordenadas de manera descendente.
```
SELECT city.Name AS City_Name, country.name AS Country_Name, city.District, city.Population
FROM city
JOIN country ON city.countrycode = country.code
WHERE city.countrycode = 'ARG' AND city.district = 'Buenos Aires' AND city.population > 500000
ORDER BY city.population DESC
```
8. Número de países por región, ordenados de manera descendente.
```
SELECT Region, count(code) AS Countries_In_Region from country
GROUP BY region
ORDER BY count(code) DESC
```