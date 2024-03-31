# QUAD: "Quick and Dirty (Scripting)"

Quad is a slightly unhinged idea I had for a scripting language. The idea
is to make the most boring, predicatable scripting language possible, with
the addition of a plugin system to the compiler for adding custom syntax
for pattern matching on and serializing to common data formats. I'm currently
picturing something like

```quad
config_path = "./config.json"
users = get_rows(read_users_path(config_path))
of_age_users = filter(users, |user| user.age >= 21 end)
write_users("./of_age.json", of_age_users)

read_users_path |config_path|
    ```json
        "config_info": {
            "users_path": (path)
        }
    ``` <- read(config_path) 
    path
end

get_rows |users_path|
    ```csv
        name, _, age, _ as users
    ``` <- read(users_path)
    users
end

write_users |of_age_path, of_age_users|
    total_of_age_users = count(of_age_users)
    ```json
        {
            "total_of_age_users": (total_of_age_users),
            "of_age_users": (of_age_users)
        }
    ``` -> output
    write(of_age_path, output)
end
```

Making this repo in case I decide to prototype something.
