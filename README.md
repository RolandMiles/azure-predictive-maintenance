# [Microsoft Azure Predictive Maintenance](https://www.kaggle.com/datasets/arnabbiswas1/microsoft-azure-predictive-maintenance)

## Task Description
Unexpected equipment failures cause unplanned downtime and disrupt production. This study aims to predict whether a machine component will fail within the next 24 hours using historical sensor readings, error logs, maintenance records, and machine characteristics. The task is formulated as a multiclass classification problem that identifies the component expected to fail or predicts no failure, enabling earlier maintenance planning.

## Data Description

1. Telemetry Time Series Data `PdM_telemetry.csv`. Sensor measurements:
    - datetime: Timestamp of the hourly measurement;
    - machineID: Unique identifier of the machine;
    - volt: Hourly average voltage;
    - rotate: Hourly average rotational speed;
    - pressure: Hourly average pressure;
    - vibration: Hourly average vibration level.

2. Error logs `PdM_errors.csv`. Records of non-fatal errors encountered during machine operation. An error does not necessarily indicate a component failure:
    - datetime: Timestamp of the error event;
    - machineID: Identifier of the machine that generated the error;
    - errorID: Error category (error1 through error5).

3. Maintenance records `PdM_maint.csv`. Component replacements performed during scheduled maintenance or following a failure
    - datetime: Timestamp of the component replacement;
    - machineID: Identifier of the serviced machine;
    - comp: Replaced component (comp1 through comp4).  
		
    Components are replaced under two situations:
    - During the regular scheduled visit, the technician replaced it (Proactive Maintenance);
    - A component breaks down and then the technician does an unscheduled maintenance to replace the component (Reactive Maintenance). This is considered as a failure and corresponding data is captured under Failures. Maintenance data has both 2014 and 2015 records. This data is rounded to the closest hour since the telemetry data is collected at an hourly rate.																	

4. Component failures `PdM_failures.csv`. Recorded component failures used to construct the prediction target:
    - datetime: Timestamp of the component failure;
    - machineID: Identifier of the machine where the failure occurred;
    - failure: Failed component (comp1 through comp4).

    In the original file, failure describes an observed event. For this study, these events are used to label earlier telemetry records according to whether a failure occurs within the following 24 hours.

5. Machine characteristics `PdM_machines.csv`. Machine characteristics:
    - machineID: Unique identifier of the machine;
    - model: Machine model category (model1 through model4);
    - age: Machine age in years.
