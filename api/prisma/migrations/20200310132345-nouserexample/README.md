# Migration `20200310132345-nouserexample`

This migration has been generated by swyx at 3/10/2020, 1:23:45 PM.
You can check out the [state of the schema](./schema.prisma) after the migration.

## Database Steps

```sql
CREATE TABLE "quaint"."Post" (
    "body" TEXT NOT NULL DEFAULT '' ,
    "createdAt" DATE NOT NULL DEFAULT '1970-01-01 00:00:00' ,
    "id" INTEGER NOT NULL  PRIMARY KEY AUTOINCREMENT,
    "title" TEXT NOT NULL DEFAULT '' 
) 

DROP TABLE "quaint"."UserExample";
```

## Changes

```diff
diff --git schema.prisma schema.prisma
migration 20200310123523-create-posts..20200310132345-nouserexample
--- datamodel.dml
+++ datamodel.dml
@@ -1,18 +1,16 @@
 datasource DS {
   provider = "sqlite"
-  url = "***"
+  url = env("DB_HOST")
 }
 generator photonjs {
   provider = "prisma-client-js"
   binaryTargets = ["native", "rhel-openssl-1.0.x"]
 }
-// Define your own datamodels here and run `yarn redwood db save` to create
-// migrations for them.
-// TODO: Please remove the following example:
-model UserExample {
-  id    Int     @id @default(autoincrement())
-  email String  @unique
-  name  String?
-}
+model Post {
+  id        Int @id @default(autoincrement())
+  title     String
+  body      String
+  createdAt DateTime @default(now())
+}
```


