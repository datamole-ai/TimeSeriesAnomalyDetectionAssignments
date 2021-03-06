This repository acts as a base for Datamole's time series anomaly detection assignments.

# Requirements

- Poetry environment file `pyproject.toml` specifies python packages version requirements. In case you decide to use
Python package listed there, the used version must conform to it. Use [poetry](https://python-poetry.org/) and 
base your environment on the provided `pyproject.toml`. There are also extra dependencies specified in `pyproject.toml` (e.g. tensorflow). 
If you decide to use one of these dependencies, make sure that your version conforms to it.

- File `time_series_anomaly_detection/abstractions.py` contains Python module with abstract class `TimeSeriesAnomalyDetector`. Your
anomaly detector must implement this class. Make sure that the abstract methods are implemented according to their documentation.

- File `time_series_anomaly_detection/detector.py` contains Python module with `TemplateDetector` which you can use as base for your
anomaly detector. As you can see the detector takes `id_columns` parameter in its constructor. Your detector should also take this
parameter as it's necessary to fulfill requirements for the functionality of anomaly detector.

- File `tests/test_detector.py` contains [pytest](https://docs.pytest.org/en/stable/) module with simple tests that your detector must pass. 
Make sure that `DETECTOR_CLASS` points to your detector. In case your detector contains additional required parameters (in its constructor), 
modify existing tests so that these parameters are filled. Adding of additional unit tests is welcome but do not change predefined unit tests 
except for the mentioned exceptions.

- The anomaly detector should be able to handle numerical data with missing values (nan values). In case the paper introducing the detector
does not mention it and there is not a clear solution you can relax on it. For example in case the detector is working with certain window size, 
ignoring (window size - 1) samples after sample with a missing value is a possible solution (nan anomaly score should be returned for each ignored sample).

- The anomaly detector must be able to handle multiple time series which are identified by the ID columns whose names are
provided in the constructor argument `id_columns`. These columns should only be used to separate individual time series 
(not as feature columns). In case the paper introducing the detector does not mention training on multiple time series, try to come up with
a reasonable solution. If there is not a clear reasonable solution you can relax on it.

- Your solution must be in your github repository. You should develop your solution in a non-master branch
and the pull request to master branch should be used as a place for our review.

- Each function and class must be documented using [numpy style docstring](https://numpydoc.readthedocs.io/en/latest/format.html).

# How to start

1. Fork this repository. Create a new branch for the solution.

2. Install [poetry](https://python-poetry.org/) and read its documentation.

3. Install poetry environment by running `poetry install` inside the project's folder.

4. Rename `TemplateDetector` in `time_series_anomaly_detection/detector` to the name of your anomaly detector and start implementing 
it (the documentation of `predict_anomaly_scores` and `fit` is inherited from `TimeSeriesAnomalyDetector` and can be found in 
`time_series_anomaly_detection/abstractions.py`.

5. Make sure that your detector passes all tests in `tests/test_detector.py` by running `poetry run python -m pytest tests`. 
First make sure that in the beginning of `tests/test_detector.py` constant DETECTOR_CLASS points to your anomaly detector 
and not to `TemplateDetector` (in case you renamed it). In case your detector contains additional required parameters (in its constructor), 
modify tests so that these parameters are filled.

6. Create pull request of the solution branch to the master branch.
