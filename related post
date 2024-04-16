<section class="blog_single_post pt_100 pb_100 related_articles">
    <div class="row_sm">
        <h2>Related <b>Articles</b></h2>
        <div class="row">
            <?php 
            // Get the ID of the current post
            $current_post_id = get_the_ID();

            // Get the categories of the current post
            $categories = get_the_category($current_post_id);
            $category_ids = array();
            foreach ($categories as $category) {
                $category_ids[] = $category->term_id;
            }

            $args = array(
                'post_type' => 'post',
                'posts_per_page' => 3,
                'post__not_in' => array($current_post_id), // Exclude the current post
                'category__in' => $category_ids, // Retrieve posts from the same categories
            );              

            $the_query = new WP_Query($args);
            if ($the_query->have_posts()) : 
                while ($the_query->have_posts()) : 
                    $the_query->the_post(); 
                    $post_id = get_the_ID();
                    $thumbnail_url = '';
                    
                    if (has_post_thumbnail()) {
                        $thumbnail_url = get_the_post_thumbnail_url(get_the_ID(), 'full');
                    }

                    $post_title = get_the_title(); 
                    $post_excerpt = get_the_excerpt();
                    $post_date = get_the_date(); 
                    ?>
                    <div class="col-12 col-md-6 col-lg-4">
                        <div class="inner_card">
                            <figure>
                                <a href="<?php the_permalink(); ?>"><img src="<?php echo $thumbnail_url; ?>" alt=""></a>
                            </figure>
                            <div class="desc">
                                <span class="post_date"><?php echo $post_date; ?></span>
                                <h5 class="post_title"><a href="<?php the_permalink(); ?>"><?php echo $post_title; ?></a></h5>
                                <p class="post_desc"><?php echo $post_excerpt; ?></p>
                            </div>
                        </div>
                    </div>
                <?php
                endwhile; 
                wp_reset_postdata(); 
            else: 
                // If no posts are found
                echo 'No posts found.';
            endif;
            ?>
        </div>
    </div>
</section>
