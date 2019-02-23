Migration
=========

Migrate from API v1 to v2.0.0
-----------------------------

API version 2 was introduced along with Ulauncher v5 after migrating from Python 2 to 3.

.. TODO: add description of new features introduced in API 2

*Required actions:*

1. Remove ``manifest_version`` from ``manifest.json``. It's no longer needed
2. Also rename ``api_version`` to ``required_api_version``
3. ``required_api_version`` should follow `NPM Semver <https://docs.npmjs.com/misc/semver>`_ format. In most of the cases you would want to specify a string like ``^x.y.z`` where ``x.y.z`` is the current version of extension API (not Ulauncher).
4. Migrate your extension to Python 3 manually or by using `2to3 tool <https://docs.python.org/2/library/2to3.html>`_ for example
5. Create a file called ``versions.json`` in the **root** directory of **master** branch with the following content:

  ::

    [
      {"required_api_version": "^1.0.0", "commit": "abcd1234"},
      {"required_api_version": "^2.0.0", "commit": "my-branch-with-api-v2-support"}
    ]

  For more details about ``version.json``, see `tutorial <tutorial.html#versions-json>`__.

----

.. NOTE::
  Please take `a short survey <https://goo.gl/forms/wcIRCTjQXnO0M8Lw2>`_ to help us build greater API and documentation