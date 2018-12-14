Back to [world database](mangosdb_struct) list of tables.

The \`pool\_pool\` table
------------------------

This is the pool of pools table. You can create a pool with a chance of a range of pools in that pool being activated.

### Structure

| **Field**                             | **Type**     | **Attributes** | **Key** | **Null** | **Default** | **Extra** | **Comment** |
|---------------------------------------|--------------|----------------|---------|----------|-------------|-----------|-------------|
| [pool\_id](Pool_pool#pool_id)         | mediumint(8) | unsigned       | PRI     | NO       | 0           |           |             |
| [mother\_pool](Pool_pool#mother_pool) | mediumint(8) | unsigned       |         | NO       | 0           |           |             |
| [chance](Pool_pool#chance)            | float        | signed         |         | NO       | 0           |           |             |
| [description](Pool_pool#description)  | varchar(255) | signed         |         | YES      | NULL        |           |             |

### Description of the fields

#### pool\_id

The [ID](pool_template#entry) of the [pool\_template](pool_template) that you want to include in this "pool of pools" as a child pool.

#### mother\_pool

The [ID](pool_template#entry) of the [pool\_template](pool_template) that defines this "pool of pools".

#### chance

The explicit percentage chance that this child pool will be spawned.

If the mother pool spawns just one child pool ([max\_limit](pool_template#max_limit) = 1 in the respective mother pool's [pool\_template](pool_template)), the core selects the child pool to be spawned in a two-step process: First, only the explicitly-chanced (chance &gt; 0) child pools of the mother pool are rolled. If this roll does not produce any child pool, all the child pools without explicit chance (chance = 0) are rolled with equal chance. If the mother pool spawns more than one child pool, the chance is ignored and all the child pools in the mother pool are rolled in one step with equal chance.

In case the mother pool spawns just one child pool and all the child pools have a nonzero chance, the sum of the chances for all the child pools must equal to 100, otherwise the mother pool won't function correctly.

#### description

A text field to describe what this pool of pools is for.