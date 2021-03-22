This repository acts as a base for Datamole's time series anomaly detection assignments.

# Requirements

- Poetry environment file `pyproject.toml` specifies python packages version requirements. In case you decide to use
Python package listed there, the used version must conform to it. It is strongly recommended to use [poetry](https://python-poetry.org/) and 
base your environment on the provided `pyproject.toml`.

- File `time_series_anomaly_detection/abstractions.py` contains Python module with abstract class `TimeSeriesAnomalyDetector`. Your
anomaly detector must implement this class. Make sure that the abstract methods are implemented according to their documentation.

- File `time_series_anomaly_detection/detector` contains Python module with `TemplateDetector` which you can use as base for your
anomaly detector. As you can see the detector takes `id_columns` parameter in its constructor. Your detector should also take this
parameter as it's necessary to fulfill requirements for the functionality of anomaly detector.

- File `tests/test_detector.py` contains [pytest](https://docs.pytest.org/en/stable/) module with simple tests that your detector must pass. 
Make sure that `DETECTOR_CLASS` points to your detector.

- The anomaly detector must be able to handle numerical data with missing values (nan values).

- The anomaly detector must be able to handle multiple time series which are identified by the ID columns whose names are
provided in the constructor argument `id_columns`. These columns should only be used to separate individual time series 
(not as feature columns).

- Your solution must be on a github repository to which you must give us access. You should develop your solution in a non-master branch
and the pull request to master branch should be used as a place for our review.
