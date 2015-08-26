## 1 Find all rows that have an ingredient name of Brussels sprouts.
```
EXPLAIN ANALYSE
SELECT *
	FROM ingredients INDEX (ingredients_name_idx)
	WHERE name LIKE '%Brussels sprouts%'
	;
--with index ![alt](https://40.media.tumblr.com/effe6b597491a65c07b2255259121dfa/tumblr_ntpchokqT91uzhpxoo1_1280.png)


EXPLAIN ANALYSE
SELECT *
	FROM ingredients
	WHERE name LIKE '%Brussels sprouts%'
	;
--without index ![alt](https://40.media.tumblr.com/02574c2ca8b7885acabd003d144c3328/tumblr_ntpchokqT91uzhpxoo2_1280.png)
```

## 2 Calculate the total count of rows of ingredients with a name of Brussels sprouts.
```
EXPLAIN ANALYSE
SELECT count(*)
	FROM ingredients INDEX (ingredients_name_idx)
	WHERE name LIKE '%Brussels sprouts%'
	;
--with index
![alt](https://36.media.tumblr.com/9961338dce987e2fb8d0994c7360c3da/tumblr_ntpcphfrJ71uzhpxoo1_1280.png)

EXPLAIN ANALYSE
SELECT count(*)
	FROM ingredients
	WHERE name LIKE '%Brussels sprouts%'
	;
	--without index
	![alt](https://41.media.tumblr.com/afe09c16b3cf08b121f5687fb557e8e5/tumblr_ntpcphfrJ71uzhpxoo2_r1_1280.png)
```
## 3 Find all Brussels sprouts ingredients having a unit type of gallon(s).
```
EXPLAIN ANALYSE
SELECT *
	FROM ingredients INDEX (ingredients_name_idx)
	WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%'
	;
	--with index
	![alt](https://41.media.tumblr.com/d249b751cc2658c52846c29b22e7fdb1/tumblr_ntpcvy2QXe1uzhpxoo1_1280.png)

EXPLAIN ANALYSE
SELECT *
	FROM ingredients
	WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%'
	;
	--without index
	![alt](https://36.media.tumblr.com/2e8cb1bda06488da48d03a6986331019/tumblr_ntpcvy2QXe1uzhpxoo2_r1_1280.png)
```

## 4 Find all rows that have a unit type of gallon(s), a name of Brussels sprouts or has the letter j in it.
```
EXPLAIN ANALYSE
SELECT *
	FROM ingredients INDEX (ingredients_name_idx)
	WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%' OR name LIKE '%j%'
	;
	--with index
	![alt](https://36.media.tumblr.com/23498fe499211dd09ed1b03fc22af375/tumblr_ntpczoM1631uzhpxoo1_1280.png)

EXPLAIN ANALYSE
SELECT *
	FROM ingredients
	WHERE unit LIKE '%gallon(s)%' AND name LIKE '%Brussels sprouts%' OR name LIKE '%j%'
	;
	--without index
	![alt](https://40.media.tumblr.com/3b4e5404c44a0a57bcdefd2809d8ab15/tumblr_ntpczoM1631uzhpxoo2_r1_1280.png)
```
