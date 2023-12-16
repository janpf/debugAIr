# debuggAir - Your AI-Powered Debugging Companion 🤖

Tired of debugging your code?
Let an AI do it for you!
Just run `python -m debuggAir <your_script.py>` and let debuggAir do the rest!

The following, definitely not cherry-picked example took just 5 seconds to run! Can you find the fix faster than ChatGPT? 🤓

``` py
(venv) janpf@mbp ~/p/S/s/evaluation (main)> python -m debuggAir broken_script.py
2023-12-15 01:08:49.770 | INFO     | __main__:<module>:69 -
Traceback (most recent call last): File ".../Python.framework/Versions/3.10/lib/python3.10/pdb.py", line 1723, in main
    pdb._runscript(mainpyfile)
  File ".../Python.framework/Versions/3.10/lib/python3.10/pdb.py", line 1583, in _runscript
    self.run(statement)
  File ".../Python.framework/Versions/3.10/lib/python3.10/bdb.py", line 598, in run
    exec(cmd, globals, locals)
  File "<string>", line 1, in <module>
  File "/Users/janpf/.../src/evaluation/tester.py", line 48, in <module>
    *[eval_results[c] for c in columns if "_" in c],
  File "/Users/janpf/.../src/evaluation/tester.py", line 48, in <listcomp>
    *[eval_results[c] for c in columns if "_" in c],
KeyError: 'predict_overall_acc'
Uncaught exception. Entering post mortem debugging
Running 'cont' or 'step' will restart the program
> /Users/janpf/.../src/evaluation/tester.py(48)<listcomp>()
-> *[eval_results[c] for c in columns if "_" in c],
(Pdb) w
main()
-> pdb._runscript(mainpyfile)
  .../Python.framework/Versions/3.10/lib/python3.10/pdb.py(1583)_runscript()
-> self.run(statement)
  .../Python.framework/Versions/3.10/lib/python3.10/bdb.py(598)run()
-> exec(cmd, globals, locals)
  <string>(1)<module>()
  /Users/janpf/.../src/evaluation/tester.py(48)<module>()
-> *[eval_results[c] for c in columns if "_" in c],
> /Users/janpf/.../src/evaluation/tester.py(48)<listcomp>()
-> *[eval_results[c] for c in columns if "_" in c],
(Pdb) l
 43                                      [
 44                                     cfg["model"]["model_name"],
 45                                     cfg["task"]["task_name"],
 46                                     cfg["seed"],
 47                                     f"{day.name}/{run.name}",
 48  ->                                 *[eval_results[c] for c in columns if "_" in c],
 49                                 ]
 50                             ],
 51                             columns=columns,
 52                         ),
 53                     ]
(Pdb) p columns, eval_results
(['model', 'task', 'seed', 'source', 'predict_overall_f1', 'predict_overall_acc', 'predict_loss'], {'pred_samples': 977, 'predict_ART_f1': 0.0, 'predict_ART_number': 210, 'predict_ART_precision': 0.0, 'predict_ART_recall': 0.0, 'predict_CONJ_f1': 0.0, 'predict_CONJ_number': 747, 'predict_CONJ_precision': 0.0, 'predict_CONJ_recall': 0.0, 'predict_DJ_f1': 0.0, 'predict_DJ_number': 989, 'predict_DJ_precision': 0.0, 'predict_DJ_recall': 0.0, 'predict_DP_f1': 0.0, 'predict_DP_number': 1594, 'predict_DP_precision': 0.0, 'predict_DP_recall': 0.0, 'predict_DV_f1': 0.0, 'predict_DV_number': 1060, 'predict_DV_precision': 0.0, 'predict_DV_recall': 0.0, 'predict_ERB_f1': 0.0, 'predict_ERB_number': 1304, 'predict_ERB_precision': 0.0, 'predict_ERB_recall': 0.0, 'predict_ET_f1': 0.0, 'predict_ET_number': 1881, 'predict_ET_precision': 0.0, 'predict_ET_recall': 0.0, 'predict_NTJ_f1': 0.0, 'predict_NTJ_number': 4, 'predict_NTJ_precision': 0.0, 'predict_NTJ_recall': 0.0, 'predict_OUN_f1': 0.0, 'predict_OUN_number': 3047, 'predict_OUN_precision': 0.0, 'predict_OUN_recall': 0.0, 'predict_RON_f1': 0.0, 'predict_RON_number': 962, 'predict_RON_precision': 0.0, 'predict_RON_recall': 0.0, 'predict_ROPN_f1': 0.0, 'predict_ROPN_number': 836, 'predict_ROPN_precision': 0.0, 'predict_ROPN_recall': 0.0, 'predict_UM_f1': 0.0, 'predict_UM_number': 249, 'predict_UM_precision': 0.0, 'predict_UM_recall': 0.0, 'predict_UNCT_f1': 0.0, 'predict_UNCT_number': 2183, 'predict_UNCT_precision': 0.0, 'predict_UNCT_recall': 0.0, 'predict_UX_f1': 0.0, 'predict_UX_number': 676, 'predict_UX_precision': 0.0, 'predict_UX_recall': 0.0, 'predict_YM_f1': 0.0, 'predict_YM_number': 5, 'predict_YM_precision': 0.0, 'predict_YM_recall': 0.0, 'predict___f1': 0.0, 'predict___number': 15, 'predict___precision': 0.0, 'predict___recall': 0.0, 'predict_loss': nan, 'predict_overall_accuracy': 0.09156062600555799, 'predict_overall_f1': 0.0, 'predict_overall_precision': 0.0, 'predict_overall_recall': 0.0, 'predict_runtime': 7.2699, 'predict_samples_per_second': 134.389, 'predict_steps_per_second': 16.919})
(Pdb) p eval_results
{'pred_samples': 977, 'predict_ART_f1': 0.0, 'predict_ART_number': 210, 'predict_ART_precision': 0.0, 'predict_ART_recall': 0.0, 'predict_CONJ_f1': 0.0, 'predict_CONJ_number': 747, 'predict_CONJ_precision': 0.0, 'predict_CONJ_recall': 0.0, 'predict_DJ_f1': 0.0, 'predict_DJ_number': 989, 'predict_DJ_precision': 0.0, 'predict_DJ_recall': 0.0, 'predict_DP_f1': 0.0, 'predict_DP_number': 1594, 'predict_DP_precision': 0.0, 'predict_DP_recall': 0.0, 'predict_DV_f1': 0.0, 'predict_DV_number': 1060, 'predict_DV_precision': 0.0, 'predict_DV_recall': 0.0, 'predict_ERB_f1': 0.0, 'predict_ERB_number': 1304, 'predict_ERB_precision': 0.0, 'predict_ERB_recall': 0.0, 'predict_ET_f1': 0.0, 'predict_ET_number': 1881, 'predict_ET_precision': 0.0, 'predict_ET_recall': 0.0, 'predict_NTJ_f1': 0.0, 'predict_NTJ_number': 4, 'predict_NTJ_precision': 0.0, 'predict_NTJ_recall': 0.0, 'predict_OUN_f1': 0.0, 'predict_OUN_number': 3047, 'predict_OUN_precision': 0.0, 'predict_OUN_recall': 0.0, 'predict_RON_f1': 0.0, 'predict_RON_number': 962, 'predict_RON_precision': 0.0, 'predict_RON_recall': 0.0, 'predict_ROPN_f1': 0.0, 'predict_ROPN_number': 836, 'predict_ROPN_precision': 0.0, 'predict_ROPN_recall': 0.0, 'predict_UM_f1': 0.0, 'predict_UM_number': 249, 'predict_UM_precision': 0.0, 'predict_UM_recall': 0.0, 'predict_UNCT_f1': 0.0, 'predict_UNCT_number': 2183, 'predict_UNCT_precision': 0.0, 'predict_UNCT_recall': 0.0, 'predict_UX_f1': 0.0, 'predict_UX_number': 676, 'predict_UX_precision': 0.0, 'predict_UX_recall': 0.0, 'predict_YM_f1': 0.0, 'predict_YM_number': 5, 'predict_YM_precision': 0.0, 'predict_YM_recall': 0.0, 'predict___f1': 0.0, 'predict___number': 15, 'predict___precision': 0.0, 'predict___recall': 0.0, 'predict_loss': nan, 'predict_overall_accuracy': 0.09156062600555799, 'predict_overall_f1': 0.0, 'predict_overall_precision': 0.0, 'predict_overall_recall': 0.0, 'predict_runtime': 7.2699, 'predict_samples_per_second': 134.389, 'predict_steps_per_second': 16.919}
(Pdb) q
Post mortem debugger finished. The /Users/janpf/.../src/evaluation/tester.py will be restarted
> /Users/janpf/.../src/evaluation/tester.py(1)<module>()
-> import json
(Pdb)

!solution
The issue is that in the eval_results dictionary, there is no key called 'predict_overall_acc', but there is a key named 'predict_overall_accuracy'. To fix this issue, you need to change 'predict_overall_acc' to 'predict_overall_accuracy'.
2023-12-15 01:08:54.602 | SUCCESS  | __main__:<module>:86 - Solution found
```

