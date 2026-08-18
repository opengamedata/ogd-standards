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

- Python: 3.12

#### Python Libraries

| Package                                                                                  | Version                                 |
| ---                                                                                      | ---                                     |
| [gitdb](https://pypi.org/project/gitdb/)                                                 | [4.0.*](https://pypi.org/project/gitdb/4.0.12/) |
| [GitPython](https://pypi.org/project/GitPython/)                                         | [3.1.*](https://pypi.org/project/GitPython/3.1.44/) |
| [flask](https://flask.palletsprojects.com/en/stable/)                                    | [2.3.3](https://pypi.org/project/Flask/2.3.3/) |
| [flask-cors](https://pypi.org/project/flask-cors/)                                       | [6.0.1](https://pypi.org/project/flask-cors/6.0.1/) |
| [flask-restful](https://pypi.org/project/Flask-RESTful/)                                 | [0.3.10](https://pypi.org/project/Flask-RESTful/0.3.10/) |
| [Flask-SocketIO](https://pypi.org/project/Flask-SocketIO/)                               | [5.3.6](https://pypi.org/project/Flask-SocketIO/5.3.6/) |
| [google-auth](https://pypi.org/project/google-auth/)                                     | [2.16.1](https://pypi.org/project/google-auth/2.16.1/) |
| [google-cloud-bigquery](https://pypi.org/project/google-cloud-bigquery/)                 | [3.37.0](https://pypi.org/project/google-cloud-bigquery/3.37.0) |
| [google-cloud-bigquery-storage](https://pypi.org/project/google-cloud-bigquery-storage/) | [2.33.1](https://pypi.org/project/google-cloud-bigquery-storage/2.33.1) |
| [ipywidgets](https://pypi.org/project/ipywidgets/)                                       | [8.0.*](https://pypi.org/project/ipywidgets/8.0.7) |
| [matplotlib](https://matplotlib.org/)                                                    | [3.9.*](https://pypi.org/project/matplotlib/3.9.4) |
| [mysql-connector-python](https://pypi.org/project/mysql-connector-python/)               | [9.3.0](https://pypi.org/project/mysql-connector-python/9.3.0) |
| [numpy](https://numpy.org/)                                                              | [2.1.*](https://pypi.org/project/numpy/2.1.3) |
| [pandas](https://pandas.pydata.org/)                                                     | [2.2.*](https://pypi.org/project/pandas/2.2.3) |
| paramiko                                                                                 | 3.5.* |
| pyOpenSSL                                                                                | 23.0.* |
| [requests](https://pypi.org/project/requests/)                                           | [2.32.*](https://pypi.org/project/requests/2.32.5) |
| [scikit-learn](https://scikit-learn.org/stable/)                                         | [1.5.*](https://pypi.org/project/scikit-learn/1.5.2) |
| [seaborn](http://seaborn.pydata.org/)                                                    | [0.13.*](https://pypi.org/project/seaborn/0.13.2) |
| [sshtunnel](https://pypi.org/project/sshtunnel/)                                         | [0.4.0](https://pypi.org/project/sshtunnel/0.4.0) |
| [statsmodels](https://www.statsmodels.org/)                                              | [0.14.*](https://pypi.org/project/statsmodels/0.14.5) |
| [tensorflow](https://www.tensorflow.org/)                                                | [2.17.*](https://pypi.org/project/tensorflow/2.17.1) |

#### Python Build Tools

| Package                                                                          | Version                                 |
| ---                                                                              | ---                                     |
| [build](https://pypi.org/project/build/)                                         | [1.2.*](https://pypi.org/project/build/1.2.2.post1/) |
| [setuptools](https://setuptools.pypa.io/en/latest/)                              | [74.1.*](https://pypi.org/project/setuptools/74.1.3/) |
| [setuptools-git-versioning](https://pypi.org/project/setuptools-git-versioning/) | [2.0.*](https://pypi.org/project/setuptools-git-versioning/2.0.0/) |
| [twine](https://pypi.org/project/twine/)                                         | [5.1.1](https://pypi.org/project/twine/5.1.1/) |
| [wheel](https://pypi.org/project/wheel/)                                         | [0.44.*](https://pypi.org/project/wheel/0.44.0/) |

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

| Package                                                                     | Version                                 |
| ---                                                                         | ---                                     |
| [actions/checkout](https://github.com/actions/checkout)                     | [v4](https://github.com/actions/checkout/releases/tag/v4.3.1) |
| [actions/cache/save](https://github.com/actions/cache/)                     | [v4](https://github.com/actions/cache/releases/tag/v4.3.0) |
| [actions/cache/restore](https://github.com/actions/cache)                   | [v4](https://github.com/actions/cache/releases/tag/v4.3.0) |
| [actions/upload-artifact](https://github.com/actions/upload-artifact)       | [v4](https://github.com/actions/upload-artifact/releases/tag/v4.6.2) |
| [actions/setup-node](https://github.com/actions/setup-node)                 | [v4.4.0](https://github.com/actions/setup-node/releases/tag/v4.4.0) |
| [actions/setup-python](https://github.com/actions/setup-python)             | [v5.3](https://github.com/actions/setup-python/releases/tag/v5.3.0) |
| [burnett01/rsync-deployment](https://github.com/burnett01/rsync-deployment) | [7.0.1](https://github.com/burnett01/rsync-deployment/releases/tag/7.0.1) |
| [google-github-actions/auth](https://github.com/google-github-actions/auth) | [v3](https://github.com/google-github-actions/auth/releases/tag/v3) |

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
