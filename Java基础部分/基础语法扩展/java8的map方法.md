# Java8的Map方法



## 1、put()

> put():V put(K key, V value);
>
> put覆盖并返回旧值，如果不存在则返回null

```java
public static void main(String[] args) {
        Map<String, String> map = new HashMap<>();
        map.put("a","A");
        map.put("b","B");
        String v = map.put("b","v");
        System.out.println(v);// 输出 B
        String v1 = map.put("c","v");
        System.out.println(v1); // 输出：NULL
    }
```



## 2、compute()

> compute()：V compute(K key, BiFunction < ? super K, ? super V, ? extends V> remappingFunction)
>
> 相当于put方法，不过返回的是新值。当key不存在时，执行value计算方法，计算value

```java
	@Test
    public void testMap() {
        Map<String, String> map = new HashMap<>();
        map.put("a", "A");
        map.put("b", "B");
        String val = map.compute("b", (k, v) -> "B2"); // 返回 B2
        System.out.println(val);
        String v1 = map.compute("c", (k, v) -> "C"); // 返回 C
        System.out.println(v1);
        System.out.println(map);
    }
```

测试结果：

```java
B2
C
{a=A, b=B2, c=C}
```



## 3、putIfAbsent()

> putIfAbsent():default V putIfAbsent(K key, V value)
>
> 如果存在则不设值，并且返回旧值。如果不存在则设值，并返回null

```java
	@Test
    public void testMap2() {
        Map<String, String> map = new HashMap<>();
        map.put("a", "A");
        map.put("b", "B");
        String v = map.putIfAbsent("b", "B2");  // 返回 B
        System.out.println(v);
        String v1 = map.putIfAbsent("c", "C");  // 返回 null
        System.out.println(v1);
        System.out.println(map);
    }
```

测试结果：

```java
B
null
{a=A, b=B, c=C}
```



## 4、computeIfAbsent()

> computeIfAbsent():default V computeIfAbsent(K key,Function<? super K, ? extends V> mappingFunction)
>
> 如果存在则不设值，并且返回旧值。如果不存在则返回新值

```java
	@Test
    public void testMap3() {
        Map<String, String> map = new HashMap<>();
        map.put("a", "A");
        map.put("b", "B");
        String v = map.computeIfAbsent("b", k -> "B2");  // 返回 B
        System.out.println(v);
        String v1 = map.computeIfAbsent("c", k -> "C"); // 返回 C
        System.out.println(v1);
        System.out.println(map);
    }
```

测试结果：

```java
B
C
{a=A, b=B, c=C}
```



## 5、computeIfPresent()

> computeIfPresent():V computeIfPresent(K key, BiFunction < ? super K, ? super V, ? extends V> remappingFunction)
>
> computeIfPresent的方法,对指定的在map中已经存在的key的value进行操作。只对已经存在key的进行操作，其他不操作

```java
	@Test
    public void testMap4() {
        Map<String, String> map = new HashMap<>();
        map.put("a", "A");
        map.put("b", "B");
        String s = map.computeIfPresent("b", (k, v) -> v = "B2");
        System.out.println(s);
        String s1 = map.computeIfPresent("c", (k, v) -> v = "C");
        System.out.println(s1);
        System.out.println(map);
    }
```

测试结果：

```java
B2
null
{a=A, b=B2}
```



**综上测试：**

```java
	@Test
    public void testMap5() {
        Map<String, String> map = new HashMap<>();
        map.put("a", "A");
        map.put("b", "B");
        map.put("c", null);//允许
        map.putIfAbsent("d", null);//允许
        map.compute("e", null);//空指针
        map.computeIfAbsent("f", null);//空指针
    }
```



扩充：

```java
		@Test
    public void testMap10() {
        Map<String, List<String>> map = new HashMap<>();
        List<String> list1 = new ArrayList<>();
        list1.add("1");
        list1.add("2");
        List<String> list2 = new ArrayList<>();
        list2.add("3");
        list2.add("4");
        map.put("A", list1);
        map.put("B", list2);
        map.computeIfPresent("A", (k, v) -> {
            v.add("88");
            return v;
        });
        map.computeIfPresent("C", (k, v) -> {
            v.add("99");
            return v;
        });
        System.out.println(map);
    }

		// 结果：{A=[1, 2, 88], B=[3, 4]}

    @Test
    public void map99() {
        Map<String, List<String>> map = new HashMap<>();
        List<String> list1 = new ArrayList<>();
        list1.add("1");
        list1.add("2");
        List<String> list2 = new ArrayList<>();
        list2.add("3");
        list2.add("4");
        map.put("A", list1);
        map.put("B", list2);
        map.compute("A", (k, v) -> {
            if (CollectionUtils.isEmpty(v)) {
                v = new ArrayList<>();
            }
            v.add("888");
            return v;
        });
        map.compute("C", (k, v) -> {
            if (CollectionUtils.isEmpty(v)) {
                v = new ArrayList<>();
            }
            v.add("999");
            return v;
        });
        System.out.println(map);
    }

		// 结果：{A=[1, 2, 888], B=[3, 4], C=[999]}
```





