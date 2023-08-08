## Contexts
### Spawn
How many particles are spawned and in which tempo. You can set it to 1 and no decay to have one object forever.

### Initialize
Start method, gets called once after the particle is spawned.
Capacity is about memory pool.

### Update
Update method, updates every frame.

This will add to the previous value.

### Ouput
How particles are going to be displayed. 

Only happens when it's drawn so it doesn't add to the previous value. 