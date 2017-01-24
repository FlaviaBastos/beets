.. _setup:

The development setup
=====================

Obtain a copy of the source code
--------------------------------
In the top-right corner of the `beets GitHub repository page <https://github.com/beetbox/beets>`_, click Fork. This will make a copy of beets repository under your GitHub ID.

Create a local clone of your fork on your computer:

* On GitHub, navigate to **your fork** of the beets repository
* Click **Clone or download**
* Copy the clone URL for the repository
* In the terminal, type ``git clone`` and paste the URL you copied - it will look like this, with your GitHub user name instead of ``YOUR-USERNAME``::

    git clone https://github.com/*YOUR-USERNAME*/beets.git

Now you have a local copy of your fork of the beets repository.

Configure Git to sync your fork with the original beets repository:

* On GitHub, navigate to beets repository, click **Clone or download** and copy the beets URL
* In the terminal type::

    cd beets/
    git remote -v
This will show the current configured remote repository for your fork.

* Type ``git remote add upstream`` and paste the URL you copied. It will look like this::

    git remote add upstream https://github.com/beetbox/beets.git
* Verify the new upstream repository::

    git remote -v
This will show the URL for your fork as ``origin`` and the URL for the original beets repository as ``upstream``.

In the future you will want to keep your fork synced with the beets upstream repository. Please see GitHub's `Syncing a fork <https://help.github.com/articles/syncing-a-fork/>`_ documentation.

External Dependencies
---------------------
* Python 2.7 and Python 3.4 or later


Your local python environment
-----------------------------

Please execute ``python -V`` or ``python3 -V`` to make sure you have Python 3.4 (or newer) installed. Also make sure you have pip for Python 3 installed, you can execute ``pip3 -V`` to check. Then use Python's internal tools to create a virtual environment and activate it for your current session::

    python3 -m venv env
    source env/bin/activate

You should now see a ``(env)`` prepended to your shell prompt.

Working with the code
----------------------
To install beets, run::

    python setup.py install

If this is the first time you are running beets, the next steps are:

* `Configure it <http://beets.readthedocs.io/en/v1.4.3/guides/main.html#configuring>`_
* `Import your library <http://beets.readthedocs.io/en/v1.4.3/guides/main.html#importing-your-library>`_

Create a new branch for your code
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
When contributing to a project it's a good idea to create a separate branch to develop new code. You can do so this way:

* Make sure your fork is in `sync with beets project <https://help.github.com/articles/syncing-a-fork/>`_
* Tell Git where you want to make a branch from::

    git checkout upstream/master
* Create your branch::

    git checkout -b your_branch_name
* Push your new branch to your remote fork on GitHub::

    git push -u origin your_branch_name

You can run ``git branch`` to make sure you are working on your newly created branch. The branch you are in will have a '*' next to it.


Code checks and unit tests
^^^^^^^^^^^^^^^^^^^^^^^^^^
Before you check in your code into git, always run the static checkers and unit tests. In the terminal type::

    nosetests

Be aware that the tests have a few more dependencies than beets itself. You can read more about `test dependencies in the beets wiki. <https://github.com/beetbox/beets/wiki/Testing>`_


Submitting your code for review
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
After your tests have passed you can commit your code into git and submit it for review.

* Check which files are modified are ready to be committed::

    git status
* Add files to the staging area::

    git add file_name

* Commit::

    git commit -m "commit message"

* Push your code to your remote repository in GitHub::

    git push
If you visit your repository page in GitHub and select your new branch, it will show that you have new code that is not present in the original beets repository. Click on **New pull request** and provide information about the changes you are submitting. Then click on **Create pull request**. The project maintainer will receive a notification about your new code and give you feedback.
Once your pull request is accepted, your code will be merged into beets master branch and you can go ahead and delete the branch you created for this issue. You can delete your branch this way::

    git checkout master
    git branch -d your_branch_name
    git push
