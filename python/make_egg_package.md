## Knowledge base for Python
How to build an egg package in steps </br></br>
 1) Create setup.py file in root dir, use template below:
  
  ```python

from setuptools import setup, find_packages


__version__ = "0.0.1"


setup(
    # package name in pypi
    name='package_name',
    # extract version from module.
    version=__version__,
    description="",
    long_description="",
    classifiers=[],
    keywords='',
    author='',
    author_email='',
    url='',
    license='',
    # include all packages in the egg, except the test package.
    packages=find_packages(exclude=['ez_setup', 'examples', 'tests']),
    # for avoiding conflict have one namespace for all apc related eggs.
    namespace_packages=['namespace_package_name'],
    # include non python files
    include_package_data=True,
    zip_safe=False,
    # specify dependencies
    install_requires=[
        'distribute',
    ],
    # mark test target to require extras.
    extras_require = {
        'test':  ["mock"]
    },
    # generate scripts
    entry_points={
        'console_scripts':[
            'script_name = name.module:main',
        ]
    },
    scripts=[
        'script_name',
    ],
)
```

2) Example setup.py file:

```python
from setuptools import setup, find_packages


__version__ = "0.0.1"


setup(
    # package name in pypi
    name='rpiscan',
    # extract version from module.
    version=__version__,
    description="Raspberry PI application for handling production",
    classifiers=[],
    keywords='raspberrypi',
    author='devsyst',
    author_email='pgzella@devsyst.com',
    url='https://github.com/VentureGroup/RPIScan',
    license='VentureGroup',
    # include all packages in the egg, except the test package.
    packages=find_packages(exclude=['examples', 'tests']),
    # for avoiding conflict have one namespace for all apc related eggs.
    namespace_packages=[],
    # include non python files
    include_package_data=True,
    zip_safe=False,
    # specify dependencies
    install_requires=[
        'setuptools',
    ],
    # mark test target to require extras.
    extras_require = {
        'test':  []
    },
    # generate scripts
    entry_points={
        'console_scripts':[
            'rpiscan = rpiscan.startscreen:main',
        ]
    },
)
```

3) Run:   ```python sudo python setup.py install ```

   to generate egg and install dependencies

