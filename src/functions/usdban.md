---
description: Bans an user from the guild using their ID.
---

# $ban



### Usage

```php
$abbreviate[number;decimal?]
```

### Fields

| Field | Description | Type | Required |
| :--- | :--- | :--- | :--- |
| number | The number is going to abbreviated | number | yes |
| decimal | Separates the number in a decimal way | number | no |

###### Abbreviation Types

* `k` — thousands
* `m` — millions
* `b` — billions
* `t` — trillions

## Examples

Without decimal:

```javascript
bot.command({
  name: "abbreviate",
  code: `
  $abbreviate[6900]
  `
//Returns: 7K
});
```

With decimal:

```javascript
bot.command({
  name: "abbreviate",
  code: `
  $abbreviate[6983;1]
  `
//Returns: 6.9K
});
```

---
description: 

# $ban

Bans an user from the guild using their ID.
---

#### Fields

This function has 4 properties, 1 required and 2 optional.

1. User ID.
2. Guild ID (optional).
3. MessagesToDelete\(In days, optional\)
4. Reason \(Optional\)

Raw Usage: `$ban[userID;guildID (optional);MessagesToDelete (Optional);reason (Optional)]`

#### Options

* UserID - The user the bot is banning
* GuildID - The server ID where you are banning
* MessagesToDelete - How many of the messages over x days to delete of the banned user
* Reason - The reason in the audit logs

#### Usage

```javascript
bot.command({
    name: "ban",
    code: `
    $username[$message] has been banned from the guild.
    $ban[$message;$guildID;7;$noMentionMessage]
    $argsCheck[1;Just enter the User ID of who you want to ban.]
    `
});
```

{% hint style="danger" %}
We recommend adding an `$onlyPerms[ban;Error when no permissions.]` at the bottom of the command!

This way only people who have permission to ban will be able to ban other members.
{% endhint %}

Example of the code with `$onlyPerms[]` to avoid bans without permissions:

```javascript
bot.command({
    name: "ban",
    code: `
    $username[$message] has been banned from the guild.
    $ban[$message;$guildID;7;$noMentionMessage]
    $argsCheck[1;Just enter the User ID of who you want to ban.]
    $onlyPerms[ban;Only cool people with ban perms can use this!]
    `
});
```



