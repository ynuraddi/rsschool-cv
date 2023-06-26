# Yeresagyn Nuraddinov
### Junior Frontend Developer
---
### Contact information:
* email: definston@gmail.com
* tel: 8 (747) 821-83-23
* tg: @pelmenstruation
* [LinkedIn](https://www.linkedin.com/in/ynuraddi/)

---

### About me:
My name is Ersagny, I am 23 years old, a resident of Astana, Kazakhstan.
In the beginning I wanted to become an architect, but apparently it was not my destiny. Studied in Europe, but returned for family reasons, then went to a local university, where the quality of teaching I was very disappointed, decided to go away and work myself.
Last year I was studying actively 50-80 hours a week in [Alem School](http://alem.school) of Programming, received the training inside company [One Technologies](https://one.kz/), but I still haven`t found job =(
I am ready to work around the clock and give all my free time to the company, I am still young and inexperienced - hungry, I am well aware of my situation, I need to work very hard and I am ready for it.

![I'm ready to work!!!](https://sun9-77.userapi.com/impg/Y1kwSHSPb-4TTQDLNdN_MOJR2QkrJxqkQbzycw/j0R2Zr7pEjM.jpg?size=750x750&quality=95&sign=e2fc3e2fe139c1a2552ab0df713aafc5&type=album "I'm ready to work")

---

### My skills:
* **Golang**
* **Docker:**
    + Docker-compose
* **HTTP, RPC:**
    + REST, gRPC
* **SQL, noSQL:**
    + MongoDB, PostgreSQL, MySQL
* **Frameworks:**
    + Echo
    + Gin
    + GORM
* **Testing:**
    + Unit
    + Mock


---

### I recently solved a problem in leetcode

**97. Interleaving String**
*Given strings s1, s2, and s3, find whether s3 is formed by an interleaving of s1 and s2.*
*An interleaving of two strings s and t is a configuration where s and t are divided into n and m substrings respectively, such that:*

**Example 1:**
![example](https://assets.leetcode.com/uploads/2020/09/02/interleave.jpg)

**My solve**
```
func isInterleave(s1 string, s2 string, s3 string) bool {
	if len(s1)+len(s2) != len(s3) {
		return false
	}

	cache := make(map[[2]int]bool)

	var dfs func(i, j int) bool
	dfs = func(i, j int) bool {
		if i >= len(s1) && j >= len(s2) {
			return true
		}

		if val, ok := cache[[2]int{i, j}]; ok {
			return val
		}

		if i < len(s1) && s1[i] == s3[i+j] && dfs(i+1, j) {
			return true
		}
		if j < len(s2) && s2[j] == s3[i+j] && dfs(i, j+1) {
			return true
		}

		cache[[2]int{i, j}] = false
		return false
	}
	return dfs(0, 0)
}
```