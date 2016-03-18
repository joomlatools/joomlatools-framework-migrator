# Joomlatools Migrator

## What is Joomlatools Migrator?

Joomlatools Migrator is a re-usable component for exporting and importing extension data.

## Requirements

- Nooku Framework 2.1 or newer.
- PHP 5.3 or newer.
- MySQL 5.

## Installation

Joomlatools Migrator can and should be installed by using [Composer](https://getcomposer.org/).

Go to the root directory of your Joomla installation in command line and execute this command:

```
composer require joomlatools/joomlatools-migrator:*
```

The component will be installed in the `vendor` folder of the root directory of your Joomla site. The composer installer 
will make sure that the component is bootstrapped from that location and made available to other components extending it 
or just making use of it.

## How to use

Include the behavior in your extension's dispatcher:

```
class ComFooDispatcherHttp extends ComKoowaDispatcherHttp
{
    protected function _initialize(KObjectConfig $config)
    {
        $config->append(array(
            'behaviors'  => array(
                'com:migrator.dispatcher.behavior.migratable'
            )
        ));

		parent::_initialize($config);
    }
}
```

This will pick the migrators from the following identifiers by default:

```
com://admin/foo.migrator.export
com://admin/foo.migrator.import
```

Alternatively you can specify different identifiers in the behavior configuration.

Then navigate to `view=export` or `view=import` in your extension to perform migrations.

## Contributing

Joomlatools Migrator is an open source, community-driven project. Contributions are welcome from everyone. We have [contributing guidelines](CONTRIBUTING.md) to help you get started.

## Authors

See the list of [contributors](https://github.com/joomlatools/joomlatools-migrator/contributors).

## License

The `joomlatools-migrator` component is free and open-source software licensed under the [GPLv3 license](gplv3-license).

[gitlab-flow]: http://doc.gitlab.com/ee/workflow/gitlab_flow.html
[gplv3-license]: https://github.com/joomlatools/joomlatools-migrator/blob/master/LICENSE.txt
