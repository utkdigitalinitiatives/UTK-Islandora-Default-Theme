<!-- @file Project Page -->

# How to Use
__Required__: Node.js, Grunt, git(assuming this is already installed),
[Brew Installer]('http://brew.sh')(Optional)
```shell
$ brew install node
$ npm install -g grunt-cli
```

```shell
$ git clone -b 2016 https://github.com/utkdigitalinitiatives/UTK-Islandora-Default-Theme.git
$ npm install
$ npm run postinstall
$ grunt watch
```

# Copy Theme into Islandora
__Vagrant:__ (copies theme from Vagrant to Drupal's theme directory)

#### ___Clone to Vagrant directly___
```shell
$ cd /var/www/drupal/sites/all/themes/

$ git clone -b 2016 --single-branch https://github.com/utkdigitalinitiatives/UTK-Islandora-Default-Theme.git
```

__Set this template as default & disable original templates__
```shell
$ cd /var/www/drupal

$ drush cache-clear drush

$ drush -y pm-enable bootstrap

$ drush vset theme_default bootstrap

$ drush vset admin_theme bootstrap

$ drush -y pm-disable bartik

$ drush -y pm-disable seven

$ drush -y pm-disable garland
```

# Local Develope and Update
___Manual___ Local Development

___OSX:___ (copies theme to Vagrant)
```shell
$ mkdir ~/GitHub/islandora_vagrant/themes/

$ rsync -azP ~/GitHub/UTK-Islandora-Default-Theme ~/GitHub/islandora_vagrant/themes/
```

```diff
+ Note: run rsync after each update on local machine to copy to Vagrant
```

__Vagrant:__ (copies Vagrant themes folder to drupal themes)
```shell
$ rsync -azP /vagrant/themes/ /var/www/drupal/sites/all/themes/
```



### Load some sample content.
```shell
$ cd /var/www/drupal/sites/all/modules

$ git clone https://github.com/mjordan/islandora_scg.git

$ drush --yes en islandora_scg

$ drush --yes cc drush

$ drush iscgl --user=admin --quantity=10 --content_model=islandora:sp_basic_image --parent=islandora:sp_basic_image_collection --namespace=testing --bgcolor=SlateGray

$ drush iscgl --user=admin --quantity=15 --content_model=islandora:sp_large_image_cmodel --parent=islandora:sp_large_image_collection --namespace=testing --bgcolor=SlateGray

$ drush iscgl --user=admin --quantity=2 --content_model=islandora:newspaperCModel --parent=islandora:newspaper_collection --namespace=testing --quantity_newspaper_issues=2

$ drush iscgl --user=admin --quantity=2 --content_model=islandora:newspaperCModel --parent=islandora:newspaper_collection --namespace=islandora

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
