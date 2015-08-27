## 1 Find all rows that have an ingredient name of Brussels sprouts.

**combined with index**
		EXPLAIN ANALYSE
		SELECT *
			FROM ingredients INDEX (ingredients_name_idx)
			WHERE name = '%Brussels sprouts%';

**2 steps with index**
		CREATE INDEX ON ingredients(name);
			EXPLAIN ANALYSE
			SELECT *
				FROM ingredients
				WHERE name = 'Brussels sprouts';
 ![alt](https://40.media.tumblr.com/effe6b597491a65c07b2255259121dfa/tumblr_ntpchokqT91uzhpxoo1_1280.png)
 *images are out of date*


**without index**
		EXPLAIN ANALYSE
		SELECT *
			FROM ingredients
			WHERE name LIKE '%Brussels sprouts%';
 ![alt](https://40.media.tumblr.com/02574c2ca8b7885acabd003d144c3328/tumblr_ntpchokqT91uzhpxoo2_1280.png)


## 2 Calculate the total count of rows of ingredients with a name of Brussels sprouts.

**combined with index**
		EXPLAIN ANALYSE
		SELECT count(\*)
			FROM ingredients INDEX (ingredients_name_idx)
			WHERE name LIKE '%Brussels sprouts%';

**2 steps with index**
		CREATE INDEX ON ingredients(name);
			EXPLAIN ANALYSE
			SELECT count(\*)
				FROM ingredients
				WHERE name = 'Brussels sprouts';

**without index**
		EXPLAIN ANALYSE
		SELECT count(\*)
			FROM ingredients
			WHERE name LIKE '%Brussels sprouts%';

## 3 Find all Brussels sprouts ingredients having a unit type of gallon(s).

**combined with index**
		EXPLAIN ANALYSE
		SELECT *
			FROM ingredients INDEX (ingredients_name_idx)
			WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%';

**2 steps with index**
		CREATE INDEX ON ingredients(name);
			EXPLAIN ANALYSE
				SELECT *
					FROM ingredients
					WHERE name = 'Brussels sprouts' AND unit = 'gallon(s)';

**without index**
		EXPLAIN ANALYSE
		SELECT *
			FROM ingredients
			WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%';

## 4 Find all rows that have a unit type of gallon(s), a name of Brussels sprouts or has the letter j in it.

**combined with index**
		EXPLAIN ANALYSE
		SELECT *
			FROM ingredients INDEX (ingredients_name_idx)
			WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%' OR name LIKE '%j%';

**2 steps with index**
		CREATE INDEX ON ingredients(name);
			EXPLAIN ANALYSE
				SELECT *
					FROM ingredients
					WHERE name LIKE 'Brussels sprouts' AND ingredients.unit = 'gallon(s)' OR name LIKE '%j%';

**without index**
		EXPLAIN ANALYSE
		SELECT *
			FROM ingredients
			WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%' OR name LIKE '%j%';
