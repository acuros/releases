=================================
Releases, a Sphinx changelog tool
=================================

About
=====

Releases is a `Sphinx <http://sphinx-doc.org>`_ extension designed to help you
keep a source control friendly, merge friendly changelog file & turn it into a
useful, human readable HTML output.

Specifically:

* The source format is a stream-like timeline that plays well with source
  control & only requires one entry per change (even for changes that exist in
  multiple release lines).
* The output is a traditional looking changelog with a section for every
  release; multi-release issues are copied automatically into each release.
* By default, feature and support issues are only displayed under feature
  releases, and bugs are only displayed under bugfix releases. This can be
  overridden on a per-issue basis.

Usage
=====

Mimic the format seen `in Fabric's changelog
<https://raw.github.com/fabric/fabric/master/docs/changelog.rst>`_:

* Install ``releases`` and update your Sphinx ``conf.py`` to include it in the
  ``extensions`` list setting: ``extensions = ['releases']``.
* Create a docs file named ``changelog.rst`` with a top-level header followed
  by a bulleted list.
* Bullet list items must use the ``:support:``, ``:feature`` or ``:bug`` roles to
  mark issues, or ``:release:`` to mark a release. These special roles must be
  the first element in each list item.
* Issue roles are of the form ``:type:`number[ keyword]``. Keywords are
  optional and may be one of:

    * ``backported``: Given on support or feature issues to denote
      backporting to bugfix releases; will show up in both release types.
    * ``major``: Given on bug issues to denote inclusion in feature, instead
      of bugfix, releases.

* Regular Sphinx content may be given after issue roles and will be preserved
  as-is when rendering.
* Release roles are of the form ``:release:`number <date>```. Do not place any
  additional elements after release roles.

Then build your docs; ``changelog.html`` should show issues grouped by release,
as per the above rules.

TODO
====

* Migrate to a directive-driven (vs role-driven) format. Existing format
  evolved from a purely role-oriented, prose-embedded setup; roles are no
  longer the right way to do this.
* Possibly add more keywords to allow control over additional edge cases.