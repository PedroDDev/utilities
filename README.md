# Docker

Docker is a set of platform-as-a-service products that use operating system-level virtualization to deliver software in packages called containers. Containers are isolated from each other and bundle their own software, libraries, and configuration files.

## Docker Commands

### docker-compose up

The `docker-compose up` command aggregates the output of each container. When the command exits, all containers are stopped.

    docker-compose up

Beside that, running `docker-compose up -d` starts the containers in the background and leaves them running. 

    docker-compose up -d

### docker-compose down

The `docker-compose down` command stops containers and removes containers, networks, volumes, and images created by `docker-compose up`.

By default, the only things removed are:

  + Containers for services defined in the Compose file
  + Networks defined in the networks section of the Compose file
  + The default network, if one is used

Networks and volumes defined as `external` are never removed. 

    docker-compose down

### docker system prune -f -a --volumes

The `docker system prune -f -a --volumes` command removes all docker containers, images and volumes. Start from scratch.

    docker system prune -f -a --volumes

# Git

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

## Git Commands

### git clone

If you want to get a copy of an existing Git repository — for example, a project you’d like to contribute to — the command you need is `git clone`.

    git clone <url of the repository in github>
       
### git branch -d

To delete a git branch locally, use `git branch -d`.

The `-d` option will delete the branch only if it has already been pushed and merged with the remote branch. Use `-D` instead if you want to force the branch to be deleted, even if it hasn't been pushed or merged yet.

    git branch -d <branch name>

### git config --global user.name

To configure your git username on your machine, use `git config --global user.name`.

The `--global` option will set crendentials to all repositories in your machine.

    git config --global user.name <your username>

### git config --global user.email

To configure your git user email on your machine, use `git config --global user.email`.

The `--global` option will set crendentials to all repositories in your machine.

    git config --global user.email <your@email.com>

## Conventional Commits Pattern

### What is it?

Conventional Commits is a simple commit message convention, which follows a set of rules and helps projects to have an explicit and well-structured commit history.

There are several benefits in using this type of convention, such as, for example, facilitating the entry of new Devs in the project, as well as being able to generate reports and be able to understand where the hours of the project are being concentrated (in code refactoring, feature creation, change styles, development environment, among others).

The truth is that by adopting this convention we discourage disorderly change, and so, with well-structured and organized code, we lose some time occasionally, but we gain enormous time in the long run.

### How to use?

The rules are very simple, as shown below we have a type of commit (type), the scope/context of the commit (scope) and the subject/message of the commit (subject), but I will detail each one later.

    !type(?scope): !subject
    <?body>
    <?footer>

Thus, ! indicates the mandatory attributes and ? indicates non-required attributes. We will not talk about the body or the footer of the commit. But these are simple specifications, which you can see more about [here](https://www.conventionalcommits.org/en/v1.0.0/#specification).



#### Subject: Imperative instead of past tense

I know it may seem strange at first to write the message in the imperative, as the implemented change was a past action, but by writing subjects using the imperative we are telling our team what the commit will do if applied. In Chris Beams [article](https://cbea.ms/git-commit/#imperative) he says a little more about choosing the imperative and brings a great notation, to which every subject must fit:

> *“If applied, this commit will [message]”*

#### Type: What are the commit types

The type is responsible for telling us what type of change or iteration is being made, from the convention rules, we have the following types:

+ `test`: indicates any type of creation or alteration of test codes. ***Example:** Creating unit tests.*
+ `feat`: indicates the development of a new feature to the project. ***Example:** Addition of a service, functionality, endpoint, etc.*
+ `refactor`: used when there is a code refactoring that does not have any impact on the system's business logic/rules. ***Example:** Code changes after a code review.*
+ `style`: employed when there are formatting and style changes to the code that do not change the system in any way. ***Example:** Change style-guide, change lint convention, fix indentations, remove whitespace, remove comments, etc.*
+ `fix`: used when correcting errors that are generating bugs in the system. ***Example:** Applying handling to a function that is not having the expected behavior and returning an error.*
+ `chore`: indicates design changes that do not affect system or test files. These are developmental changes. ***Example:** Change eslint rules, add prettier, add more file extensions to .gitignore.*
+ `docs`: used when there are changes to the project documentation. ***Example:** add info in API documentation, change README, etc.*
+ `build`: used to indicate changes that affect the project's build process or external dependencies. ***Example:** Gulp, add/remove npm dependencies, etc.*
+ `perf`: indicates a change that improved system performance. ***Example:** change ForEach to while, improve the database query, etc.*
+ `ci`: used for changes in CI configuration files. ***Example:** Circle, Travis, BrowserStack, etc.*
+ `revert`: indicates reverting a previous commit.

      git commit -m "test: add test for create product automation"
      git commit -m "feat: implement tracking product service"
      git commit -m "refactor: change return log pattern"
      git commit -m "style: change function param for objects"
      git commit -m "fix: remove getPayment() wrong attribute"
      git commit -m "chore: add no-undef rule in eslintrc.json"
      git commit -m "docs: add technologies list in readme"
      git commit -m "style: remove all blank spaces"
      git commit -m "perf: change looping for parallel execution"
      git commit -m "build: remove moment.js dependency"
      git commit -m "build: add date-fns npm dependency"
      git commit -m "revert: back to a215868 commit"

Thus, we can simply and directly see what kind of change is taking place, greatly improving visibility and alignment with the team.

**Note:**

+ Only one type can be used per commit;
+ The type is required;
+ If you're not sure which type to use, it's probably a big change and it's possible to split this commit into two or more commits;
+ The difference between build and chore can be quite subtle and can cause confusion, so we must be aware of the correct type. In the case of Node.js for example, we can think that when there is an addition/change of a certain development dependency present in devDependencies, we use the chore. For changes/additions of common dependencies to the project, and that have a direct and real impact on the system, we use the build.

#### Scope: contextualizing the commit

At this point — and following past conventions — we were able to understand the type of change that was made in the commit (commit type) and clearly understand what the commit will bring if applied (commit subject).

**However, how far can this change affect?**

In huge repositories, like [monorepos](https://en.wikipedia.org/wiki/Monorepo), or projects with many features and parallel changes, it is not very clear how far the incoming change can change. For this, we can use the scope of the commit.

    git commit -m "feat(UserService): add /getAppointments endpoint"

Even though the scope is not mandatory, it can be used to contextualize the commit and bring less responsibility to the subject, since having the type of commit and the context that was applied, the message should be as brief and concise as possible. Remembering that the scope must be inserted in the commit between parentheses.

In addition, in the case of scope, it is possible to add multiple values, for example: If there was a code refactoring in a repository with mobile, web and desktop versions. Which affects the mobile and web context, we could write the commit like this:

    git commit -m "refactor(web/mobile): change createUser() logs"

**Note:** Scopes must be separated with / , \ or ,.

***Reference:** https://medium.com/linkapi-solutions/conventional-commits-pattern-3778d1a1e657*





