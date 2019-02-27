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

- CEM reset!
- KDC hw2: inner loop... index 1-based or 0-based..

- flag boolean: `Feb, 19`
    + flags.DEFINE_bool --nofoo / --nofoo`=`False
    + args boolean also does some weird thing
- Don't naively call numpy.random.rand() in torch multi threading. bc numpy does not handle fork() properly [ref](https://github.com/pytorch/pytorch/issues/5059)
```
def worker_init_fn(worker_id):
    if opts.is_train :
        np.random.seed(np.random.get_state()[1][0] + worker_id)
    else:
        np.random.seed(opts.seed + worker_id)

DataLoader(
        dset,
        batch_size=batch_size,
        shuffle=shuffle,
        num_workers=opts.n_data_workers,
        drop_last=True,
        worker_init_fn=worker_init_fn)        
```