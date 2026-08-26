# OpenGameData Software Reference Platform

Below is a list of standard software libraries that make up the **OpenGameData Reference Platform**. This **reference platform** is meant as a *convention* for keeping new development coordinated with respect to the development and deployment environments.

## Justification

The bar for updating a package is relatively low, we only require some simple justification,
e.g. "we need a feature from a newer version to make X better,"
or "the current version is old and nobody uses it anymore,"
or "another library needs a newer version."

In general, we avoid allowing projects to become so oddly-specific as to be tied to a specific package/version. The onus is on us to keep OGD projects running on relatively recent library versions, to keep a low barrier for entry to new collaborators who want to start fresh.

However, any OpenGameData project should avoid using a different version of any of these libraries than what is listed. Instead, ask for a version bump and wait for an update to the platform, so we don’t have incompatibilities pop up at random.

We use this list for GitHub Actions, requirements.txt, and .devcontainer files.
Note: for some libraries, we use .* to indicate any patch version may be used (we only specify patch version for mission-critical dependencies, such as database libraries).

## External Packages Platform

### Python

- [Python](https://www.python.org/): [3.12](https://www.python.org/downloads/release/python-31214/)

#### Python Libraries

| Package                                               | Version                                 |
| ---                                                   | ---                                     |
| [gitdb][gitdb-link]                                   | [4.0.*](https://pypi.org/project/gitdb/4.0.12/) |
| [GitPython][gitpy-link]                               | [3.1.*](https://pypi.org/project/GitPython/3.1.44/) |
| [flask][flask-link]                                   | [2.3.3](https://pypi.org/project/Flask/2.3.3/) |
| [flask-cors][flask-cors-link]                         | [6.0.1](https://pypi.org/project/flask-cors/6.0.1/) |
| [flask-restful][flask-rest-link]                      | [0.3.10](https://pypi.org/project/Flask-RESTful/0.3.10/) |
| [Flask-SocketIO][flask-socket-link]                   | [5.3.6](https://pypi.org/project/Flask-SocketIO/5.3.6/) |
| [google-auth][google-auth-link]                       | [2.16.1](https://pypi.org/project/google-auth/2.16.1/) |
| [google-cloud-bigquery][google-bq-link]               | [3.37.0](https://pypi.org/project/google-cloud-bigquery/3.37.0) |
| [google-cloud-bigquery-storage][google-bq-store-link] | [2.33.1](https://pypi.org/project/google-cloud-bigquery-storage/2.33.1) |
| [ipywidgets][ipywid-link]                             | [8.0.*](https://pypi.org/project/ipywidgets/8.0.7) |
| [matplotlib][matplotlib-link]                         | [3.9.*](https://pypi.org/project/matplotlib/3.9.4) |
| [mysql-connector-python][mysql-py-link]               | [9.3.0](https://pypi.org/project/mysql-connector-python/9.3.0) |
| [numpy][numpy-link]                                   | [2.1.*](https://pypi.org/project/numpy/2.1.3) |
| [pandas][pandas-link]                                 | [2.2.*](https://pypi.org/project/pandas/2.2.3) |
| [paramiko][paramiko-link]                             | [3.5.*](https://pypi.org/project/paramiko/3.5.1/) |
| [pyOpenSSL][pyOpenSSL-link]                           | [23.0.*](https://pypi.org/project/pyOpenSSL/23.0.0/) |
| [python-dateutil][dateutil-link]                      | [2.9.*](https://pypi.org/project/python-dateutil/2.9.0.post0/) |
| [requests][requests-link]                             | [2.32.*](https://pypi.org/project/requests/2.32.5) |
| [scikit-learn][scikit-link]                           | [1.5.*](https://pypi.org/project/scikit-learn/1.5.2) |
| [seaborn][seaborn-link]                               | [0.13.*](https://pypi.org/project/seaborn/0.13.2) |
| [sshtunnel][sshtunnel-link]                           | [0.4.0](https://pypi.org/project/sshtunnel/0.4.0) |
| [statsmodels][statsmods-link]                         | [0.14.*](https://pypi.org/project/statsmodels/0.14.5) |
| [tensorflow][tensorflow-link]                         | [2.17.*](https://pypi.org/project/tensorflow/2.17.1) |

[gitdb-link]: https://pypi.org/project/gitdb/
[gitpy-link]: https://pypi.org/project/GitPython/
[flask-link]: https://flask.palletsprojects.com/en/stable/
[flask-cors-link]: https://pypi.org/project/flask-cors/
[flask-rest-link]: https://pypi.org/project/Flask-RESTful/
[flask-socket-link]: https://pypi.org/project/Flask-SocketIO/
[google-auth-link]: https://pypi.org/project/google-auth/
[google-bq-link]: https://pypi.org/project/google-cloud-bigquery/
[google-bq-store-link]: https://pypi.org/project/google-cloud-bigquery-storage/
[ipywid-link]: https://pypi.org/project/ipywidgets/
[matplotlib-link]: https://matplotlib.org/
[mysql-py-link]: https://pypi.org/project/mysql-connector-python/
[numpy-link]: https://numpy.org/
[pandas-link]: https://pandas.pydata.org/
[paramiko-link]: https://www.paramiko.org/
[pyopenssl-link]: https://pypi.org/project/pyOpenSSL/
[dateutil-link]: https://pypi.org/project/python-dateutil/
[requests-link]: https://pypi.org/project/requests/
[scikit-link]: https://scikit-learn.org/stable/
[seaborn-link]: http://seaborn.pydata.org/
[sshtunnel-link]: https://pypi.org/project/sshtunnel/
[statsmods-link]: https://www.statsmodels.org/
[tensorflow-link]: https://www.tensorflow.org/

#### Python Build Tools

| Package                                     | Version                                 |
| ---                                         | ---                                     |
| [build][build-link]                         | [1.2.*](https://pypi.org/project/build/1.2.2.post1/) |
| [setuptools][setup-link]                    | [74.1.*](https://pypi.org/project/setuptools/74.1.3/) |
| [setuptools-git-versioning][setup-git-link] | [2.0.*](https://pypi.org/project/setuptools-git-versioning/2.0.0/) |
| [twine][twine-link]                         | [5.1.1](https://pypi.org/project/twine/5.1.1/) |
| [wheel][wheel-link]                         | [0.44.*](https://pypi.org/project/wheel/0.44.0/) |

[build-link]: https://pypi.org/project/build/
[setup-link]: https://setuptools.pypa.io/en/latest/
[setup-git-link]: https://pypi.org/project/setuptools-git-versioning/
[twine-link]: https://pypi.org/project/twine/
[wheel-link]: https://pypi.org/project/wheel/

### JavaScript

- [nodejs](https://nodejs.org/en): [v22](https://nodejs.org/en/download/archive/v22)

#### JS Libraries

| Package                                        | Version        |
| ---                                            | ---            |
| [@heroicons/react][heroicons-link]             | [^2.0.13](https://www.npmjs.com/package/@heroicons/react/v/2.0.13)    |
| [@popperjs/core][popper-link]                  | [^2.11.6](https://www.npmjs.com/package/@popperjs/core/v/2.11.6)    |
| [@tailwindcss/forms][tailwindforms-link]       | [^0.5.3](https://www.npmjs.com/package/@tailwindcss/forms/v/0.5.3)     |
| [@testing-library/jest-dom][jest-dom-link]     | [^5.16.5](https://www.npmjs.com/package/@testing-library/jest-dom/v/5.16.5)    |
| [@testing-library/react][test-react-link]      | [^13.4.0](https://www.npmjs.com/package/@testing-library/react/v/13.4.0)    |
| [@testing-library/user-event][user-event-link] | [^14.4.3](https://www.npmjs.com/package/@testing-library/user-event/v/14.4.3)    |
| [@types/node][node-type-link]                  | [^18.11.18](https://www.npmjs.com/package/@types/node/v/18.11.18)  |
| [@types/react][react-type-link]                | [^18.0.26](https://www.npmjs.com/package/@types/react/v/18.0.26)   |
| [@types/react-dom][react-dom-type-link]        | [^18.0.10](https://www.npmjs.com/package/@types/react-dom/v/18.0.10)   |
| [axios][axios-link]                            | [^1.3.4](https://www.npmjs.com/package/axios/v/1.3.4) |
| [bootstrap][bootstrap-link]                    | [^5.2.3](https://www.npmjs.com/package/bootstrap/v/5.3.4) |
| [browser-sync][browsync-link]                  | ^2.2.28.3 |
| [c3][c3-link]                                  | [^0.7.20](https://www.npmjs.com/package/c3/v/0.7.20) |
| [chart.js][chart-link]                         | [.js ^4.2.1](https://www.npmjs.com/package/chart.js/v/4.2.1) |
| [d3][d3-link]                                  | [^7.8.0](https://www.npmjs.com/package/d3/v/7.8.0) |
| [d3-selection-multi][d3-select-link]           | [^1.0.1](https://www.npmjs.com/package/d3-selection-multi/v/1.0.1) |
| [gulp][gulp-link]                              | [^4.0.2](https://www.npmjs.com/package/gulp/v/4.0.2) |
| [gulp-sass][gulp-sass-link]                    | [^5.1.0](https://www.npmjs.com/package/gulp-sass/v/5.1.0) |
| [jsdoc-typeof-plugin][jsdoc-type-link]         | [^1.0.0](https://www.npmjs.com/package/jsdoc-typeof-plugin/v/1.0.0) |
| [tailwindcss][tailwind-link]                   | [^3.2.4](https://www.npmjs.com/package/tailwindcss/v/3.2.4) |
| [typescript][typescript-link]                  | [^4.9.4](https://www.npmjs.com/package/typescript/v/4.9.4) |
| [react][react-link]                            | [^18.2.0](https://www.npmjs.com/package/react/v/18.2.0) |
| [react-dom][react-dom-link]                    | [^18.2.0](https://www.npmjs.com/package/react-dom/v/18.2.0) |
| [react-router-dom][react-router-link]          | [^6.6.2](https://www.npmjs.com/package/react-router-dom/v/6.6.2) |
| [react-scripts][react-scripts-link]            | [^5.0.1](https://www.npmjs.com/package/react-scripts/v/5.0.1) |
| [sass][sass-link]                              | [^1.58.3](https://www.npmjs.com/package/sass/v/1.58.3) |
| [web-vitals][web-vitals-link]                  | [^3.1.0](https://www.npmjs.com/package/web-vitals/v/3.1.0) |

[heroicons-link]: https://github.com/tailwindlabs/heroicons#readme
[popper-link]: https://github.com/popperjs/popper-core#readme
[tailwindforms-link]: https://github.com/tailwindlabs/tailwindcss-forms#readme
[jest-dom-link]: https://github.com/testing-library/jest-dom#readme
[test-react-link]: https://github.com/testing-library/react-testing-library#readme
[user-event-link]: https://github.com/testing-library/user-event#readme
[node-type-link]: https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/node
[react-type-link]: https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/react
[react-dom-type-link]: https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/react-dom
[axios-link]: https://axios-http.com/
[bootstrap-link]: https://getbootstrap.com/
[browsync-link]: https://browsersync.io/
[c3-link]: https://github.com/c3js/c3#readme
[chart-link]: https://www.chartjs.org/
[d3-link]: https://d3js.org/
[d3-select-link]:https://github.com/d3/d3-selection-multi 
[gulp-link]: https://gulpjs.com/
[gulp-sass-link]: https://github.com/dlmanning/gulp-sass#readme
[jsdoc-type-link]: https://www.npmjs.com/package/jsdoc-typeof-plugin
[tailwind-link]: https://tailwindcss.com/
[typescript-link]: https://www.typescriptlang.org/
[react-link]: https://reactjs.org/
[react-dom-link]: https://reactjs.org/
[react-router-link]: https://reactrouter.com/
[react-scripts-link]: https://github.com/facebook/create-react-app#readme
[sass-link]: https://sass-lang.com/
[web-vitals-link]: https://github.com/GoogleChrome/web-vitals#readme

### LAMP software

| Package                 | Version  |
| ---                     | ---      |
| [Apache][apache-link]   | -        |
| [mod_wsgi][wsgi-link]   | -        |
| [PHP][php-link]         | v.8.1.32 |
| [MariaDB][mariadb-link] | 10.5.29 (compatible with MySQL 15.1) |

[apache-link]: https://httpd.apache.org/
[wsgi-link]: https://modwsgi.readthedocs.io/en/master/
[php-link]: https://www.php.net/
[mariadb-link]: https://mariadb.org/

### GitHub Actions

| Package                                        | Version                                 |
| ---                                            | ---                                     |
| [actions/checkout][checkout-link]              | [v4](https://github.com/actions/checkout/releases/tag/v4.3.1) |
| [actions/cache/save][cache-save-link]          | [v4](https://github.com/actions/cache/releases/tag/v4.3.0) |
| [actions/cache/restore][cache-restore-link]    | [v4](https://github.com/actions/cache/releases/tag/v4.3.0) |
| [actions/upload-artifact][upload-link]         | [v4](https://github.com/actions/upload-artifact/releases/tag/v4.6.2) |
| [actions/setup-node][setup-node-link]          | [v4.4.0](https://github.com/actions/setup-node/releases/tag/v4.4.0) |
| [actions/setup-python][setup-py-link]          | [v5.3](https://github.com/actions/setup-python/releases/tag/v5.3.0) |
| [burnett01/rsync-deployment][rsync-link]       | [7.0.1](https://github.com/burnett01/rsync-deployment/releases/tag/7.0.1) |
| [google-github-actions/auth][google-auth-link] | [v3](https://github.com/google-github-actions/auth/releases/tag/v3) |

[checkout-link]: https://github.com/actions/checkout
[cache-save-link]: https://github.com/actions/cache/
[cache-restore-link]: https://github.com/actions/cache
[upload-link]: https://github.com/actions/upload-artifact
[setup-node-link]: https://github.com/actions/setup-node
[setup-py-link]: https://github.com/actions/setup-python
[rsync-link]: https://github.com/burnett01/rsync-deployment
[google-auth-link]: https://github.com/google-github-actions/auth

## OpenGameData Tools & Libraries - Compatible with Platform

The following releases of tools, libraries, and APIs from the OpenGameData community are compatible with the platform version outlined above, and are recommended for use with any projects using this version of the platform:

- Libraries
  - opengamedata-core >= 0.0.14
  - opengamedata-common >= 2.0.0
  - OGDUtils >= 2.1.0
  - APIUtils >= 1.1.0
- Tools
- GitHub Actions
  - opengamedata/actions-openconnect-vpn >= v1.1
  - opengamedata/actions-setup-ogd-py-dependencies >= v1.2
  - opengamedata/actions-setup-ogd-py-build >= v2.0
  - opengamedata/actions-setup-fd-git >= v1.0
  - opengamedata/actions-execute-testbed >= v1.0
