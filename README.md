# sleepstudies
various tidbits regarding my attempts to study sleep habits



# Step-by-step howtos:
### installing and using muselsl
```
  pip install muselsl     #install the muselsl package in python
  # My fork of the muselsl repo provides a bit of extra functionality:
  #   1) --persistent
  #   2) recordHdf5:  This lets me record multiple lsl streams into an hdf5 file, and properly 
  #       preserve timestamps (which seems to be something that the edf format lacks).  Datasets
  #       can then be loaded into pandas with a command like "x = pd.read_hdf('recording1.h5', 'Muse/EEG')"
  #   3) view non-eeg streams
  git clone ...
  cd muselsl
  pip install -e .
  
  # run the muselsl streamer;  note the --persistent flag for restarting after disconnects
  #   -using "-b gatt" because the default bluetoothctl timeout wasn't working and hung muselsl stream
  #   -using "-i hci1" because the built-in bluetooth on my laptop had very poor sensitivity
  #      -using the built-in bluetooth, the muse s disconnects just from me putting my hand on my forehead
  #      -using this instead, which lets me walk around the house without disconnecting: https://www.amazon.com/gp/product/B08LVH5BCP/
  #      -note that I had to upgrade my kernel to 5.8, and install the firmware here: https://linuxreviews.org/Realtek_RTL8761B
  sudo /home/a/anaconda3/bin/muselsl stream -a 00:55:DA:B9:43:06 -n MuseS-4306 -b gatt -i hci1 -p -c -g --persistent
  
  # record the lsl streams to a hdf5 file
  muselsl recordHdf5 -t EEG,PPG,GYRO,ACC
  
  # view live traces of the muselsl data received over lsl
  muselsl view -w 10 -s 10 -r 10 -v 2 -f 10x5
```  

### Getting TinySleepNet to work:


### Hacking the Muse S to record Cz and Pz:


### Fitting TinySleepNet on other datasets



  
