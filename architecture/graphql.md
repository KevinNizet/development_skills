# GraphQL

## 🎓 J'ai compris et je peux expliquer

- la différence entre REST et GraphQL ✅
- les besoins auxquels répond GraphQL ✅
- la définition d'un schéma ✅
- Query ✅
- Mutation ✅
- Subscription ❌

## 💻 J'utilise

### Un exemple personnel commenté ✅

### Utilisation dans un projet ✅

[lien github](https://github.com/KevinNizet/the-good-corner)

Description :

Dans le cadre du projet de cours, j'ai mis en place une API GraphQL sur une base de donnée PostgreSQL.

GraphQL offre une flexibilité significative par rapport à REST, permettant une meilleure optimisation des requêtes, une évolution simplifiée du schéma et la prise en charge des besoins en temps réel avec les abonnements.
A la différence de REST, en GraphQL, le client spécifie les données exactes dont il a besoin, permettant une récupération plus efficace des données. En effet, le client ne récupére que la donnée dont il a besoin et non plus tout un ensemble de données via une query interrogeant la base. 
La mutation quant à elle est une requête pour effectuer des modifications sur le serveur (création, mise à jour, suppression).

Le schéma en GraphQL décrit le type de données, les relations établies entre eelles et les poits d'netrée de l'API. 


**Resolvers**
Ce sont les équivalents des Controller en REST. Ils sont chargés de résoudre les requêtes GraphQL en appelant les méthodes appropriées pour récupérer ou modifier les données.
Voici un extrait du code relatif au resolver des catégories, avec une partie des queries et mutations : 

```
import { Arg, ID, Mutation, Query, Resolver } from "type-graphql";
import {
  Category,
  CategoryCreateInput,
  CategoryUpdateInput,
} from "../../entities/Category";
import { validate } from "class-validator";

@Resolver(Category)
export class CategoriesResolver {
  @Query(() => [Category])
  async allCategories(): Promise<Category[]> {
    const categories = await Category.find({ relations: { ads: true } });
    return categories;
  }


  @Query(() => Category, { nullable: true })
  async category(@Arg("id", () => ID) id: number): Promise<Category | null> {
    const category = await Category.findOne({
      where: { id: id },
      relations: { ads: true },
    });
    return category;
  }

  @Mutation(() => Category)
  async createCategory(
    @Arg("data", () => CategoryCreateInput) data: CategoryCreateInput
  ): Promise<Category> {
    const newCategory = new Category();
    Object.assign(newCategory, data);

    const errors = await validate(newCategory);
    if (errors.length === 0) {
      await newCategory.save();
      return newCategory;
    } else {
      throw new Error(`Error occured: ${JSON.stringify(errors)}`);
    }
  }
}
```
La fonction allCategories est une requête GraphQL qui renvoie toutes les catégories avec leurs annonces associées.
La fonction category prend un identifiant en entrée et renvoie la catégorie correspondante avec ses annonces associées (ou null si aucune catégorie n'est trouvée).
La fonction createCategory prend en entrée les données nécessaires à la création d'une nouvelle catégorie. Elle valide (class-validator), crée une nouvelle instance de la catégorie, la sauvegarde en base de données, puis la renvoie.
Les annotations telles que @Query et @Mutation indiquent les types de requêtes/mutations que le resolver gère, et @Arg est utilisé pour spécifier les arguments des fonctions.

**Entities:**

Entités (ou Modèles) représentent la structure des données métier et sont utilisées par les resolvers pour interagir avec la base de données.
```
import {
  BaseEntity,
  Column,
  Entity,
  OneToMany,
  PrimaryGeneratedColumn,
} from "typeorm";
import { Length } from "class-validator";
import { Ad } from "./Ad";
import { Field, ID, ObjectType, InputType } from "type-graphql";

@Entity()
@ObjectType()
export class Category extends BaseEntity {
  @PrimaryGeneratedColumn()
  @Field(() => ID)
  id!: number;

  @Column({ length: 100 })
  @Length(10, 100)
  @Field()
  name!: string;

  @OneToMany(() => Ad, (ad) => ad.category)
  @Field(() => [Ad])
  ads!: Ad[];
}

@InputType()
export class CategoryCreateInput {
  @Field()
  name!: string;
}

@InputType()
export class CategoryUpdateInput {
  @Field({ nullable: true })
  name!: string;
}
```

L'entité "Category" représent une catégorie dans la base de données et a une relation "one to many" avec les annonces (Ads), définies par ailleurs dans le code également.
Des décorateurs sont utilisés pour la définir : @Entity, @ObjectType et @Field.

La structure des données est définie avec les "input types". Par exemple :
- CategoryCreateInput a un champ name requis.
- CategoryUpdateInput a un champ name facultatif.
Le décorateur @Length est utilisé pour définir la longueur du champs "name". 

Enfin, les annotations de TypeORM sont utilisées afin de simplifier l'interaction avec la base de données relationnelles. 
Il permet de :
- @Entity, @PrimaryGeneratedColumn, et @Column : définir les entités et leur structure
- @OneToMany : définir la relation entre Category et Ad. Il spécifie qu'une catégorie peut avoir plusieurs annonces.
- save, findOne, find : définir des opérations du CRUD
- @Length : définir des contraintes de validation


### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ✅

Description :

Dans le cadre de l'entreprise, le backend de nos applications mobiles utilise une API GraphQL.

## 🌐 J'utilise des ressources

### Titre

- Documentation officielle : https://graphql.org/learn/
- Description : documentation de référence utilisée pour définir le schéma de mon application ou le formatage des différentes requêtes.