It now also works for java!

``` java
(venv) janpf@whackintosh ~/p/d/java_test (master)> python3 ../jebuggAIr.py IAmBroken
2023-12-17 00:25:08.208 | INFO     | __main__:<module>:66 - Initializing jdb ...
> run IAmBroken
Set uncaught java.lang.Throwable
Set deferred uncaught java.lang.Throwable
>
VM Started: Fill that Pokedex! Got to catch'em all!

Exception occurred: IAmBroken$Pikachu (uncaught)"thread=main", IAmBroken.main(), line=24 bci=142
24                      throw new Pikachu("Donnerblitz");

main[1] list
20                          System.out.println("Cleaned up!");
21              }
22              catch (RuntimeException e) {
23                      System.out.println("Fill that Pokedex! Got to catch'em all!");
24 =>                   throw new Pikachu("Donnerblitz");
25              }
26      }
27
28      static class Pikachu extends RuntimeException {
29
main[1] list 20, 30
16                                  if (entry.getValue().equals("Ohrangschensaft")) {
17                                      map.remove(entry.getKey());
18                              }
19                      }
20                      System.out.println("Cleaned up!");
21              }
22              catch (RuntimeException e) {
23                      System.out.println("Fill that Pokedex! Got to catch'em all!");
24 =>                   throw new Pikachu("Donnerblitz");
25              }
main[1] print e.getMessage()
e.getMessage() = null
main[1] print map.entrySet()
com.sun.tools.example.debug.expr.ParseException: Name unknown: map.entrySet
map.entrySet() = null
main[1]

!solution

The issue is that an exception is being thrown when trying to remove an entry from a map during iteration. This causes a ConcurrentModificationException, which is a RuntimeException, to be thrown. The solution is to use an iterator to remove the entry instead of trying to remove it directly.
2023-12-17 00:25:12.155 | SUCCESS  | __main__:<module>:83 - Solution found
```

Absolutely no warranty, use at your own risk.
