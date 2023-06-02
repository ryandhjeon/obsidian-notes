```d2
users_placeholder -> u_e -> model_phase_I
pos_items_placeholder -> pos_i_e -> batch_predictions -> bi_interaction_embed -> model_phase_I
neg_items_placeholder -> neg_i_e -> batch_predictions -> bi_interaction_embed -> model_phase_I

A_values_placeholder

A_in -> A_fold_hat

r_placeholder -> r_e

h_placeholder -> h_e
pos_t_placeholder -> post_t_e
neg_t_placeholder -> neg_t_e

node_dropout_placeholder
mess_dropout_placeholder

build_weights -> w_user_embed
build_weights -> w_item_embed
build_weights -> w_entity_embed
build_weights -> w_relation_embed
build_weights -> w_Trans_W
build_weights -> w_W_gc
build_weights -> w_b_gc
build_weights -> w_W_bi
build_weights -> w_b_bi
build_weights -> w_W_mlp
build_weights -> w_b_mlp
```
