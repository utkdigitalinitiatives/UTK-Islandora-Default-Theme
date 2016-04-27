<!-- @file Project Page -->

# How to Use
```terminal
$ git clone -b 2016 https://github.com/utkdigitalinitiatives/UTK-Islandora-Default-Theme.git
$ npm install
$ npm run postinstall
$ grunt watch
```

# Copy Theme into Islandora
__OSX:__ (run once)
> $ mkdir ~/GitHub/islandora_vagrant/themes/

__OSX:__ (copies theme to Vagrant)
> $ rsync -azP ~/GitHub/UTK-Islandora-Default-Theme ~/GitHub/islandora_vagrant/themes/

__Vagrant:__ (copies theme from Vagrant to Drupal's theme directory)

___Automatically___ (initial)
```terminal
$ cd /var/www/drupal/sites/all/themes/

$ git clone -b 2016 --single-branch https://github.com/utkdigitalinitiatives/UTK-Islandora-Default-Theme.git
```


OR ___Manually___ copy from local folder (while developing)
```terminal
$ rsync -azP /vagrant/themes/ /var/www/drupal/sites/all/themes/
```


__Set new template as default__
```terminal
$ cd /var/www/drupal

$ drush theme pm-enable bootstrap

$ drush vset theme_default bootstrap

$ drush vset admin_theme bootstrap

$ drush theme pm-disable bartik

$ drush theme pm-disable seven

$ drush theme pm-disable garland
```

### Load some sample content.
```terminal
$ git clone https://github.com/mjordan/islandora_scg.git

$ drush --yes en islandora_scg

$ drush --yes cc drush

$ drush iscgl --user=admin --quantity=10 --content_model=islandora:sp_basic_image --parent=islandora:sp_basic_image_collection --namespace=testing --bgcolor=SlateGray

$ drush iscgl --user=admin --quantity=2 --content_model=islandora:newspaperCModel --parent=islandora:newspaper_collection --namespace=testing --quantity_newspaper_issues=2
```

### Features
- [jsDelivr CDN](http://www.jsdelivr.com) for "out-of-the-box" styling and
  faster page load times.
- [Bootswatch](http://bootswatch.com) theme support, if using the CDN.
- Glyphicons support via [Icon API](https://www.drupal.org/project/icon).
- Extensive integration and template/preprocessor overrides for most of the
  [Bootstrap Framework] CSS, Components and JavaScript
- Theme settings to further enhance the Drupal Bootstrap integration:
  - [Breadcrumbs](http://getbootstrap.com/components/#breadcrumbs)
  - [Navbar](http://getbootstrap.com/components/#navbar)
  - [Popovers](http://getbootstrap.com/javascript/#popovers)
  - [Tooltips](http://getbootstrap.com/javascript/#tooltips)
  - [Wells](http://getbootstrap.com/components/#wells) (per region)

### Documentation
Visit the project's [official documentation site](http://drupal-bootstrap.org)
or the markdown files inside the `./docs` folder.

[Bootstrap Framework]: http://getbootstrap.com
