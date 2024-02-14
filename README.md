<p align="center">
  <img src="https://github.com/KRochaS/NextLevelWeek14/blob/master/.github/nlw-logo.svg" width="370" >
  <br/>
  <br/>
  <img src="https://github.com/KRochaS/NextLevelWeek14/blob/master/.github/logo.svg" width="200" >
</p>

<br/>

<p align="center">	
   <img src="https://img.shields.io/badge/-Fastify-A9C195?style=flat&logoColor=white" />

  <img src="https://img.shields.io/badge/-Prisma-A9C195?style=flat&logoColor=white" />
  
  <img src="https://img.shields.io/badge/-Websocket-A9C195?style=flat&logoColor=white" />
</p>


## :bar_chart: About
A real-time polling system where users can create a poll, and others can actively participate by submitting their votes. The platform generates an instant ranking based on the choices, continuously updating the vote counts.

## :books: Technologies e libs                                                                
- [NodeJS](https://nodejs.org/en)
- [Typescript](https://www.typescriptlang.org/)
- [Fastify](https://fastify.dev/)
- [Prisma](https://www.prisma.io/)
- [Zod](https://zod.dev/)
- [Redis](https://redis.io/)
- [Docker](https://www.docker.com/)

## :computer: Routes

 <img src="https://github.com/KRochaS/NextLevelWeek14/blob/master/.github/screenshot-01.PNG" width="986" >
 
### POST `/polls`

 [![Run in Hoppscotch](https://hopp.sh/badge-dark.svg)](https://hopp.sh/r/dO2f3P01Z7R7)

Create a new poll.


#### Request body

```json
{
  "title": "What is the best programming language?",
  "options": [
    "JavaScript",
    "Java",
    "PHP",
    "C#"
  ]
}
```

#### Response body

```json
{
  "pollId": "194cef63-2ccf-46a3-aad1-aa94b2bc89b0"
}
```

### GET `/polls/:pollId`
[![Run in Hoppscotch](https://hopp.sh/badge-dark.svg)](https://hopp.sh/r/zBdwKePkhCCY)

Return data from a single poll.

#### Response body

```json
{
	"poll": {
		"id": "e4365599-0205-4429-9808-ea1f94062a5f",
		"title": "Qual a melhor linguagem de programação?",
		"options": [
			{
				"id": "4af3fca1-91dc-4c2d-b6aa-897ad5042c84",
				"title": "JavaScript",
				"score": 1
			},
			{
				"id": "780b8e25-a40e-4301-ab32-77ebf8c79da8",
				"title": "Java",
				"score": 0
			},
			{
				"id": "539fa272-152b-478f-9f53-8472cddb7491",
				"title": "PHP",
				"score": 0
			},
			{
				"id": "ca1d4af3-347a-4d77-b08b-528b181fe80e",
				"title": "C#",
				"score": 0
			}
		]
	}
}
```

### POST `/polls/:pollId/votes`

[![Run in Hoppscotch](https://hopp.sh/badge-dark.svg)](https://hopp.sh/r/xeNZLax9KNX5)

Add a vote to specific poll.

#### Request body

```json
{
  "pollOptionId": "31cca9dc-15da-44d4-ad7f-12b86610fe98"
}
```

## WebSockets ws `/polls/:pollId/results`

```json
{
  "pollOptionId": "31cca9dc-15da-44d4-ad7f-12b86610fe98"
}
```

#### Message

```json
{
  "pollOptionId": "da9601cc-0b58-4395-8865-113cbdc42089",
  "votes": 2
}
```
 Run in wscat:

 ```
$ npm i -g wscat

wscat -c ws://localhost:3333/polls/:pollId/results
```


## :green_book: Swagger Documentation

<img src="https://github.com/KRochaS/NextLevelWeek14/blob/master/.github/screenshot-02.png" width="986" >
<img src="https://github.com/KRochaS/NextLevelWeek14/blob/master/.github/screenshot-03.png" width="986" >


## :pencil: How to run the project

```bash

#  Clone this repository.
$ git clone https://github.com/KRochaS/NextLevelWeek14.git

# Navigate to the project folder in the terminal/cmd.
$ cd NextLevelWeek14/

# Install the dependencies.
$ npm i ou yarn install

# Setup PostgreSQL and Redis
$ docker compose up -d

# Copy .env.example to .env file

# run the project
$ npm run dev

# HTTP server running on http://localhost:3333
```
