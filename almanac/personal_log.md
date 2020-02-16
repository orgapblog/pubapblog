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
- 21:00 Increase home partition ubuntu

# 17/02/2020
- 09:00 Submit Gen-RKM to Johan.
- 09:30 Think again from basics & uncorrelatedness constraint on H: H^t*H = I.
