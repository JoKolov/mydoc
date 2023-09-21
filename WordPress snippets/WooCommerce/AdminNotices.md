# WooCommerce Admin Notices

## Fix WC Admin notice "Remove legacy coupon menu"

### Update DB from phpmyadmin
```
UPDATE {wp_}wc_admin_notes
SET status = 'actioned'
WHERE name = 'wc-admin-coupon-page-moved';
```
*Replace {wp_} by your current db prefix*

### Update DB from PHP snippet
```
add_action( 'init', function() {
    global $wpdb;

    $table_admin_notes = $wpdb->prefix . 'wc_admin_notes';
    $query = "UPDATE {$table_admin_notes} SET status = 'actioned' WHERE name = 'wc-admin-coupon-page-moved'";

    $wpdb->query($query);
} );
```
*Run it once and remove it using any code snippet plugin*
