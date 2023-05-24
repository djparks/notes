# Migrate to Spring and Hibernate 6

## Text Blocks

```JAVA
@Query("""
  select p
  from Post p
  left join fetch p. comments
  where p. id between :minId and :maxId
""")
List<Post> findAllWithComments (
  @Param("minId") long minId,
  @Param("maxId") long maxId
);
```

## Records

Can't replace Entity with Record, but use as DTO.

```JAVA
public record PostCommentSummary(Long id, String title, String review) { }

@Query("""
select
  p.id as id, p.title as title, c.review as review
  from PostComment c
join c.post p
where p.title like :postTitle
order by c. id
""")

List<PostCommentSummary> findCommentSummaryByTitle(
  @Param("postTit1e") String postTitle
);
```

## Pattern Matching

Pattern matching (auto-casting) for instanceOf

```Java
subscribers.stream().forEach(sub -> {
  if(sub instanceof Fmai1Subscriber emailSub) {
     LOGGER.info("Send email to address [{}]", emailSub.getEmai1Address());
} else if(sub instanceof SmsSubscriber smsSub) {
     LOGGER.info("Send SMS to phone number [{}]", smsSub.getPhoneNumber());
} else {
     throw new IllegalStateException(
       String.format( "The [%s] type is not supported!", sub.getC1ass())
     );
}
});
```

## Jakarta Persistence 3.1 -- UUID

Not GOOD to use, too big and since random, screws up index cluster rebuild.

```JAVA
@Column (
    name = "external id",
    columnDefinition = "UUID NOT NULL"
)
private UUID externalId;
```

## Jakarta Persistence 3.1 -- Functions

### New numeric functions available in JPQL

* CEILING, FLOOR
* EXP, LN
* POWER
* ROUND
* SIGN

### New Date/Time functions available in JPQL

* LOCAL DATETIME, LOCAL DATE, LOCAL TIME
* EXTRACT(fie1d FROM expression)

``` JAVA
List<Post> posts = entityManager.createQuery("""
 select p
 from Post p
 where EXTRACT(YEAR FROM createdOn) = :year
 """, Post.class)
.setParameter( "year", Year.now().getValue())
getResultList();
```

## Hibernate 6 - JPQL - Window Functions

Brings standard SQL across different databases.

```JAVA
List<Long> runningTotals = entityManager.createQuery("""
SELECT
  SUM(at.amount) OVER(
     PARTITION BY at.account.id
     ORDER BY at. createdon
   ) AS balance
  FROM AccountTransaction at
 ORDER BY at.id
 """, Long.class)
.getResultList();
```

## Hibernate 6 - JPQL - Derived Tables

```JAVA
List<Tup1e> tuples = entityManager.createQuery("""
SELECT
  post_id AS post_id, post_title AS post_title,
  comment id AS comment id, comment review AS comment_review,
  DENSE RANK() OVER (ORDER BY p_pc.comment_count DESC) AS ranking
FROM (
  SELECT
    p.id AS post_id, p.title AS post_title,
    pc.id AS comment_id, pc.review AS comment_review,
    COUNT(p.id) OVER(PARTITION BY p.id) AS comment_count
  FROM PostComment pc
  JOIN pc.post p
  WHERE p.title LIKE :title
) p_pc
ORDER BY post_id, comment_id
""", Tuple.class)
.setParameter( "title", "SQL%" )
.getResultList();

```

## Hibernate 6 - JPQL - UNION [ALL]

```JAVA
List<String> topics = entityManager.createQuery("""
    select c.name as name
    from Category c
    union
    select t.name as name
    from Tag t
""", String.class)
.getResultList();
```

## Hibernate 6 - JPQL - INTERSECT [ALL], EXCEPT [ALL]

## Hibernate 6 — Criteria Queries

* Blaze Persistence is a much better option than criteria

```JAVA
List<Post> tuples = cbf.create(entityManager, Post.class)
  .from(Post.c1ass, "p")
  .like (Post_.TITLE).expression(":titlePattern").noEscape()
.orderBy(Post_ID, true)
.setParameter( "titlePattern", titlePattern)
.setMaxResults(maxCount)
.getResultList();
```

## Hibernate 6 - Auto entit dedu lication

```JAVA
List<Post> posts = entityManager.createQuery("""
  select p
  from Post p
  left join fetch p.comments
  where p.title = :title
  """, Post.c1ass)
.setParameter( "title", titlePattern)
.getResultList();
```

GENERATED SQL:

```JAVA
SELECT p.id AS idl_0_0_, pc.id AS idl1_1_1_,
       p.title AS title2_0_0_, pc.review AS review2_1_1_,
       pc.post_id AS post_id3_1_0, pc.id AS idl_1_0_
FROM post p
LEFT OUTER JOIN post_comment pc ON p.id=pc.post_id
WHERE p.title = ?
```

## Hibernate 6 - Type system - @TypeDef in @Entity

* The @TypeDef annotation is gone.
* User @Type; it is now type safe. Example: @Type(JsonType.class)
* @JdbcTypeCode(SqlTypes.JSON)

```JAVA
@JdbcTypeCode(SqlTypes.JSON)
@Column(columnDefinition = "jsonb")
private Map<String, String> properties;

```

## Spring Data 2 - PagingAndSortingRepository

* The PagingAndSortingRepository was extending the CrudRepository interface.

```JAVA
public interface PagingAndSortingRepository<T, ID>
   extends CrudRepository<T, ID> {

  Iterab1e<T> findAll(Sort sort);
  Page<T> findAll(Pageable pageable);
}
```
