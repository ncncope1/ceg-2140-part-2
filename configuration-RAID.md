choice is raid 6 as it can survive 2 drive failures, with the con being 
less usable storage, i chose this as I have dealt with drive failures in the past and dont wanna take that risk

Usable = (n - 2) × S for raid 6

Usable = (n - 1) × S

i have 10 cores so n = 10 in my case

commands
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/xvdf /dev/xvdg /dev/xvdh

output

mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.

sudo mkfs.ext4 /dev/md0

ARRAY /dev/md0 metadata=1.2 ncncope1=ip-54.81.57.156:0 UUID=3a1b2c3d:4e5f6789:cdby:9840ehib

UUID=3f8c2a1b-9c4d-4e2a-8d7a-42990425cco /mnt/raid_data ext4 defaults,nofail 0 0
5 

Personalities : [raid6] 
md0 : active raid5 xvdh[2](F) xvdg[1] xvdf[0]
      10475520 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]


Personalities : [raid6]  
md0 : active raid5 xvdh[3] xvdg[1] xvdf[0]
      10475520 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [UU_]
      [====>................]  recovery = 22.4% (1176576/5237760) finish=1.1min speed=58432K/sec
took about 88 seconds
