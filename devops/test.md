# Tester son application

> ❌ A travailler

> ✔️ Auto validation par l'étudiant

## 🎓 J'ai compris et je peux expliquer

- les tests unitaires ✅
- les mocks ✅
- les tests d'integration ✅
- les tests de bout en bout (end to end) ✅
- le TDD ✅
- les tests par snapshot ❌ / ✔️

## 💻 J'utilise

### Un exemple personnel commenté ✅

Exemple de test front écrit avec Jest : le but de ce test Jest est de vérifier le comportement de la création et de la recherche d'une quête via GraphQL
Vérification de la création d'une nouvelle quête puis que cette quête peut être trouvée via son id

```
describe("create a new quest", () => {
  let createdQuestId: number;

  it("should create a new quest", async () => {
    const data: QuestCreateInput = {
      title: "Test Quest",
      description: "Description d'une quête test",
      startDate: new Date(),
      duration: 10,
      difficulty: Difficulty.EASY,
      missions: [],
    };

    const response = await graphql({
      schema,
      source: `
          mutation CreateQuest($data: QuestCreateInput!) {
            createQuest(data: $data) {
              id
              title
              startDate
              duration
              difficulty
            }
          }
        `,
      variableValues: { data },
    });

    const createQuest: any = response.data?.createQuest;
    createdQuestId = createQuest.id;

    expect(createQuest).toBeDefined();
    expect(createQuest).toHaveProperty("id");
    expect(createQuest).toHaveProperty("title", data.title);
    expect(createQuest).toHaveProperty(
      "startDate",
      data.startDate.toISOString()
    );
    expect(createQuest).toHaveProperty("duration", data.duration);
    expect(createQuest).toHaveProperty("difficulty", data.difficulty);
  });

  it("should find the created quest by its ID", async () => {
    const response = await graphql({
      schema,
      source: `
        query getQuestById($Id: ID!) {
          getQuestById(id: $Id) {
              id
              title
            }
          }
        `,
      variableValues: { Id: createdQuestId },
    });

    const foundQuest = response.data?.getQuestById;

    expect(foundQuest).toBeDefined();
    expect(foundQuest).toHaveProperty("id", createdQuestId);
  });
});
```

Exemple d'uen partie detest back écrit avec Jest : le but ici est de mocker une authentification utilisateur
Vérification de la création d'une nouvelle quête puis que cette quête peut être trouvée via son id

```
// mocks des données envoyées et reçues
const mocks = [
  // Successful login & correct credentials
  {
    request: {
      query: mutationSignin,
      variables: {
        email: "valid@example.com",
        password: "validpassword",
      },
    },
    result: {
      data: {
        signin: { id: "1", __typename: "User" },
      },
    },
  },
  // Unsuccessful login & incorrect credentials
  {
    request: {
      query: mutationSignin,
      variables: {
        email: "wrong@example.com",
        password: "wrongpassword",
      },
    },
    result: {
      error: new Error("Les identifiants sont incorrects"),
    },
  },
];
```

### Utilisation dans un projet ✅

[lien github](https://github.com/WildCodeSchool/2023-09-wns-rouge-greenquest)

Description :

### Utilisation en production si applicable❌ / ✔️

[lien du projet](...)

Description :

### Utilisation en environement professionnel ✅

Description :
Dans le cadre de l'entreprise, je suis amené à écrire des tests unitaires et d'intération sur mobile avec Patrol et Gherkin Cucumber

## 🌐 J'utilise des ressources

### Titre

- Documentation officielle de Jest : https://jestjs.io/fr/


## 📽️ J'en fais la démonstration


- J'ai fait une [présentation](https://www.canva.com/design/DAFydT0qFNY/r_VeacUySMFI_-AQUzKumQ/edit?utm_content=DAFydT0qFNY&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton) ✅
En effet, je parle de la problématique de l'écriture des tests en Flutter, dans le cadre de l'intégration continue.
