# NoShow Prediction Model

Machine learning model that predicts whether a patient will miss 
their hospital appointment. Built as part of the MediCure Hospital 
Management System research project.

## Model Details
- Algorithm: Random Forest Classifier
- Training data: Kaggle Medical Appointment No-Show dataset (110,527 records)
- Accuracy: 76%
- Export format: ONNX (for C# integration)

## Features Used
| Feature | Description |
|---|---|
| Gender | Patient gender (0=Female, 1=Male) |
| Age | Patient age (0-100) |
| DaysInAdvance | Days between scheduling and appointment |
| AppointmentDayOfWeek | Day of week (0=Monday, 6=Sunday) |
| Scholarship | Patient on welfare program |
| Hipertension | Patient has hypertension |
| Diabetes | Patient has diabetes |
| Alcoholism | Patient has alcoholism |
| SMS_received | Patient received SMS reminder |

## Known Limitations
- Class imbalance: 80% show-up vs 20% no-show in training data
- No-show recall is 0.23 — model is conservative in flagging risk
- Trained on Brazilian hospital data — cultural context may differ

## Integration
The `noshow_model.onnx` file is consumed by MediCure's 
`NoShowPredictionService.cs` via Microsoft.ML.OnnxRuntime.

## Related Repository
[MediCure HMS](https://github.com/ilma-wafa/MediCure)

## Model File
The `noshow_model.onnx` file is not included in this repo due to 
GitHub's 100MB file size limit (model is 119MB).

To regenerate it, run:
python train_model.py
This will retrain the model and export a fresh `noshow_model.onnx` file.