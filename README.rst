====
PRam
====

This is an enhanced rewrite of Patrice Clement's pram utility, in bash
[#CLEMENT-PRAM]_.  It is a tool to ease merging of pull requests
and git format patches to ebuild repositories.  It incorporates
the requirements of Gentoo policies and reduces the necessity
of manually updating commit messages [#GLEP66]_ [#GLEP76]_.


Merging pull requests
---------------------
To merge GitHub PR #12345, enter your local gentoo.git checkout
and type::

    pram 12345

This will fetch it from gentoo/gentoo repository, verify the presence
of author's sign-off, append appropriate ``Closes`` trailer and merge
it via ``git am``.

You can request referencing or closing additional bugs using ``--bug``
and ``--closes`` options appropriately (they can be specified multiple
times).  Note that PRam appends the relevant trailers only to the last
commit in batch; you may want to move them around via editor.


Merging Bugzilla patches
------------------------
PRam can also merge patches from Gentoo Bugzilla.  To do that, use
the full URL to the patch file, e.g.::

    pram https://123456.bugs.gentoo.org/attachment.cgi?id=123456

PRam will automatically request closing that bug as well.  If this is
undesirable, remove the added ``Closes`` trailer via editor.


Working with other repositories
-------------------------------
You can easily use PRam with other repositories.  You can either use
the ``--repository`` option to override the remote GitHub repository
or specify a full PR URL::

    pram -r foo/gentoo 123
    pram https://github.com/foo/gentoo/pull/123

If your repository does not use DCO/GCO, you can use ``--no-signoff``
option to disable requiring sign-off.


References
----------
.. [#CLEMENT-PRAM] Patrice Clement: Gentoo-App-Pram
   (https://github.com/monsieurp/Gentoo-App-Pram/)

.. [#GLEP66] GLEP 66: Gentoo Git Workflow
   (https://www.gentoo.org/glep/glep-0066.html)

.. [#GLEP76] GLEP 76: Copyright Policy
   (https://www.gentoo.org/glep/glep-0076.html)


Copyright
---------
This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License along
with this program; if not, write to the Free Software Foundation, Inc.,
51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
