# Django - Sessions
## What it is ?
## Where to store data ? (3 types)
### (1). DB-based (by default)
### (2). Cache-based
### (3). File-based
## How to Enable in Django
### (1). MIDDLEWARE 
### (2). INSTALLED_APPS
## How to use in Django views

    __getitem__(key)
    Example: fav_color = request.session['fav_color']

    __setitem__(key, value)
    Example: request.session['fav_color'] = 'blue'

    __delitem__(key)
    Example: del request.session['fav_color']. This raises KeyError if the given key isn’t already in the session.

    __contains__(key)
    Example: 'fav_color' in request.session
