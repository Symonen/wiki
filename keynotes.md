
### [Alex Orlov Cython as a Game Changer for Efficiency PyCon 2017](https://www.youtube.com/watch?v=_1MSX7V28Po)

For simple solutions with small number of machines is no need for optimization you just add additional boxes. Readability and simplicity first.
If you have big enough infrastructure then think about optimization

1. Check algorithm first and check all options for pure python solutions
2. Extract piece of functionality and rewrite it as a microservice in faster language
3. Create lib in c++ rewrite some functionality and plug it to your python code
4. Use some alternative interpreter eg. pypy GrumPy ... ( probably need some migrations)
5. Sometimes updating CPython is the case
6. Adjust your code to Cython

### [Greg Price - Clearer Code at Scale: Static Types at Zulip and Dropbox - PyCon 2018](https://www.youtube.com/watch?v=0c46YHS3RY8)

Dropbox (2MLOC +) and Zulip and also instagram are using type annotations.

1. **mypy** for type annotation checking -> use it with your hooks with script (see Zulip script for mypy)

**Tools**
  * **MonkeyType** (facebook/instagram) - Tries to annotate functions automaticly in runtime (instagram using it in production)
  * **PyAnnotate** (dropbox) - same as above
  * **pytype** (google) - Statically check and infer types for unannotated Python code. (This is not an official Google product.)
  
  
### [Graham Dumpleton - Secrets of a WSGI master. - PyCon 2018](https://www.youtube.com/watch?v=CPz0s1CQsTE)

**WSGI is a specification for an Application Programming Interface** -> is not a wire protocol like http

1. Do not use raw WSGI use some web framework instead.
2. The development servers builtin to a framework are not good enough never use them in production!
3. There are couple of options to serve Python apps:\
    nginix  <-->  uWSGI/Unicorn ... <--> python app

4. Apache and mod_wsgi
    * Install mod_wsgi through pip: \
    `pip install mod_wsgi`
    * Running wsgi from command line\
    `mod_wsgi-express start-server wsgi.py` \
    predefined settings used by express are reasonable and good
    * Run as a dev server for django:\
    `python manage.py runmodwski --reload-on-changes` <- remember to add mod_wsgi to installed_apps
    * Run as a prod server:
    ```
    mod_wsgi-express start-server wsgi.py \ 
    --server-root /etc/wsgi-port-80 \
    --user www-data \ 
    --group www-data \
    --port 80 \
    --url-alias /static static\ 
    --setup-only
    ```
    

5. **Never run containers as a root**
6. wrapdrive project to simplify 
7. Don't user mode_wsgi embedded mode use deamon mode instead
8. Useful options:
    * startup-timeout
    * socket-timeout
    * queue-timeout
    * request-timeout
    

### [Cracking the coding interview](https://www.youtube.com/watch?v=v4cd1O4zkGw&list=PLX6IKgS15Ue02WDPRCmYKuZicQHit9kFt)

Step by step coding interview process:
1. Listen and understand
 * Ask for complexity and space constraints
 * Ask for example if you still don't understand
2. Think about examples
 * Create multiple examples that covers all difficulties
 * Think how you can test your code
3. Think about simplest solution
4. Think about optimal solution
5. Work throught your algorithm step by step with example
6. Code your solution
7. Test your code: edge cases ect.
 * Check edge cases
 * Think twice about lines of code that seems to you suspicious
8. Make improvements and optimizations if needed
