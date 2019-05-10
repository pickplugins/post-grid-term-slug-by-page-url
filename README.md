# post-grid-term-slug-by-page-url

```
function post_grid_filter_query_args_extra($query_args){

    if(is_page()):

        $current_post_id = get_the_ID();
        $post = get_post($current_post_id);
        $slug = $post->post_name;

        $taxonomy = 'post_tag';
        $operator  = 'IN';


        $query_args['tax_query'][] = array(
            'taxonomy' => $taxonomy,
            'field'    => 'slug',
            'terms'    => $slug,
            'operator'    => $operator,
        );


    endif;

    //echo '<pre>'.var_export($query_args, true).'</pre>';

    return array_merge($query_args);


}

add_filter('post_grid_filter_query_args','post_grid_filter_query_args_extra');

```
