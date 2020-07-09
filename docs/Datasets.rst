.. image:: images/logo.png

-------------------------------------

Datasets
''''''''

There are a few datasets that have been included with reliability that users may find useful for testing and experimenting. While this list is currently small, expect it to increase significantly over time. Within ``reliability.Datasets`` the following datasets are available:

**Standard datasets**

- automotive - 10 failures, 21 right censored. It is used in `this example <https://reliability.readthedocs.io/en/latest/Kaplan-Meier%20estimate%20of%20reliability.html>`_
- defective_sample - 1350 failures, 12296 right censored. It exhibits the behavior of a defective sample (also known as Limited failure population or Defective subpopulation).
- electronics - 10 failures, 4072 right censored. It is used in `this example <https://reliability.readthedocs.io/en/latest/Fitting%20a%20specific%20distribution%20to%20data.html#using-fit-weibull-2p-grouped-for-large-data-sets>`_.

**ALT Datasets**

- ALT_temperature - conducted at 3 temperatures. 35 failures, 102 right censored. For example usage of many of the ALT Datasets see the `examples here <https://reliability.readthedocs.io/en/latest/Fitting%20a%20model%20to%20ALT%20data.html>`_.
- ALT_temperature2 - conducted at 4 temperatures. 40 failures, 20 right censored.
- ALT_temperature3 - conducted at 3 temperatures. 30 failures, 0 right censored.
- ALT_load - conducted at 3 loads. 20 failures, 0 censored.
- ALT_load2 - conducted at 3 loads. 13 failures, 5 right censored.
- ALT_temperature_voltage - conducted at 2 different temperatures and 2 different voltages. 12 failures, 0 right censored.
- ALT_temperature_voltage2 - conducted at 3 different temperatures and 2 different voltages. 18 failures, 8 right censored.
- ALT_temperature_humidity - conducted at 2 different temperatures and 2 different humidities. 12 failures, 0 right censored.

All datasets are functions which create objects and every dataset object has several values. For most datasets, these are:

- info - a dataframe of statistics about the dataset
- failures - a list of the failure data
- right_censored - a list of the right_censored data
- right_censored_stress - a list of the right_censored stresses (ALT datasets only)
- some data set specific variations on the above such as failure_stress_humidity, right_censored_stress_voltage, failure_stress_temp, etc.

If you would like more information on a dataset, you can type the name of the dataset in the help function (after importing it).

.. code:: python

    from reliability.Datasets import automotive
    print(help(automotive))

If you would like the statistics about a dataset you can access the info dataframe as shown below.

.. code:: python

    from reliability.Datasets import defective_sample
    print(defective_sample().info)

    '''
                Stat             Value
                Name  defective_sample
        Total Values             13645
            Failures      1350 (9.89%)
      Right Censored    12295 (90.11%)
    '''

The following example shows how to import a dataset and use it. Note that we must use () before accessing the failures and right_censored values.

.. code:: python

    from reliability.Datasets import automotive
    from reliability.Fitters import Fit_Weibull_2P
    Fit_Weibull_2P(failures=automotive().failures,right_censored=automotive().right_censored,show_probability_plot=False)
    
    '''
    Results from Fit_Weibull_2P (95% CI):
               Point Estimate  Standard Error      Lower CI       Upper CI
    Parameter                                                             
    Alpha       140882.303527    49299.609699  70956.382925  279718.647273
    Beta             1.132769        0.301468      0.672370       1.908422
    Log-Likelihood: -128.98350896528038
    '''

If you have an interesting dataset, please email me (m.reid854@gmail.com) and I may include it in this database.
