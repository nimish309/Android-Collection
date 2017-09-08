# Android-Collection

add_action( 'rest_api_init', function () {
        register_rest_route( 'tomjn/v1', '/test/', array(
                'methods' => 'POST',
                'callback' => 'tomjn_rest_test'
        ) );
} );

function tomjn_rest_test() {
        $args = array(
	'posts_per_page'   => 3,
	'post_type'        => 'post',
);

    $query = new WP_Query( $args ); 
    if($query->have_posts()){
        while($query->have_posts()){
        $query->the_post();
            $locations[]['name'] = get_the_title();
           
        }
    }
    //Return the data
    return $locations;



}

add_action( 'rest_api_init', function () {
        register_rest_route( 'test/v1', '/tested/', array(
                'methods' => 'POST',
                'callback' => 'post_datas'
        ) );
} );

function post_datas($request){
	     // return $request->get_body();
       
        $json =  $request->get_body();
      //  print_r($param) ;
       $array = json_decode( $json, true );
       if( ! empty( $array ) ) {
	
	
	foreach( $array as $product ) {
		$a = $product['name'];
	}
	 return $a;
	
}


    //       $param = $request['some_param'];

    // // Or via the helper method:
    // $param = $request->get_param( 'some_param' );

    // // You can get the combined, merged set of parameters:
    // $parameters = $request->get_params();

    // // The individual sets of parameters are also available, if needed:
    // $parameters = $request->get_url_params();
    // $parameters = $request->get_query_params();
    // $parameters = $request->get_body_params();
    // $parameters = $request->get_default_params();

    // // Uploads aren't merged in, but can be accessed separately:
    // $parameters = $request->get_file_params();

      
      ==> https://apppresser.com/wp-api-post-submission/
       
