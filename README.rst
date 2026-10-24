.. image:: https://raw.githubusercontent.com/insanai/ccm/main/assets/ccm-logo.svg
   :width: 96px
   :alt: CCM
   :target: https://insanai.github.io/ccm/

CCM for Homebrew
=================

**Measure the code. Understand the change.**

This tap installs `CCM <https://github.com/insanai/ccm>`_ on macOS and Linux, on x86-64 and ARM64.
The formula downloads the matching native archive and verifies the SHA-256 published with that release.
It installs one executable and its license and build records.
It starts no service.

.. code-block:: sh

   brew tap insanai/ccm
   brew install insanai/ccm/ccm
   ccm .

To follow a newer release:

.. code-block:: sh

   brew update
   brew upgrade insanai/ccm/ccm

Release synchronization
------------------------

The hourly workflow follows CCM's GitHub Latest release, including versions whose names contain beta.
It can also be run through ``gh workflow run sync.yml --repo insanai/homebrew-ccm``.
The workflow downloads that release's checksum manifest and checks out the matching source tag.
CCM's Rust ``cargo xtask homebrew`` generator writes the formula from those checksums.
The workflow tests installation on macOS before committing the new formula and release marker.
Only changed releases cause an update.

The workflow uses this repository's GitHub Actions token and needs no personal token copied from the CCM repository.
The generated formula supports the four macOS and Linux native archives; Windows and FreeBSD archives are available directly from `CCM releases <https://github.com/insanai/ccm/releases>`_.

Documentation and license
---------------------------

The `CCM website <https://insanai.github.io/ccm/>`_ provides the book, PDF, examples, and design records.
CCM is LGPL-3.0-or-later; third-party materials retain their own terms.
Organizations seeking other licensing terms can contact `Vikrant Rathore <mailto:admin@vyomtech.com>`_.
The formula source and synchronization configuration in this tap are also LGPL-3.0-or-later.
