---
title: Apply and Configure a Storefront Theme | Commerce Frontend Development
description: Learn how to apply and configure storefront themes in Adobe Commerce and Magento Open Source.
---

# Apply and configure a storefront theme

The topic describes how to apply a [theme](https://glossary.magento.com/theme) for your store. This is a required step if you want a theme to be used on a [storefront](https://glossary.magento.com/storefront).
Also, it gives information how to add a theme independent logo for your store.

## Prerequisites

Make sure that you [set](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/set-mode.html) your application to the developer [mode](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/setup/application-modes.html).

## Apply a theme

After you [add your theme to the file system](create-storefront.md), you can apply it to your store. You apply a theme in [Admin](https://glossary.magento.com/admin).

To apply a theme:

1. In Admin, go to **Content** > Design > **Configuration**. A Design Configuration page opens. It contains a grid with the available configuration scopes. For example:

   ![Design Configuration page](../../_images/frontend/design_conf1.png)

1. In the configuration record corresponding to your store view, click **Edit**. The page with design configuration for the selected scope opens. For example:

   ![Design Configuration page for a particular scope](../../_images/frontend/applied_theme.png)

1. On the **Default Theme** tab, in the **Applied Theme** drop-down, select your newly created theme.
1. Click **Save Configuration**.
1. If caching is enabled, [clear the cache](#clear-the-cache).
1. To see your changes applied, reload the storefront pages.

## Add a design exception

Design exceptions enable you to specify an alternative theme for particular user-agents, instead of creating a separate store views for them.
To add a design exception:

1. In Admin, go to **Content** > Design > **Configuration**
1. In the configuration record corresponding to your store view, click **Edit**.
1. On the **Design Rule** tab, click **Add New User Agent Rule**.
1. In the **Search String** box specify the user-agent using either normal strings or regular expressions (PCRE). In the **Theme Name** drop-down list select the theme to be used for matching agent.

![Design Exception](../../_images/frontend/user_agent_rule.png)

1. Click **Save Configuration** or **Save and Continue**.
1. If caching is enabled, [clear the cache](#clear-the-cache).
1. To see your changes applied, reload the storefront pages.

## Add a theme-independent logo

You might want to set a permanent store logo that displays on the storefront no matter what theme is applied.
To add a permanent theme-independent logo:

1. In Admin, go to **Content** > Design > **Configuration**
1. In the configuration record corresponding to your store view, click **Edit**.
1. Expand the **Header** tab.
1. In the **Logo Image** field browse to the logo file saved in your file system.
1. Upload the file. Allowed file types include .png, .gif, .jpg, and .jpeg. To add an .svg logo, see [Declaring theme logo](create-storefront.md#declaring-theme-logo).
1. Optionally, specify the desired width, height, and the alternative text for the logo in the corresponding fields.
1. Click **Save Configuration** or **Save and Continue**.
1. If caching is enabled, [clear the cache](#clear-the-cache).
1. To see your changes applied, reload the storefront pages.

![Set store logo in Admin](../../_images/frontend/logo.png)

The logo you add here is stored in the `/pub/media/logo/default/` directory.

<InlineAlert variant="warning" slots="text"/>

To delete the permanent logo, go to the same location, and click the "Delete image" icon in the bottom left corner of the logo preview, then click the "Save Configuration button".

## Clear the cache

If caching is enabled in Admin, you must clear the cache after you apply the theme, add a design exception, add a logo, and perform other tasks.

A system message notifies you that invalidated cache types must be refreshed.

1. Click **System** > **Cache Management**.
1. Clear the invalid cache types.

![Clear the cache from Admin](../../_images/frontend/clear_cache.png)

## Troubleshooting

If the changes you configure in the Admin are not applied after you clear the cache and reload the page, delete all files in the `pub/static/frontend` and `var/view_preprocessed` directories, then reload the pages. You can delete the files manually or run the `grunt clean:<theme_name>` command in CLI. See [Installing and configuring Grunt](../tools/grunt.md).
