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

- nodejs v22

#### JS Libraries

- @heroicons/
  - react ^2.0.13
- @popperjs/
  - core ^2.11.6
- @tailwindcss/
  - forms ^0.5.3
- @testing-library/
  - jest-dom ^5.16.5
  - react ^13.4.0
  - user-event ^14.4.3
- @types/
  - node ^18.11.18
  - react ^18.0.26
  - react-dom ^18.0.10

- axios ^1.3.4
- bootstrap ^5.2.3
- browser-sync ^2.2.28.3
- c3 ^0.7.20
- chart.js ^4.2.1
- d3 ^7.8.0
- d3-selection-multi ^1.0.1
- gulp ^4.0.2
- gulp-sass ^5.1.0
- jsdoc-typeof-plugin ^1.0.0
- tailwindcss ^3.2.4
- typescript ^4.9.4
- react ^18.2.0
  - react-dom ^18.2.0
  - react-router-dom ^6.6.2
  - react-scripts ^5.0.1
- sass ^1.58.3
- web-vitals ^3.1.0

### LAMP packages

- Apache
  - mod_wsgi
- PHP v.8.1.32
- MariaDB 10.5.29 (compatible with MySQL 15.1)

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
