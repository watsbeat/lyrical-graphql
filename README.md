# Lyrical-GraphQL

_This is an extension of a starter project from a GraphQL course on Udemy.com_

### Features:

- list songs
- add new song to list
- delete song from list
- add lyrics to song
- upvote individual lyrics
- navigate between song list screen and song detail screen (which displays lyric list)

## Setup Instructions

Database:

- Create a MongoDB Cloud account and follow instructions to get started
- Replace `MONGO_URI` value with your own URI

- Clone the repo
- `npm i` to install dependencies
- `npm run dev` to start to application
- Open in browser: `http://localhost:4000/#/`
- Experiment with the GraphiQL tool at `http://localhost:4000/graphql`

## GraphiQL Queries

```graphql
mutation AddSong($title: String) {
  addSong(title: $title) {
    id
  }
}

mutation AddLyricToSong($id: ID!, $content: String!) {
  addLyricToSong(songId: $id, content: $content) {
    id
    lyrics {
      id
      content
      likes
    }
  }
}

mutation DeleteSong($id: ID!) {
  deleteSong(id: $id) {
    id
  }
}

query FetchSongDetail($id: ID!) {
  song(id: $id) {
    id
    title
    lyrics {
      id
      content
      likes
    }
  }
}

query FetchSongs {
  songs {
    id
    title
  }
}

mutation LikeLyric($lyricId: ID!) {
  likeLyric(id: $lyricId) {
    id
    likes
  }
}
```
