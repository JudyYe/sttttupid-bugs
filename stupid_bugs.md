# Some STUPID mistakes I made

## Training Neural Network
- last layer nonliniearity. if it's ReLU, then the logits are all positive...
- BN makes a differencel. sometimes, we want evaluation mode to use statistic in the current batch instead of history batch.
- during test, forget to restore model first... `Feb, 18`
    + symptom: if the result is graph / structure dependent, it is hard to find
    + surprise outcome: some network highly depends on the graph instead of the representation you learn. Even random initialization can get good result.
- Loaded unexpected variables when loading pretrained model... `May, 18`
    + symptom: loading / finetuning does not get what we expected lr. 
    + diagnose: should be easy to find this bug if you use tensorboard
    + surprise outcome: just stupid...
- Forget bias when representing a classifier parameters `Nov, 17`
    + surprise outcome: does not affect performance so much
- 

