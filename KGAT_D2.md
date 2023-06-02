```d2
users_placeholder -> u_e -> model_phase_I
pos_items_placeholder -> pos_i_e -> batch_predictions -> bi_interaction_embed() -> model_phase_I
neg_items_placeholder -> neg_i_e -> batch_predictions -> bi_interaction_embed() -> model_phase_I

A_values_placeholder

A_in -> A_split_A_hat -> bi_interaction_embed()

r_placeholder -> r_e

h_placeholder -> h_e
pos_t_placeholder -> post_t_e
neg_t_placeholder -> neg_t_e

node_dropout_placeholder
mess_dropout_placeholder

ego_embedding + side_embedding -> add_embedding

build_weights -> w_user_embed -> ego_embedding 
build_weights -> w_item_embed
build_weights -> w_entity_embed -> ego_embedding 
build_weights -> w_relation_embed
build_weights -> w_Trans_W
build_weights -> w_W_gc -> sum_embedding
build_weights -> w_b_gc -> sum_embedding
build_weights -> w_W_bi
build_weights -> w_b_bi
build_weights -> w_W_mlp
build_weights -> w_b_mlp
```
