# Platform usage scenarios

Civicoin is the platform, so you can use it however you want. **There are examples:**

## 1. Building an economy in your community

> Basic MVP scenario

You may want to create an economy in your community (Discord server or something else), where members are able to exchange some value with determined game rules. It's useful when you want to distribute things, worth or just for fun

### How to set it up?

1. The community administrator creates a `system` on the platform, creating the admin account (it could be called *system account*). He sets the core, limits of coin issuance, coin name and other parameters
2. The administrator generates invite links with which members join the `system`
3. He issues coins — the economy has started!

## 2. Club with membership payments

> More complex scenario with contracts

There are closed clubs with membership, which can be paid with some virtual coins. Members can earn them by performing useful actions: inviting friends, activities, etc.

### How to set it up?

1. The club administrator creates a `system` on the platform. He disables the possibility for members to interchange coins, sets unlimited issuance and adds an API connector (to automate coins accrual)
2. Administrator creates `contracts` with content like „withdraw 10 coins every first day of the month; if successful — extend membership; if failed — close membership and send message“, which members sign
3. Members may not create accounts handedly if it's wanted to hide platform details — registration can be automated, as well as contacts signing. Or you can ask them to sign up and use the platform's beautiful app!
