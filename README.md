# Narwhal Wall of Learning

## Goal
The goal of Team Narwhal was to learn how to utilize the Google maps API in a `Go` application.

## Go Learning
Check out what we learned with the Go language and how we used it.  [Go Learning](./learning/GoReadme.md) for what we learned on Go.

## Over_React Learning
Check ou t what we learned with the Over_React framework and how we used it. [Over_React Learning](./learning/OverReactReadme.md) for what we learned with Over_React.

### References
[**Working Prototype**](https://github.com/Narwhal-Pillar/hamsterApi/blob/google-api/app/features/places/place_controller.go) Prototype utilizing the Google Maps API in Go.

### Folder Architecture
We have subscribed to the idea of `package by feature.` Essentially, files that change together, stay together. See example below:

```
guild-members/
    app/
        guildMembers/
            guild_member_controller.go
            guild_member_controller_test.go
            guild_member_service.go
        shared/
            members/
                members_model.go
                members_filter.go
                members_filter_test.go
        main.go
        main_test.go
    .gitignore
    README.md
```