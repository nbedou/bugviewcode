Bug sphinx: `viewcode` cannot parse a Python file using the matrix multiplicator operator `@` (Python 3.5).


    conda create -n bugviewcode python=3.5 numpy
    source activate bugviewcode

Install dev versions of pygments and sphinx:

    pip install hg+https://bitbucket.org/birkenfeld/pygments-main
    pip install git+https://github.com/sphinx-doc/sphinx

    pip install -e . 

Refresh PATH:

    source deactive
    source activate bugviewcode

Run doc:

    cd doc
    make clean && make html

Error obtained:

    File "/home/nicolas/anaconda3/envs/bugviewcode/lib/python3.5/site-packages/pygments/filters/__init__.py", line 196, in filter
    
    pygments.filters.ErrorToken: @

Full trace in log file.

Debug
=====

`pygments` is able to parse '@' without problem:

    $pygmentize -V
    Pygments version 2.2a0, (c) 2006-2015 by Georg Brandl.

    $pygmentize -l python3 bugviewcode/__init__.py
    (no error)

`conda list`:

    # packages in environment at /home/nicolas/anaconda3/envs/bugviewcode:
    #
    alabaster                 0.7.7                     <pip>
    babel                     2.3.3                     <pip>
    bugviewcode (/home/nicolas/Python/bugviewcode) 0.1                       <pip>
    docutils                  0.12                      <pip>
    imagesize                 0.7.0                     <pip>
    jinja2                    2.8                       <pip>
    markupsafe                0.23                      <pip>
    mkl                       11.3.1                        0  
    numpy                     1.11.0                   py35_0  
    openssl                   1.0.2g                        0  
    pip                       8.1.1                    py35_1  
    pygments                  2.2.dev20160421           <pip>
    python                    3.5.1                         0  
    pytz                      2016.3                    <pip>
    readline                  6.2                           2  
    setuptools                20.7.0                   py35_0  
    six                       1.10.0                    <pip>
    snowballstemmer           1.2.1                     <pip>
    sphinx                    1.5a0.dev20160421           <pip>
    sqlite                    3.9.2                         0  
    tk                        8.5.18                        0  
    wheel                     0.29.0                   py35_0  
    xz                        5.0.5                         1  
    zlib                      1.2.8                         0  
