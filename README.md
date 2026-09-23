# Video Sharing Platform

A backend database design for a video-sharing and social media platform.
The system supports users, videos, comments, playlists, subscriptions,
likes, and tweets.

## Overview

The platform is designed around a user-centric content model where users
can:

-   Upload and manage videos
-   Create playlists
-   Comment on videos
-   Like videos, comments, and tweets
-   Subscribe to channels
-   Publish tweets
-   Manage profile information and authentication data

## Database Structure

The database contains the following collections/tables:

### Users

Stores account and profile information.

  Field            Type     Description
  ---------------- -------- ------------------------------
  `id`             string   Primary key
  `username`       string   Unique username
  `email`          string   User email
  `fullName`       string   Full name
  `avatar`         string   Profile avatar
  `coverImage`     string   Profile cover image
  `password`       string   Hashed password
  `refreshToken`   string   Authentication refresh token
  `createdAt`      Date     Account creation date
  `updatedAt`      Date     Last update date

### Videos

Stores uploaded video content.

  Field           Type      Description
  --------------- --------- -------------------------
  `id`            string    Primary key
  `videoFile`     string    Video file reference
  `thumbnail`     string    Video thumbnail
  `title`         string    Video title
  `description`   string    Video description
  `duration`      number    Video duration
  `views`         number    View count
  `isPublished`   boolean   Publication status
  `createdAt`     Date      Creation date
  `updatedAt`     Date      Last update date
  `owner`         Users     User who owns the video

### Comments

Stores comments made on videos.

  Field         Type     Description
  ------------- -------- ------------------------------
  `id`          string   Primary key
  `video`       Videos   Referenced video
  `content`     string   Comment text
  `createdAt`   Date     Creation date
  `updatedAt`   Date     Last update date
  `owner`       Users    User who created the comment

### Playlists

Stores user-created video playlists.

  Field           Type         Description
  --------------- ------------ ---------------------------------
  `id`            string       Primary key
  `videos`        Videos\[\]   Videos included in the playlist
  `name`          string       Playlist name
  `description`   string       Playlist description
  `createdAt`     Date         Creation date
  `updatedAt`     Date         Last update date
  `owner`         Users        Playlist owner

### Subscriptions

Stores channel subscription relationships.

  Field          Type     Description
  -------------- -------- ----------------------------------
  `id`           string   Primary key
  `createdAt`    Date     Subscription creation date
  `updatedAt`    Date     Last update date
  `subscriber`   Users    User subscribing to a channel
  `channel`      Users    User/channel being subscribed to

### Likes

Stores likes associated with different types of content.

  Field         Type       Description
  ------------- ---------- ----------------------------
  `id`          string     Primary key
  `video`       Videos     Liked video
  `comment`     Comments   Liked comment
  `likedBy`     Users      User who liked the content
  `createdAt`   Date       Creation date
  `updatedAt`   Date       Last update date
  `tweet`       Tweets     Liked tweet

### Tweets

Stores short-form text posts.

  Field         Type     Description
  ------------- -------- ------------------
  `id`          string   Primary key
  `owner`       Users    Tweet author
  `content`     string   Tweet content
  `createdAt`   Date     Creation date
  `updatedAt`   Date     Last update date

## Relationships

-   A **User** can own multiple videos.
-   A **User** can create multiple comments.
-   A **Video** can have multiple comments.
-   A **User** can own multiple playlists.
-   A **Playlist** can contain multiple videos.
-   A **User** can subscribe to multiple channels.
-   A **User** can have multiple subscribers.
-   A **User** can like videos, comments, and tweets.
-   A **User** can create multiple tweets.
-   A **Video** belongs to one owner.
-   A **Comment** belongs to one video and one owner.
-   A **Tweet** belongs to one owner.

## Entity Relationship Diagram

The database relationships can be visualized using an ER diagram created
with Eraser.

The main entities are:

``` text
Users
 ├── Videos
 ├── Comments
 ├── Playlists
 ├── Subscriptions
 ├── Likes
 └── Tweets
```

## Project Status

Database/schema design phase.

## License

This project is for educational and development purposes.
