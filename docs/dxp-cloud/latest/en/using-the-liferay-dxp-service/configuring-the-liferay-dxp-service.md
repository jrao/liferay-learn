# Configuring the Liferay DXP Service

There are several methods available to configure Liferay DXP: through the in [DXP System Settings](https://help.liferay.com/hc/en-us/articles/360029131591-System-Settings) and through the use of [config](https://help.liferay.com/hc/en-us/articles/360029131591-System-Settings) and [property files](https://help.liferay.com/hc/en-us/articles/360028712292-Portal-Properties).  DXP property and configuration files for your Liferay DXP instance in DXP Cloud are deployed by being placed inside of one of the `config` folders in the Liferay DXP service directory in your repository.

```
	lcp
	└── liferay
		├── LCP.json
		└── config
			├── common
			├── dev
			├── local
			├── prd
			└── uat
```

With the exception of the `common/` directory, changes added to a given service's environment folder (e.g., `dev`, `uat`, `prod`) will _only_ be propagated when deploying to the corresponding environment. Changes added to the `common/` directory will _always_ be deployed, regardless of the target deployment environment. This applies to the `config`, `deploy`, `license`, and `script` directories within `lcp/liferay/`.

## Portal Properties

[Portal properties](https://help.liferay.com/hc/en-us/articles/360028712292-Portal-Properties) are files of the form `portal-*.properties` that are used to configure your Liferay DXP environment.

In an on-site Liferay DXP instance, these files belong inside of `$LIFERAY_HOME`. When using Liferay DXP Cloud, place these files into the appropriate `config` folder(s) for them to be copied into `$LIFERAY_HOME` for the Liferay DXP instance on deployment.

These are the types of portal properties files you may use in one of the `config` folders:

* `portal-all.properties`: Contains the properties that change Liferay DXP across environments

* `portal-env.properties`: Contains the properties that only affect the current environment (for example, credentials and URL endpoints for external services that differ from environment to environment)

* `portal-clu.properties`: Contains the pre-configured properties for clustering Liferay DXP on DXP Cloud; see [Setting Up Clustering in DXP Cloud](./setting-up-clustering-in-dxp-cloud.md) for more information

* `portal-ext.properties`: Contains the final changes to the Liferay DXP configuration; since most properties are configured in `portal-all.properties` and `portal-env.properties`, this file is often empty or missing altogether

> **Note**: Portal properties may also be defined as environment variables. See [the environment variables reference](./introduction-to-the-liferay-dxp-service.md#environment-variables-reference) for more information.

## OSGi Configurations

OSGi configurations (`.cfg` or `.config` files) are used to configure OSGi components in Liferay DXP.

These configuration files belong in the `/osgi/configs` folder inside of `$LIFERAY_HOME`. When using Liferay DXP Cloud, place these files into the appropriate `config` folder(s) for them to be copied into `/osgi/configs` for the Liferay DXP instance on deployment.

## Additional Information

* [Introduction to the Liferay DXP Service](./introduction-to-the-liferay-dxp-service.md)
* [Enabling Clustering in DXP Cloud](./setting-up-clustering-in-dxp-cloud.md)
* [Portal Properties](https://help.liferay.com/hc/en-us/articles/360028712292-Portal-Properties)
