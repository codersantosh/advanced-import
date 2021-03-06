Advanced Import is a very flexible plugin which convenient user to import site data( posts, page, media and even widget and customizer option ).

# Advanced Import : One Click Import for WordPress or Theme Demo Data

>`Advanced Import` Import Data or Demo Content which is exported by [Advanced Export](https://wordpress.org/plugins/advanced-export/)

## Installation

There are two ways to install any Advanced Import Plugin:-
1. Upload zip file from Dashboard->Plugin->Add New "upload plugin".
2. Extract Advanced Import and placed it to the "/wp-content/plugins/" directory.
    - Activate the plugin through the "Plugins" menu in WordPress.

## Frequently Asked Questions

#### Is Advanced Import is a free plugin? 

Yes, it is a free plugin.

#### Why my demo zip file is not importing?

Please make sure it is exported using the [Advanced Export](https://wordpress.org/plugins/advanced-export/) plugin

#### I have activated the plugin. Where is the "Demo Import"?

Login to your WordPress dashboard, go to Appearance -> Demo Import.
You can also find Import zip options on WordPress dashboard -> Tools -> Advanced Import.

#### Do I need to check to include media while Export?

If you are providing starter content- NO, but if you are migrating site - Yes. As long as the exported site is live on the internet it is not necessary but if you are migrating the site from local to live you should check it.
Technically, if you check to include media, the zip files content media files. Huge media files may cause other issues. Generally not recommended to check but you can check media as your requirements.

#### I am a theme author, how can I use this plugin for my theme?

First of all, you need to Export your theme demo data from your live demo site using [Advanced Export](https://wordpress.org/plugins/advanced-export/) plugin.
Export the zip file, it should contain 3 files content.json, options.json and widgets.json.
If you are submitting theme on WordPress dot org, you are not allowed to include Demo files ( XML, JSON, ZIP), You have to create a separate plugin for your theme/company. We would like to highly recommend to create a single plugin for your all themes. For other platforms, you may add code on your theme.
Code Example :
```
function prefix_demo_import_lists(){
   $demo_lists = array(
      'demo1' =>array(
         'title' => __( 'Title 1', 'text-domain' ),/*Title*/
         'is_pro' => false,/*Is Premium*/
         'type' => 'gutentor',/*Optional eg gutentor, elementor or other page builders or type*/
         'author' => __( 'Gutentor', 'text-domain' ),/*Author Name*/
         'keywords' => array( 'medical', 'multipurpose' ),/*Search keyword*/
         'categories' => array( 'medical','multipurpose' ),/*Categories*/
            'template_url' => array(
                'content' => 'full-url-path/content.json',/*Full URL Path to content.json*/
                'options' => 'full-url-path/master/options.json',/*Full URL Path to options.json*/
                'widgets' => 'full-url-path/widgets.json'/*Full URL Path to widgets.json*/
            ),
         'screenshot_url' => 'full-url-path/screenshot.png?ver=1.6',/*Full URL Path to demo screenshot image*/
         'demo_url' => 'https://www.demo.cosmoswp.com/',/*Full URL Path to Live Demo*/
         /* Recommended plugin for this demo */
         'plugins' => array(
            array(
               'name'      => __( 'Gutentor', 'text-domain' ),
               'slug'      => 'gutentor',
            ),
         )
      ),
        'demo2' =>array(
            'title' => __( 'Title 2', 'text-domain' ),/*Title*/
            'is_pro' => false,/*Is Premium*/
            'type' => 'gutentor',/*Optional eg gutentor, elementor or other page builders or type*/
            'author' => __( 'Gutentor', 'text-domain' ),/*Author Name*/
            'keywords' => array( 'about-block', 'about 3' ),/*Search keyword*/
            'categories' => array( 'contact','multipurpose','woocommerce' ),/*Categories*/
            'template_url' => array(
                'content' => 'full-url-path/content.json',/*Full URL Path to content.json*/
                'options' => 'full-url-path/master/options.json',/*Full URL Path to options.json*/
                'widgets' => 'full-url-path/widgets.json'/*Full URL Path to widgets.json*/
            ),
            'screenshot_url' => 'full-url-path/screenshot.png?ver=1.6',/*Full URL Path to demo screenshot image*/
            'demo_url' => 'https://www.demo.cosmoswp.com/',/*Full URL Path to Live Demo*/
            /* Recommended plugin for this demo */
            'plugins' => array(
                array(
                    'name'      => __( 'Gutentor', 'text-domain' ),
                    'slug'      => 'gutentor',
                ),
                array(
                    'name'      => __( 'Contact Form 7', 'text-domain' ),
                    'slug'      => 'contact-form-7',
                    'main_file' => 'wp-contact-form-7.php',/*the main plugin file of contact form 7 is different from plugin slug */
                ),
            )
        ),
        'demo3' =>array(
            'title' => __( 'Title 1', 'text-domain' ),/*Title*/
            'is_pro' => true,/*Is Premium : Support Premium Version*/
            'pro_url' => 'https://www.cosmoswp.com/pricing/',/*Premium version/Pricing Url*/
            'type' => 'gutentor',/*Optional eg gutentor, elementor or other page builders or type*/
            'author' => __( 'Gutentor', 'text-domain' ),/*Author Name*/
            'keywords' => array( 'woocommerce', 'shop' ),/*Search keyword*/
            'categories' => array( 'woocommerce','multipurpose' ),/*Categories*/
            'template_url' => array(/* Optional for premium theme, you can add your own logic by hook*/
                'content' => 'full-url-path/content.json',/*Full URL Path to content.json*/
                'options' => 'full-url-path/master/options.json',/*Full URL Path to options.json*/
                'widgets' => 'full-url-path/widgets.json'/*Full URL Path to widgets.json*/
            ),
            'screenshot_url' => 'full-url-path/screenshot.png?ver=1.6',/*Full URL Path to demo screenshot image*/
            'demo_url' => 'https://www.demo.cosmoswp.com/',/*Full URL Path to Live Demo*/
            /* Recommended plugin for this demo */
            'plugins' => array(
                array(
                    'name'      => __( 'Gutentor', 'text-domain' ),
                    'slug'      => 'gutentor',
                ),
            )
        ),
        /*and so on ............................*/
   );
   return $demo_lists;
}
add_filter('advanced_import_demo_lists','prefix_demo_import_lists');
```

#### Do I need to assign "Front page", "Posts page" and "Menu Locations" after the importer is done or do they automatically assign?

You don't need to assign them manually, they will be automatically assigned. Theme author also doesn't have to write additional code for it.

#### I am a theme author and I would like to customize it for my theme, Can you list hooks available on Advanced Import plugin?

Here are some important list of filter hooks:

- advanced_import_is_template_available
- advanced_import_template_import_button
- advanced_import_welcome_message
- advanced_import_demo_lists
- advanced_import_is_pro_active
- advanced_import_post_data
- advanced_import_replace_post_ids
- advanced_import_replace_term_ids
- advanced_import_new_options
- advanced_import_sidebars_widgets
- advanced_import_complete_message
- advanced_import_update_option_['option-name']
- advanced_import_update_value_['option-name']
- advanced_import_menu_hook_suffix

Here are some important list of action hooks:

- advanced_import_before_demo_import_screen
- advanced_import_after_demo_import_screen
- advanced_import_before_plugin_screen
- advanced_import_after_plugin_screen
- advanced_import_before_content_screen
- advanced_import_after_content_screen
- advanced_import_before_complete_screen
- advanced_import_after_complete_screen

#### I would like to develop a companion/starter sites/toolset plugin for my theme/company, Do you have any starter plugin?

We don't have any starter plugin but we have developed a plugin for [Acme Themes](https://www.acmethemes.com/). The plugin name is [Acme Demo Setup](https://wordpress.org/plugins/acme-demo-setup/), you can download and view the code of the plugin and develop one for yourself.

#### Are there any themes using these plugin?

Yes, many themes are using this plugin, for an example, you can look on [CosmosWP Theme](https://cosmoswp.com/)

