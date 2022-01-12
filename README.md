# xecs library

A entity component system:

```c++

// Entity Component System, create and destroy
ecs_t* ecs = g_create_ecs(alloc_t*);
g_destroy_ecs(ecs_t* ecs);

// Entity Type, 1024 is the maximum amount of entities in that type
en_type_t const* en_type_go = g_register_entity_type(ecs, 1024);

// Create / Delete entity
entity_t e = g_create_entity(ecs, en_type_go);
g_delete_entity(ecs, e);

// Components

struct position_t
{
    float x,y,z;
};

cp_type_t* poscp = g_register_component_type<position_t>(ecs);

g_set_cp(ecs, e, poscp);
if (g_has_cp(ecs, e, poscp))
{
    position_t* en_pos = g_get_cp<position_t>(ecs, e, poscp);

    g_rem_cp(ecs, e, poscp);
}


// Tags (1 bit per entity)

struct alerted_t{};

tg_type_t* alerted = g_register_tag_type<marked_t>(ecs);

g_set_tag(ecs, e, alerted);
if (g_has_tag(ecs, e, alerted))
{
    g_rem_tag(ecs, e, alerted);
}


// Iteration

// TODO, currently in progress


```

## Dependencies

- xbase (for alloc_t and hbb_t)
