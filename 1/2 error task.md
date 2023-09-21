Q. By mistakenly I was deleted my grub 2 file and instance has occur ½ error. How reinstall grub2 files.

              See following instance has ½ error occurred I have to recover it by put grub2 file in it.
So see following steps to how to get it.
 

Step 1:-
               Now you have to create 2 instances as recovery instance. First one is create with kernel 5.10 instance and second one is same as ½ error instance means same os same configuration and same kernel(6.1) as it is.

Step 2:-
             So first of all  launch 1st instance with kernel 5.10. and name it “1st recov with 5.10 kernel”. 
 

 




Step 3:-
             Now launch second instance with same configuration of ½ error instance same as it is. 
 

Step 4:-
              Now you have to stop  “1st recov with 5.10” instance because we have detach its volume.
 

      












Step 4:-
             After that go EBS means go to volume section and attach 1st recov. Instance’s volume to  2nd instance. Because 2nd instance’s grub2 file are same as ½ error instance. So we have to get that grub2 file by the help of 1st recovery instance. 1st recovery instance is 5.10 kernel so it was different block uid from ½ error. Because of this 1st recovery instance is mount in 2nd instance.
 

  
 
              
Step 5:-
               Now  get access of 2nd instance by third party application or by aws programmatic access and make 1st instance’s volume mount in it. And copy grub2(/boot/grub2) file of 2nd instance’s to one of 1st instance directory which has mounted in /mnt. I  was copy in /mnt/mnt.  See the following steps how to do it.
 


Step 6:-
         Now I was get access of 2nd instance. Now see 1st instance volume was attached or not by run command lsblk. See in the image there is attached volume it is denoted by partition name xvdf1.
 

Step 7:-
              Now run command to temporary mount to  1st instance’s volume. And 1st instance is mounted in /mnt.
 
 

Step 8:-
          Now you have to copy grub2 file of 2nd instance which is same as ½ error’s instance grub2 files. That grub2 file was copy in /mnt/mnt. Run the command “#cp -r /boot/grub2 /mnt/mnt.
 

Step 9:-
            Now unmount 1st instance volume from /mnt by run command “#umount /mnt”. Because u got grub 2 file to transfer in ½ error instance so unmount it.
 

Step 10:-
                Then go aws account and detach 1st instance volume from 2nd instance volume. 
 





















Step 11:-
                    And attach it to its own instance means 1st instance. But attach time gave that device name means partition name “xvda” because this name is its root volume name. and then attach it. And then start your instance.
 

 
 

Step 12:-
                Oky now you have get the grub2 files so now u have to move that grub2 file to ½ error instance volume. So stop the ½ error instance to detach its volume.
 

Step 13:-
               Now go volume section and detach the ½ error isnatnce volume.
 













Step 14:-
              And after that attach ½ error instance volume to 1st recov instance.
 

 





Step 15 :-
                Now get access of 1st instance by third party app or aws  programmatic access. And mount ½ errors volume mount in it. And then move grub2 file which we have get from 2nd instance and saved in /mnt of 1st instance. 
 

Step 16:- 
              Now I was get access of 1nd instance. Now see ½ error instance volume was attached or not by run command lsblk. See in the image there is attached volume it is denoted by partition name xvdf1.
 

Step 17:-
              Now run command to temporary mount to ½ error instance’s volume. And  ½ error instance volume is mounted in /home.
 




Step 18:-
               Now go to /mnt where the copied grub2 file was exist and move that grub2 file to mounted ½ errors instance volume’s boot directory.  Run command “#mv grub2 /home/boot”. And grub2 file was safely moved to ½ errors volume. Now unmount the ½ error’s volume.
  
 

Step 19:-
              Now go to aws volume section and detach the ½ erros volume from 1st recov instance.
 











Step 20:-
               And attach to it self means attach to ½ errors instance. And then gave it a root device name means its root partition name “xvda”. “xvda” is a its root volume name without that name it can’t be ½ errors root volume so remember that.
 
 




Step 21:-
              Now restart the ½ errors instance and wait for few min. and  see your instance is recover safely and with all your data.
 

 


                                                                *** THE END ***

















