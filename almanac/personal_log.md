---
layout: default
title: Almanac
---

# 09/02/2020
- 22:57 Initiated this txt file

# 10/02/2020
- 09:00 finish SWEET self-assessment. #done
- 09:30 CelebA (high quality & multi-view)
    - 4 instances running on vsc
        - failed out-of-memory error. allocate >=12gb for 5k samples
        - 1 instance on liefmans. aborted 
- 10:00 MNIST #done
- 11:00 Stiefl 
- 14:00 Review Gen-RKM #done

# 11/02/2020
- 09:00 CelebA (high quality & multi-view)
	- free memory after training bcoz always there is cuda memory error. #done
	  there was error in loading files
	- Fixed that and also added code to load the best model so far.
- 10:30 Stiefl 
	- check the effect of division by eig_values
	- think about removing the mean in feature-maps. Doesn't work :( why?

- 21:00 check celebA vsc status

# 12/12/2020
- 09:30 Solidify understanding multi-gpu training #Ndone
- 10:00 updates on Stiefel ?
	- think about removing the mean in feature-maps. Check with decoder directly learning from embeddings.
	  tried, but doesn't work.

# 13/02/2020
- 10:00 started Mul-view Celeb on vsc. waiting for celebA to finish. just select from previous batch. #done
- 11:00 Stiefel manifold

# 14/02/2020
- 09:00 play with Stiefel mnist code
- 15:00 try stiefel cayley transform #Ndone
- 16:00 meet Johan to discuss Gen-RKM journal version

# 15/02/2020
- 09:30 started on vsc h2 celeba. monitor
- 10:30 Stiefel mnist: kernel gives better orthogonal H that cov. Primal formulation works better! why?
- 19:00 make cv and cover letter #done
- 22:00 try stiefel cayley transform

# 16/02/2020
- 09:00 try stiefel cayley transform 
- 11:00 played with idea of asking uncorrelatedness constraint on H: H^t*H = I. 
- 14:00 Init the Idea if recurrent RKMs. Decoder part and Training needs to be figured-out. 
- 15:00 Finished Gen-RKM paper from my side.
- 19:30 Final read Gen-RKM #done
- 21:00 Increase home partition ubuntu #Ndone

# 17/02/2020
- 09:00 Submit Gen-RKM to Johan.
    - retrying celebA exp with capacity 16 and new normalized U.
    - try bce loss? since it worked well for mnist: doesn't work for celeb, generates more smoother images 
    - also trying fine-tuning the old model: slightly better results
    - finished from my side.
- 09:30 Think again from basics & uncorrelatedness constraint on H: H^t*H = I.
    - uncorrelatedness in H is implicitly enforced by 1^st term in obj. IDK
    - What works in the end is to compute the U, s, _= svd(C). This is efficient even on full datasets.
    - Q. x_tilde using michael's or mine ?
    
# 18/02/2020
- 09:00 Sent revised gen-RKM to johan
- 09:30 fixed cov and kpca relation
    - test it on mnist: works great on small dataset, now testing for N=20k and N=50K on VSC . Failed...probably feature-maps were not complex enough
- 11:00 Stiefel
    - started stiefels_3dshapes
    - Q. x_tilde using michael's or mine ?
- submitted gen-rkm to journal

#19/02/2020
- Spent 1st half on init class rkm and code clean-up
- 13:00 Stiefel
- 18:00 distributed training on multiple gpus #Ndone

#20/02/2020
- stiefel adam_cayley done coding
- meeting with octave
- discussion on RKM

