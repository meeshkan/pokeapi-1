# Notes

My notes on testing using schemathesis.

## Builder

1. Created and activated a python virtual environment using `virtualenv`.
1. Installed `schemathesis`.
1. Saw that there was a Makefile. Read it to see what commands were there. Ran `make install`, which looks like standard pip install.
1. Ran `make setup`, which looks like it applies a bunch of Django migrations.
1. Ran `make serve`, which booted up a server.
1. Determined the host and port by reading the source code. The Makefile's `make serve` calls a file called `manage.py`, which uses a local config. The local config does not explicity set the host and port, so it will be the Django default of `127.0.0.1:8000`.
1. Noticed that there is no OpenAPI spec and installed [`drf-yasg`](https://github.com/axnsan12/drf-yasg) to try to auto-generate one.
1. Followed the `drf-yasg` documentation, adding the appropriate boilerplate to `urls.py` and `settings.py`.
1. Grabbed the generated `http://localhost:8000/swagger.yaml` and converted to OpenAPI 3.0 using Swaggerhub. It worked (even though swaggerhub raised an error, don't know what that's about...).
1. Ran `schemathesis 
run .\openapi.yaml --base-url http://localhost:8000` successfully.

## Runner

```bash
schemathesis 
run .\openapi.yaml --base-url http://localhost:8000
=================== Schemathesis test session starts ===================
platform Windows -- Python 3.7.3, schemathesis-1.1.0, hypothesis-5.8.0, 
hypothesis_jsonschema-0.12.0, jsonschema-3.2.0
rootdir: C:\Users\MikeSolomon\devel\test-apis\pokeapi-1
hypothesis profile 'default' -> database=DirectoryBasedExampleDatabase('C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.hypothesis\\examples')
Schema location: file:///C:/Users/MikeSolomon/devel/test-apis/pokeapi-1/openapi.yaml
Base URL: http://localhost:8000
Specification version: Open API 3.0.0
Workers: 1
collected endpoints: 97

GET /api/v2/ability/ E                                           [  1%]
GET /api/v2/ability/{id}/ F                                      [  2%]
GET /api/v2/berry-firmness/ .                                    [  3%]
GET /api/v2/berry-firmness/{id}/ F                               [  4%]
GET /api/v2/berry-flavor/ .                                      [  5%]
GET /api/v2/berry-flavor/{id}/ F                                 [  6%]
GET /api/v2/berry/ .                                             [  7%]
GET /api/v2/berry/{id}/ F                                        [  8%]
GET /api/v2/characteristic/ .                                    [  9%]
GET /api/v2/characteristic/{id}/ F                               [ 10%]
GET /api/v2/contest-effect/ .                                    [ 11%]
GET /api/v2/contest-effect/{id}/ F                               [ 12%]
GET /api/v2/contest-type/ .                                      [ 13%]
GET /api/v2/contest-type/{id}/ F                                 [ 14%]
GET /api/v2/egg-group/ .                                         [ 15%]
GET /api/v2/egg-group/{id}/ F                                    [ 16%]
GET /api/v2/encounter-condition-value/ .                         [ 17%]
GET /api/v2/encounter-condition-value/{id}/ F                    [ 18%]
GET /api/v2/encounter-condition/ .                               [ 19%]
GET /api/v2/encounter-condition/{id}/ F                          [ 20%]
GET /api/v2/encounter-method/ .                                  [ 21%]
GET /api/v2/encounter-method/{id}/ F                             [ 22%]
GET /api/v2/evolution-chain/ .                                   [ 23%]
GET /api/v2/evolution-chain/{id}/ F                              [ 24%]
GET /api/v2/evolution-trigger/ .                                 [ 25%]
GET /api/v2/evolution-trigger/{id}/ F                            [ 26%]
GET /api/v2/gender/ .                                            [ 27%]
GET /api/v2/gender/{id}/ F                                       [ 28%]
GET /api/v2/generation/ .                                        [ 29%]
GET /api/v2/generation/{id}/ F                                   [ 30%]
GET /api/v2/growth-rate/ .                                       [ 31%]
GET /api/v2/growth-rate/{id}/ F                                  [ 32%]
GET /api/v2/item-attribute/ .                                    [ 34%]
GET /api/v2/item-attribute/{id}/ F                               [ 35%]
GET /api/v2/item-category/ .                                     [ 36%]
GET /api/v2/item-category/{id}/ F                                [ 37%]
GET /api/v2/item-fling-effect/ .                                 [ 38%]
GET /api/v2/item-fling-effect/{id}/ F                            [ 39%]
GET /api/v2/item-pocket/ .                                       [ 40%]
GET /api/v2/item-pocket/{id}/ F                                  [ 41%]
GET /api/v2/item/ .                                              [ 42%]
GET /api/v2/item/{id}/ F                                         [ 43%]
GET /api/v2/language/ .                                          [ 44%]
GET /api/v2/language/{id}/ F                                     [ 45%]
GET /api/v2/location-area/ .                                     [ 46%]
GET /api/v2/location-area/{id}/ F                                [ 47%]
GET /api/v2/location/ .                                          [ 48%]
GET /api/v2/location/{id}/ F                                     [ 49%]
GET /api/v2/machine/ .                                           [ 50%]
GET /api/v2/machine/{id}/ F                                      [ 51%]
GET /api/v2/move-ailment/ .                                      [ 52%]
GET /api/v2/move-ailment/{id}/ F                                 [ 53%]
GET /api/v2/move-battle-style/ .                                 [ 54%]
GET /api/v2/move-battle-style/{id}/ F                            [ 55%]
GET /api/v2/move-category/ .                                     [ 56%]
GET /api/v2/move-category/{id}/ F                                [ 57%]
GET /api/v2/move-damage-class/ .                                 [ 58%]
GET /api/v2/move-damage-class/{id}/ F                            [ 59%]
GET /api/v2/move-learn-method/ .                                 [ 60%]
GET /api/v2/move-learn-method/{id}/ F                            [ 61%]
GET /api/v2/move-target/ .                                       [ 62%]
GET /api/v2/move-target/{id}/ F                                  [ 63%]
GET /api/v2/move/ .                                              [ 64%]
GET /api/v2/move/{id}/ F                                         [ 65%]
GET /api/v2/nature/ .                                            [ 67%]
GET /api/v2/nature/{id}/ F                                       [ 68%]
GET /api/v2/pal-park-area/ .                                     [ 69%]
GET /api/v2/pal-park-area/{id}/ F                                [ 70%]
GET /api/v2/pokeathlon-stat/ .                                   [ 71%]
GET /api/v2/pokeathlon-stat/{id}/ F                              [ 72%]
GET /api/v2/pokedex/ .                                           [ 73%]
GET /api/v2/pokedex/{id}/ F                                      [ 74%]
GET /api/v2/pokemon-color/ .                                     [ 75%]
GET /api/v2/pokemon-color/{id}/ F                                [ 76%]
GET /api/v2/pokemon-form/ .                                      [ 77%]
GET /api/v2/pokemon-form/{id}/ F                                 [ 78%]
GET /api/v2/pokemon-habitat/ .                                   [ 79%]
GET /api/v2/pokemon-habitat/{id}/ F                              [ 80%]
GET /api/v2/pokemon-shape/ .                                     [ 81%]
GET /api/v2/pokemon-shape/{id}/ F                                [ 82%]
GET /api/v2/pokemon-species/ .                                   [ 83%]
GET /api/v2/pokemon-species/{id}/ F                              [ 84%]
GET /api/v2/pokemon/ .                                           [ 85%]
GET /api/v2/pokemon/{id}/ F                                      [ 86%]
GET /api/v2/pokemon/{pokemon_id}/encounters .                    [ 87%]
GET /api/v2/region/ .                                            [ 88%]
GET /api/v2/region/{id}/ F                                       [ 89%]
GET /api/v2/stat/ .                                              [ 90%]
GET /api/v2/stat/{id}/ F                                         [ 91%]
GET /api/v2/super-contest-effect/ .                              [ 92%]
GET /api/v2/super-contest-effect/{id}/ F                         [ 93%]
GET /api/v2/type/ .                                              [ 94%]
GET /api/v2/type/{id}/ F                                         [ 95%]
GET /api/v2/version-group/ .                                     [ 96%]
GET /api/v2/version-group/{id}/ F                                [ 97%]
GET /api/v2/version/ .                                           [ 98%]
GET /api/v2/version/{id}/ F                                      [100%]

========================== HYPOTHESIS OUTPUT ===========================
Unreliable test timings! On an initial run, this test took 2031.00ms, which exceeded the deadline of 500.00ms, but on a subsequent run it took 0.00 ms, which did not. If you expect this sort of variability in your test timings, consider turning deadlines off for this test by setting deadline=None.
================================ ERRORS ================================
________________________ GET: /api/v2/ability/ _________________________
hypothesis.errors.Flaky: Tests on this endpoint produce unreliable results:
Falsified on the first call but did not on a subsequent one


Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/ability/', params={})    

Or add this option to your command line parameters: --hypothesis-seed=6980176923786970459513622431294276514
Add this option to your command line parameters to see full tracebacks: 
--show-errors-tracebacks
=============================== FAILURES ===============================
______________________ GET: /api/v2/ability/{id}/ ______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/ability/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=36065638911432766098961861105016667283
__________________ GET: /api/v2/berry-firmness/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/berry-firmness/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=198255479257748141303253879973247594764
___________________ GET: /api/v2/berry-flavor/{id}/ ____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/berry-flavor/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=27310714495762177828363260013820305375
_______________________ GET: /api/v2/berry/{id}/ _______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/berry/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=257397810806927694052571800266233443333
__________________ GET: /api/v2/characteristic/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/characteristic/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=327169727593473569170383383986096873701
__________________ GET: /api/v2/contest-effect/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/contest-effect/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=10292670959379542712587387869893090464
___________________ GET: /api/v2/contest-type/{id}/ ____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/contest-type/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=197008436282874345114042040367324400644
_____________________ GET: /api/v2/egg-group/{id}/ _____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/egg-group/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=25521810688947136104003120491581642359
_____________ GET: /api/v2/encounter-condition-value/{id}/ _____________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/encounter-condition-value/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=213272950469938010763941970262912275435
________________ GET: /api/v2/encounter-condition/{id}/ ________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/encounter-condition/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=289288290528227567036260757902891781837
_________________ GET: /api/v2/encounter-method/{id}/ __________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/encounter-method/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=263405438755630871550534797781627168350
__________________ GET: /api/v2/evolution-chain/{id}/ __________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/evolution-chain/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=59929045351140269004019149894917320842
_________________ GET: /api/v2/evolution-trigger/{id}/ _________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/evolution-trigger/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=313244789259654225331246504271547172260
______________________ GET: /api/v2/gender/{id}/ _______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/gender/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=70756860274533001032369984810886142800
____________________ GET: /api/v2/generation/{id}/ _____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/generation/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=88183316215451634029524852110103253858
____________________ GET: /api/v2/growth-rate/{id}/ ____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/growth-rate/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=306520877899852821960519189916586879071
__________________ GET: /api/v2/item-attribute/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/item-attribute/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=291956646461407194060137124873472409574
___________________ GET: /api/v2/item-category/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/item-category/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=188126800687470032426082845613646632818
_________________ GET: /api/v2/item-fling-effect/{id}/ _________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/item-fling-effect/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=35213206090555768031734125367242609415
____________________ GET: /api/v2/item-pocket/{id}/ ____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/item-pocket/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=59459525509443282354017810893034166366
_______________________ GET: /api/v2/item/{id}/ ________________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/item/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=92220129575979183316689747544279703040
_____________________ GET: /api/v2/language/{id}/ ______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/language/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=164501049258943345229838370931447055988
___________________ GET: /api/v2/location-area/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/location-area/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=297866564923272379561713928160682586116
_____________________ GET: /api/v2/location/{id}/ ______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/location/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=67334160020230785303916340066931330621
______________________ GET: /api/v2/machine/{id}/ ______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/machine/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=102093451113067816331841154077593697062
___________________ GET: /api/v2/move-ailment/{id}/ ____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/move-ailment/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=219317445275589649915737057122792277128
_________________ GET: /api/v2/move-battle-style/{id}/ _________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/move-battle-style/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=203321493893034963406852837368492236640
___________________ GET: /api/v2/move-category/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/move-category/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=212399074194549437353569586330877892150
_________________ GET: /api/v2/move-damage-class/{id}/ _________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/move-damage-class/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=88676925993926532898283988873692345957
_________________ GET: /api/v2/move-learn-method/{id}/ _________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/move-learn-method/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=277364466738954223382668121655508925730
____________________ GET: /api/v2/move-target/{id}/ ____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/move-target/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=238542327243210624273567391945292208723
_______________________ GET: /api/v2/move/{id}/ ________________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/move/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=314629099368367961352354539959736960440
______________________ GET: /api/v2/nature/{id}/ _______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/nature/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=113033494493555008217243446452015896850
___________________ GET: /api/v2/pal-park-area/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pal-park-area/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=330722680936628955161659348289497301934
__________________ GET: /api/v2/pokeathlon-stat/{id}/ __________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokeathlon-stat/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=323911144359400446390591434242027292601
______________________ GET: /api/v2/pokedex/{id}/ ______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokedex/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=325341017571450078460608991379070764947
___________________ GET: /api/v2/pokemon-color/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokemon-color/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=286906121886395153446520934473402821555
___________________ GET: /api/v2/pokemon-form/{id}/ ____________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokemon-form/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=326284199074111792555144918612996400681
__________________ GET: /api/v2/pokemon-habitat/{id}/ __________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokemon-habitat/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=163507711774823192941632990675513676719
___________________ GET: /api/v2/pokemon-shape/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokemon-shape/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=14754992503859582237932054508249683567
__________________ GET: /api/v2/pokemon-species/{id}/ __________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokemon-species/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=256821626551212114697965941251010348024
______________________ GET: /api/v2/pokemon/{id}/ ______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/pokemon/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=222477974872853654701293015084165280580
______________________ GET: /api/v2/region/{id}/ _______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/region/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=331381860589695319964544786683154305107
_______________________ GET: /api/v2/stat/{id}/ ________________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/stat/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=183504656952994559480549151433357594555
_______________ GET: /api/v2/super-contest-effect/{id}/ ________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/super-contest-effect/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=311753271111489225920469132151929373458
_______________________ GET: /api/v2/type/{id}/ ________________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/type/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=283251294412995266283215458984753726625
___________________ GET: /api/v2/version-group/{id}/ ___________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/version-group/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=180098098566570520216965592320774189767
______________________ GET: /api/v2/version/{id}/ ______________________
1. Received a response with 5xx status code: 500

Check           : not_a_server_error
Path parameters : {'id': 9223372036854775808}

Run this Python code to reproduce this failure: 

    requests.get('http://localhost:8000/api/v2/version/9223372036854775808/')

Or add this option to your command line parameters: --hypothesis-seed=235432634904926188037234452443101495339
=============================== SUMMARY ================================

not_a_server_error            5679 / 5924 passed          FAILED        

============== 48 passed, 48 failed, 1 errored in 69.11s ===============
```

The error is legit! It is forced by a conversion error, as the integer is too large for SQL.

```bash
(.venv) PS C:\Users\MikeSolomon\devel\test-apis\pokeapi-1> curl.exe http://localhost:8000/api/v2/version-group/9223372036854775808/
OverflowError at /api/v2/version-group/9223372036854775808/
Python int too large to convert to SQLite INTEGER

Request Method: GET
Request URL: http://localhost:8000/api/v2/version-group/9223372036854775808/
Django Version: 2.1.11
Python Executable: C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\Scripts\python.exe
Python Version: 3.7.3
Python Path: ['C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1', 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv\\Scripts\\python37.zip', 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv\\DLLs', 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv\\lib', 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv\\Scripts', 
'c:\\users\\mikesolomon\\appdata\\local\\programs\\python\\python37\\Lib', 'c:\\users\\mikesolomon\\appdata\\local\\programs\\python\\python37\\DLLs', 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv', 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv\\lib\\site-packages']
Server time: Fri, 10 Apr 2020 14:20:22 +0100
Installed Applications:
('django.contrib.auth',
 'django.contrib.contenttypes',
 'django.contrib.sessions',
 'django.contrib.sites',
 'django.contrib.admin',
 'django.contrib.humanize',
 'drf_yasg',
 'corsheaders',
 'rest_framework',
 'cachalot',
 'tastypie',
 'pokemon_v2')
Installed Middleware:
['corsheaders.middleware.CorsMiddleware',
 'django.middleware.common.CommonMiddleware',
 'django.contrib.sessions.middleware.SessionMiddleware',
 'django.middleware.csrf.CsrfViewMiddleware',
 'django.contrib.auth.middleware.AuthenticationMiddleware',
 'django.contrib.messages.middleware.MessageMiddleware',
 'django.middleware.clickjacking.XFrameOptionsMiddleware']


Traceback:

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\utils.py" in execute
  100.             return super().execute(sql, params)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\cachalot\monkey_patch.py" in inner
  124.                 return original(cursor, sql, *args, **kwargs)    

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\utils.py" in execute
  68.         return self._execute_with_wrappers(sql, params, many=False, executor=self._execute)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\utils.py" in _execute_with_wrappers
  77.         return executor(sql, params, many, context)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\utils.py" in _execute
  85.                 return self.cursor.execute(sql, params)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\sqlite3\base.py" in execute
  298.         return Database.Cursor.execute(self, query, params)      

During handling of the above exception (Python int too large to convert 
to SQLite INTEGER), another exception occurred:

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\core\handlers\exception.py" in inner
  34.             response = get_response(request)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\core\handlers\base.py" in _get_response
  126.                 response = self.process_exception_by_middleware(e, request)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\core\handlers\base.py" in _get_response
  124.                 response = wrapped_callback(request, *callback_args, **callback_kwargs)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\views\decorators\csrf.py" in wrapped_view
  54.         return view_func(*args, **kwargs)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\rest_framework\viewsets.py" in view
  116.             return self.dispatch(request, *args, **kwargs)       

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\rest_framework\views.py" in dispatch
  495.             response = self.handle_exception(exc)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\rest_framework\views.py" in handle_exception
  455.             self.raise_uncaught_exception(exc)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\rest_framework\views.py" in dispatch
  492.             response = handler(request, *args, **kwargs)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\rest_framework\mixins.py" in retrieve
  56.         instance = self.get_object()

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\pokemon_v2\api.py" 
in get_object
  47.             resp = get_object_or_404(queryset, pk=lookup)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\shortcuts.py" in get_object_or_404
  93.         return queryset.get(*args, **kwargs)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\models\query.py" in get
  393.         num = len(clone)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\models\query.py" in __len__
  250.         self._fetch_all()

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\models\query.py" in _fetch_all
  1186.             self._result_cache = list(self._iterable_class(self))

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\models\query.py" in __iter__
  54.         results = compiler.execute_sql(chunked_fetch=self.chunked_fetch, chunk_size=self.chunk_size)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\cachalot\monkey_patch.py" in inner
  32.             return original(compiler, *args, **kwargs)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\cachalot\monkey_patch.py" in inner
  86.             cache_key, table_cache_keys)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\cachalot\monkey_patch.py" in _get_result_or_execute_query
  55.     result = execute_query_func()

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\cachalot\monkey_patch.py" in <lambda>
  71.         execute_query_func = lambda: original(compiler, *args, **kwargs)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\models\sql\compiler.py" in execute_sql
  1065.             cursor.execute(sql, params)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\utils.py" in execute
  104.             sql = self.db.ops.last_executed_query(self.cursor, sql, params)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\sqlite3\operations.py" in last_executed_query   
  142.                 params = self._quote_params_for_last_executed_query(params)

File "C:\Users\MikeSolomon\devel\test-apis\pokeapi-1\.venv\lib\site-packages\django\db\backends\sqlite3\operations.py" in _quote_params_for_last_executed_query
  131.             return cursor.execute(sql, params).fetchone()        

Exception Type: OverflowError at /api/v2/version-group/9223372036854775808/
Exception Value: Python int too large to convert to SQLite INTEGER      
Request information:
USER: AnonymousUser

GET: No GET data

POST: No POST data

FILES: No FILES data

COOKIES: No cookie data

META:
ALLUSERSPROFILE = 'C:\\ProgramData'
APPDATA = 'C:\\Users\\MikeSolomon\\AppData\\Roaming'
APPLICATION_INSIGHTS_NO_DIAGNOSTIC_CHANNEL = 'true'
CHOCOLATEYINSTALL = 'C:\\ProgramData\\chocolatey'
CHOCOLATEYLASTPATHUPDATE = '132040339862448713'
CLASSPATH = '.;C:\\Users\\MikeSolomon\\devel\\antlr\\antlr-4.7.2-complete.jar;'
COLORTERM = 'truecolor'
COMMANDER_HOME = 'C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\ToscaCommander'
COMMONPROGRAMFILES = 'C:\\Program Files\\Common Files'
COMMONPROGRAMFILES(X86) = 'C:\\Program Files (x86)\\Common Files'       
COMMONPROGRAMW6432 = 'C:\\Program Files\\Common Files'
COMPUTERNAME = 'DESKTOP-6OGFE70'
COMSPEC = 'C:\\WINDOWS\\system32\\cmd.exe'
CONTENT_LENGTH = ''
CONTENT_TYPE = 'text/plain'
DJANGO_SETTINGS_MODULE = 'config.local'
DRIVERDATA = 'C:\\Windows\\System32\\Drivers\\DriverData'
GATEWAY_INTERFACE = 'CGI/1.1'
GIT_LFS_PATH = 'C:\\Program Files\\Git LFS'
GOPATH = 'C:\\Users\\MikeSolomon\\go'
GOROOT = 'C:\\Go\\'
HOMEDRIVE = 'C:'
HOMEPATH = '\\Users\\MikeSolomon'
HTTP_ACCEPT = '*/*'
HTTP_HOST = 'localhost:8000'
HTTP_USER_AGENT = 'curl/7.55.1'
INTELLIJ IDEA COMMUNITY EDITION = 'C:\\Program Files\\JetBrains\\IntelliJ IDEA Community Edition 2019.1.2\\bin;'
INTEL_DEV_REDIST = 'C:\\Program Files (x86)\\Common Files\\Intel\\Shared Libraries\\'
LANG = 'en_US.UTF-8'
LOCALAPPDATA = 'C:\\Users\\MikeSolomon\\AppData\\Local'
LOGONSERVER = '\\\\DESKTOP-6OGFE70'
MAKEFLAGS = ''
MAKELEVEL = '1'
MAKE_TERMERR = 'CONOUT$'
MAKE_TERMOUT = 'CONOUT$'
MFLAGS = ''
MIC_LD_LIBRARY_PATH = 'C:\\Program Files (x86)\\Common Files\\Intel\\Shared Libraries\\compiler\\lib\\mic'
NUMBER_OF_PROCESSORS = '8'
ONEDRIVE = 'C:\\Users\\MikeSolomon\\OneDrive'
ONEDRIVECONSUMER = 'C:\\Users\\MikeSolomon\\OneDrive'
OPENSSL_CONF = 'C:\\Program Files\\PostgreSQL\\psqlODBC\\etc\\openssl.cnf'
OS = 'Windows_NT'
PATH = 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv/Scripts;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\ToscaCommander;;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\GuptaEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\ToscaCommander;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\DelphiEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\PBEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\VBEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\DotNetHooking;;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\TBox\\\\Resources\\Mobile\\Tools;C:\\Program Files\\Haskell\\bin;C:\\Program Files\\Haskell Platform\\8.6.5\\lib\\extralibs\\bin;C:\\Program Files\\Haskell Platform\\8.6.5\\bin;C:\\Program Files\\ImageMagick-7.0.9-Q16;C:\\Program Files (x86)\\Common Files\\Intel\\Shared Libraries\\redist\\intel64\\compiler;C:\\Program Files (x86)\\Common Files\\Oracle\\Java\\javapath;C:\\WINDOWS\\system32;C:\\WINDOWS;C:\\WINDOWS\\System32\\Wbem;C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\;C:\\WINDOWS\\System32\\OpenSSH\\;C:\\Program Files\\Git\\cmd;C:\\Program Files\\nodejs\\;C:\\Strawberry\\c\\bin;C:\\Strawberry\\perl\\site\\bin;C:\\Strawberry\\perl\\bin;C:\\Program Files\\dotnet\\;C:\\Program Files\\Microsoft SQL Server\\130\\Tools\\Binn\\;C:\\Program Files\\erl10.1\\bin;C:\\Program Files (x86)\\Elixir\\bin;C:\\Users\\MikeSolomon\\.mix\\escripts;C:\\Program Files (x86)\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Program Files\\Intel\\Intel(R) Management Engine Components\\DAL;C:\\Go\\bin;C:\\ProgramData\\chocolatey\\bin;C:\\Program Files\\Git LFS;C:\\Program Files\\CMake\\bin;C:\\Program Files\\Microsoft SQL Server\\Client SDK\\ODBC\\170\\Tools\\Binn\\;C:\\Program Files\\PuTTY\\;C:\\Program Files\\Haskell Platform\\8.6.5\\mingw\\bin;C:\\Program Files\\Wireshark;;C:\\Program Files\\Docker\\Docker\\resources\\bin;C:\\ProgramData\\DockerDesktop\\version-bin;C:\\Users\\MikeSolomon\\AppData\\Roaming\\cabal\\bin;C:\\Users\\MikeSolomon\\AppData\\Roaming\\stack\\local\\bin;C:\\Users\\MikeSolomon\\AppData\\Local\\Programs\\Python\\Python37\\Scripts\\;C:\\Users\\MikeSolomon\\AppData\\Local\\Programs\\Python\\Python37\\;C:\\Users\\MikeSolomon\\AppData\\Local\\Microsoft\\WindowsApps;C:\\Users\\MikeSolomon\\AppData\\Local\\Programs\\Microsoft VS Code\\bin;C:\\Users\\MikeSolomon\\AppData\\Roaming\\npm;C:\\Users\\MikeSolomon\\devel\\ngrok;C:\\Program Files (x86)\\LilyPond\\usr\\bin;C:\\Program Files\\JetBrains\\IntelliJ IDEA Community Edition 
2019.1.2\\bin;C:\\Users\\MikeSolomon\\go\\bin;C:\\Program Files\\heroku\\bin;C:\\Program Files\\JetBrains\\PyCharm Community Edition 2019.2.2\\bin;C:\\Users\\MikeSolomon\\.dotnet\\tools;C:\\Users\\MikeSolomon\\AppData\\Local\\Pandoc\\;C:\\Program Files (x86)\\mitmproxy\\bin'
PATHEXT = '.PY;.SCM;.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC;.CPL'
PATH_INFO = '/api/v2/version-group/9223372036854775808/'
PROCESSOR_ARCHITECTURE = 'AMD64'
PROCESSOR_IDENTIFIER = 'Intel64 Family 6 Model 142 Stepping 10, GenuineIntel'
PROCESSOR_LEVEL = '6'
PROCESSOR_REVISION = '8e0a'
PROGRAMDATA = 'C:\\ProgramData'
PROGRAMFILES = 'C:\\Program Files'
PROGRAMFILES(X86) = 'C:\\Program Files (x86)'
PROGRAMW6432 = 'C:\\Program Files'
PROMPT = '$P$G'
PSMODULEPATH = 'C:\\Users\\MikeSolomon\\Documents\\WindowsPowerShell\\Modules;C:\\Program Files\\WindowsPowerShell\\Modules;C:\\WINDOWS\\system32\\WindowsPowerShell\\v1.0\\Modules'
PUBLIC = 'C:\\Users\\Public'
PYCHARM COMMUNITY EDITION = 'C:\\Program Files\\JetBrains\\PyCharm Community Edition 2019.2.2\\bin;'
QUERY_STRING = ''
REMOTE_ADDR = '127.0.0.1'
REMOTE_HOST = ''
REQUEST_METHOD = 'GET'
RUN_MAIN = 'true'
SCRIPT_NAME = ''
SERVER_NAME = 'kubernetes.docker.internal'
SERVER_PORT = '8000'
SERVER_PROTOCOL = 'HTTP/1.1'
SERVER_SOFTWARE = 'WSGIServer/0.2'
STACK_ROOT = 'C:\\sr'
SYSTEMDRIVE = 'C:'
SYSTEMROOT = 'C:\\WINDOWS'
TBOX_HOME = 'C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\TBox\\'
TEMP = 'C:\\Users\\MikeSolomon\\AppData\\Local\\Temp'
TERM_PROGRAM = 'vscode'
TERM_PROGRAM_VERSION = '1.43.2'
TESSDATA_PREFIX = 'C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\ocr'
TMP = 'C:\\Users\\MikeSolomon\\AppData\\Local\\Temp'
TRICENTIS_ALLUSERS_APPDATA = 'C:\\ProgramData\\TRICENTIS\\Tosca Testsuite\\7.0.0'
TRICENTIS_DEX_AGENT_HOME = 'C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\DistributedExecution\\'
TRICENTIS_HOME = 'C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic'
TRICENTIS_LICENSING_HOME = 'C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Licensing'
TRICENTIS_PROJECTS = 'C:\\Tosca_Projects\\'
TRICENTIS_SEARCH = 'C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\ToscaCommander;;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\GuptaEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\ToscaCommander;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\DelphiEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\PBEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\VBEngine;C:\\Program Files (x86)\\TRICENTIS\\Tosca Testsuite\\Classic\\dll\\DotNetHooking;'
USERDOMAIN = 'AzureAD'
USERDOMAIN_ROAMINGPROFILE = 'AzureAD'
USERNAME = 'MikeSolomon'
USERPROFILE = 'C:\\Users\\MikeSolomon'
VIRTUAL_ENV = 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\.venv'
WINDIR = 'C:\\WINDOWS'
WSLENV = 'WT_SESSION:'
WT_SESSION = 'ee886ff2-e755-4e22-be82-245a505f34b0'
wsgi.errors = <_io.TextIOWrapper name='<stderr>' mode='w' encoding='utf-8'>
wsgi.file_wrapper = ''
wsgi.input = <django.core.handlers.wsgi.LimitedStream object at 0x00000279493E3160>
wsgi.multiprocess = False
wsgi.multithread = True
wsgi.run_once = False
wsgi.url_scheme = 'http'
wsgi.version = '(1, 0)'

Settings:
Using settings module config.local
ABSOLUTE_URL_OVERRIDES = {}
ADMINS = "(('Paul Hallett', 'paulandrewhallett@gmail.com'),)"
ALLOWED_HOSTS = ['.pokeapi.co', 'localhost', '127.0.0.1']
API_LIMIT_PER_PAGE = '********************'
APPEND_SLASH = True
AUTHENTICATION_BACKENDS = ['django.contrib.auth.backends.ModelBackend'] 
AUTH_PASSWORD_VALIDATORS = '********************'
AUTH_USER_MODEL = 'auth.User'
BASE_URL = 'http://pokeapi.co'
CACHES = {'default': {'BACKEND': 'django.core.cache.backends.dummy.DummyCache'}}
CACHE_MIDDLEWARE_ALIAS = 'default'
CACHE_MIDDLEWARE_KEY_PREFIX = '********************'
CACHE_MIDDLEWARE_SECONDS = 600
CORS_ALLOW_METHODS = 'GET'
CORS_ORIGIN_ALLOW_ALL = True
CORS_URLS_REGEX = '^/api/.*$'
CSRF_COOKIE_AGE = 31449600
CSRF_COOKIE_DOMAIN = None
CSRF_COOKIE_HTTPONLY = False
CSRF_COOKIE_NAME = 'csrftoken'
CSRF_COOKIE_PATH = '/'
CSRF_COOKIE_SAMESITE = 'Lax'
CSRF_COOKIE_SECURE = False
CSRF_FAILURE_VIEW = 'django.views.csrf.csrf_failure'
CSRF_HEADER_NAME = 'HTTP_X_CSRFTOKEN'
CSRF_TRUSTED_ORIGINS = []
CSRF_USE_SESSIONS = False
CUSTOM_APPS = "('tastypie', 'pokemon_v2')"
DATABASES = {'default': {'ENGINE': 'django.db.backends.sqlite3', 'NAME': 'C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1\\db.sqlite3', 'ATOMIC_REQUESTS': False, 'AUTOCOMMIT': True, 'CONN_MAX_AGE': 0, 'OPTIONS': 
{}, 'TIME_ZONE': None, 'USER': '', 'PASSWORD': '********************', 'HOST': '', 'PORT': '', 'TEST': {'CHARSET': None, 'COLLATION': None, 'NAME': None, 'MIRROR': None}}}
DATABASE_ROUTERS = []
DATA_UPLOAD_MAX_MEMORY_SIZE = 2621440
DATA_UPLOAD_MAX_NUMBER_FIELDS = 1000
DATETIME_FORMAT = 'N j, Y, P'
DATETIME_INPUT_FORMATS = ['%Y-%m-%d %H:%M:%S', '%Y-%m-%d %H:%M:%S.%f', '%Y-%m-%d %H:%M', '%Y-%m-%d', '%m/%d/%Y %H:%M:%S', '%m/%d/%Y %H:%M:%S.%f', '%m/%d/%Y %H:%M', '%m/%d/%Y', '%m/%d/%y %H:%M:%S', '%m/%d/%y %H:%M:%S.%f', '%m/%d/%y %H:%M', '%m/%d/%y']
DATE_FORMAT = 'N j, Y'
DATE_INPUT_FORMATS = ['%Y-%m-%d', '%m/%d/%Y', '%m/%d/%y', '%b %d %Y', '%b %d, %Y', '%d %b %Y', '%d %b, %Y', '%B %d %Y', '%B %d, %Y', '%d %B %Y', '%d %B, %Y']
DEBUG = True
DEBUG_PROPAGATE_EXCEPTIONS = False
DECIMAL_SEPARATOR = '.'
DEFAULT_CHARSET = 'utf-8'
DEFAULT_CONTENT_TYPE = 'text/html'
DEFAULT_EXCEPTION_REPORTER_FILTER = 'django.views.debug.SafeExceptionReporterFilter'
DEFAULT_FILE_STORAGE = 'django.core.files.storage.FileSystemStorage'    
DEFAULT_FROM_EMAIL = 'webmaster@localhost'
DEFAULT_INDEX_TABLESPACE = ''
DEFAULT_TABLESPACE = ''
DISALLOWED_USER_AGENTS = []
EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'        
EMAIL_HOST = 'localhost'
EMAIL_HOST_PASSWORD = '********************'
EMAIL_HOST_USER = ''
EMAIL_PORT = 25
EMAIL_SSL_CERTFILE = None
EMAIL_SSL_KEYFILE = '********************'
EMAIL_SUBJECT_PREFIX = '[Django] '
EMAIL_TIMEOUT = None
EMAIL_USE_LOCALTIME = False
EMAIL_USE_SSL = False
EMAIL_USE_TLS = False
FILE_CHARSET = 'utf-8'
FILE_UPLOAD_DIRECTORY_PERMISSIONS = None
FILE_UPLOAD_HANDLERS = ['django.core.files.uploadhandler.MemoryFileUploadHandler', 'django.core.files.uploadhandler.TemporaryFileUploadHandler']
FILE_UPLOAD_MAX_MEMORY_SIZE = 2621440
FILE_UPLOAD_PERMISSIONS = None
FILE_UPLOAD_TEMP_DIR = None
FIRST_DAY_OF_WEEK = 0
FIXTURE_DIRS = []
FORCE_SCRIPT_NAME = None
FORMAT_MODULE_PATH = None
FORM_RENDERER = 'django.forms.renderers.DjangoTemplates'
IGNORABLE_404_URLS = []
INSTALLED_APPS = "('django.contrib.auth', 'django.contrib.contenttypes', 'django.contrib.sessions', 'django.contrib.sites', 'django.contrib.admin', 'django.contrib.humanize', 'drf_yasg', 'corsheaders', 'rest_framework', 'cachalot', 'tastypie', 'pokemon_v2')"
INTERNAL_IPS = []
LANGUAGES = [('af', 'Afrikaans'), ('ar', 'Arabic'), ('ast', 'Asturian'), ('az', 'Azerbaijani'), ('bg', 'Bulgarian'), ('be', 'Belarusian'), ('bn', 'Bengali'), ('br', 'Breton'), ('bs', 'Bosnian'), ('ca', 'Catalan'), ('cs', 'Czech'), ('cy', 'Welsh'), ('da', 'Danish'), ('de', 'German'), ('dsb', 'Lower Sorbian'), ('el', 'Greek'), ('en', 'English'), ('en-au', 'Australian English'), ('en-gb', 'British English'), ('eo', 'Esperanto'), ('es', 'Spanish'), ('es-ar', 'Argentinian Spanish'), ('es-co', 'Colombian 
Spanish'), ('es-mx', 'Mexican Spanish'), ('es-ni', 'Nicaraguan Spanish'), ('es-ve', 'Venezuelan Spanish'), ('et', 'Estonian'), ('eu', 'Basque'), ('fa', 'Persian'), ('fi', 'Finnish'), ('fr', 'French'), ('fy', 'Frisian'), ('ga', 'Irish'), ('gd', 'Scottish Gaelic'), ('gl', 'Galician'), ('he', 'Hebrew'), ('hi', 'Hindi'), ('hr', 'Croatian'), ('hsb', 'Upper Sorbian'), ('hu', 'Hungarian'), ('ia', 'Interlingua'), ('id', 'Indonesian'), ('io', 'Ido'), ('is', 'Icelandic'), ('it', 'Italian'), ('ja', 'Japanese'), ('ka', 'Georgian'), ('kab', 'Kabyle'), ('kk', 'Kazakh'), ('km', 'Khmer'), ('kn', 'Kannada'), ('ko', 'Korean'), ('lb', 'Luxembourgish'), ('lt', 'Lithuanian'), ('lv', 'Latvian'), ('mk', 'Macedonian'), ('ml', 'Malayalam'), ('mn', 'Mongolian'), ('mr', 'Marathi'), ('my', 'Burmese'), ('nb', 
'Norwegian Bokm├Ñl'), ('ne', 'Nepali'), ('nl', 'Dutch'), ('nn', 'Norwegian Nynorsk'), ('os', 'Ossetic'), ('pa', 'Punjabi'), ('pl', 'Polish'), ('pt', 'Portuguese'), ('pt-br', 'Brazilian Portuguese'), ('ro', 'Romanian'), ('ru', 'Russian'), ('sk', 'Slovak'), ('sl', 'Slovenian'), ('sq', 'Albanian'), ('sr', 'Serbian'), ('sr-latn', 'Serbian Latin'), ('sv', 'Swedish'), ('sw', 'Swahili'), ('ta', 'Tamil'), ('te', 'Telugu'), ('th', 'Thai'), ('tr', 'Turkish'), ('tt', 'Tatar'), ('udm', 'Udmurt'), ('uk', 'Ukrainian'), ('ur', 'Urdu'), ('vi', 'Vietnamese'), ('zh-hans', 'Simplified Chinese'), ('zh-hant', 'Traditional Chinese')]
LANGUAGES_BIDI = ['he', 'ar', 'fa', 'ur']
LANGUAGE_CODE = 'en-gb'
LANGUAGE_COOKIE_AGE = None
LANGUAGE_COOKIE_DOMAIN = None
LANGUAGE_COOKIE_NAME = 'django_language'
LANGUAGE_COOKIE_PATH = '/'
LOCALE_PATHS = []
LOGGING = {}
LOGGING_CONFIG = 'logging.config.dictConfig'
LOGIN_REDIRECT_URL = '/accounts/profile/'
LOGIN_URL = '/accounts/login/'
LOGOUT_REDIRECT_URL = None
MANAGERS = "(('Paul Hallett', 'paulandrewhallett@gmail.com'),)"
MEDIA_ROOT = ''
MEDIA_URL = ''
MESSAGE_STORAGE = 'django.contrib.messages.storage.fallback.FallbackStorage'
MIDDLEWARE = ['corsheaders.middleware.CorsMiddleware', 'django.middleware.common.CommonMiddleware', 'django.contrib.sessions.middleware.SessionMiddleware', 'django.middleware.csrf.CsrfViewMiddleware', 'django.contrib.auth.middleware.AuthenticationMiddleware', 'django.contrib.messages.middleware.MessageMiddleware', 'django.middleware.clickjacking.XFrameOptionsMiddleware']
MIGRATION_MODULES = {}
MONTH_DAY_FORMAT = 'F j'
NUMBER_GROUPING = 0
PASSWORD_HASHERS = '********************'
PASSWORD_RESET_TIMEOUT_DAYS = '********************'
PREPEND_WWW = False
PROJECT_ROOT = Path('C:\\Users\\MikeSolomon\\devel\\test-apis\\pokeapi-1')
REST_FRAMEWORK = {'DEFAULT_RENDERER_CLASSES': ('drf_ujson.renderers.UJSONRenderer',), 'DEFAULT_PARSER_CLASSES': ('drf_ujson.renderers.UJSONRenderer',), 'DEFAULT_PAGINATION_CLASS': 'rest_framework.pagination.LimitOffsetPagination', 'PAGE_SIZE': 20, 'PAGINATE_BY': 20}
ROOT_URLCONF = 'config.urls'
SECRET_KEY = '********************'
SECURE_BROWSER_XSS_FILTER = False
SECURE_CONTENT_TYPE_NOSNIFF = False
SECURE_HSTS_INCLUDE_SUBDOMAINS = False
SECURE_HSTS_PRELOAD = False
SECURE_HSTS_SECONDS = 0
SECURE_PROXY_SSL_HEADER = None
SECURE_REDIRECT_EXEMPT = []
SECURE_SSL_HOST = None
SECURE_SSL_REDIRECT = False
SERVER_EMAIL = 'root@localhost'
SESSION_CACHE_ALIAS = 'default'
SESSION_COOKIE_AGE = 1209600
SESSION_COOKIE_DOMAIN = None
SESSION_COOKIE_HTTPONLY = True
SESSION_COOKIE_NAME = 'sessionid'
SESSION_COOKIE_PATH = '/'
SESSION_COOKIE_SAMESITE = 'Lax'
SESSION_COOKIE_SECURE = False
SESSION_ENGINE = 'django.contrib.sessions.backends.db'
SESSION_EXPIRE_AT_BROWSER_CLOSE = False
SESSION_FILE_PATH = None
SESSION_SAVE_EVERY_REQUEST = False
SESSION_SERIALIZER = 'django.contrib.sessions.serializers.JSONSerializer'
SETTINGS_MODULE = 'config.local'
SHORT_DATETIME_FORMAT = 'm/d/Y P'
SHORT_DATE_FORMAT = 'm/d/Y'
SIGNING_BACKEND = 'django.core.signing.TimestampSigner'
SILENCED_SYSTEM_CHECKS = []
SITE_ID = 1
STATICFILES_DIRS = []
STATICFILES_FINDERS = ['django.contrib.staticfiles.finders.FileSystemFinder', 'django.contrib.staticfiles.finders.AppDirectoriesFinder']        
STATICFILES_STORAGE = 'django.contrib.staticfiles.storage.StaticFilesStorage'
STATIC_ROOT = None
STATIC_URL = None
TASTYPIE_DEFAULT_FORMATS = ['json']
TASTYPIE_FULL_DEBUG = True
TEMPLATES = []
TEMPLATE_DEBUG = False
TEST_NON_SERIALIZED_APPS = []
TEST_RUNNER = 'django.test.runner.DiscoverRunner'
THOUSAND_SEPARATOR = ','
TIME_FORMAT = 'P'
TIME_INPUT_FORMATS = ['%H:%M:%S', '%H:%M:%S.%f', '%H:%M']
TIME_ZONE = 'Europe/London'
USE_I18N = True
USE_L10N = True
USE_THOUSAND_SEPARATOR = False
USE_TZ = True
USE_X_FORWARDED_HOST = False
USE_X_FORWARDED_PORT = False
WSGI_APPLICATION = 'config.wsgi.application'
X_FRAME_OPTIONS = 'SAMEORIGIN'
YEAR_MONTH_FORMAT = 'F Y'


You're seeing this error because you have DEBUG = True in your
Django settings file. Change that to False, and Django will
display a standard page generated by the handler for this status code.  
```

## Mocker

None needed.