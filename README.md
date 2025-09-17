# NeRF from scratch
Wanted to play with NeRFs, so that's that.
Ran it on Google colab T4 GPU. Used gemini to generate the problem and rendering views: an elongated, illuminated and colorful torus.

![torus](imgs/torus.png)

Used a basic FCN NeRF, positional encoding like described in the original paper.

In every epoch, I go over all (sampled once) given 50 training views. From each view\step, I sample only some of the pixels (for computational efficiency in every step).

I also added an option to separate a single view to different batches according to the batch size.

After playing with it a bit, it seemed like unweighted pixels loss didn't allow learning, and instead the output was fixed to be the color of the background, but weighting according to background\not-background with {0.1, 1} weights solved that issue.

Because colab is limited, it only ran for 200 epochs, but it already seems to be starting to do relatively okay:

![t0](imgs/test_pred_0.png)
![t1](imgs/test_pred_1.png)
![t3](imgs/test_pred_3.png)

[Original paper](https://arxiv.org/abs/2003.08934):
Mildenhall, B., Srinivasan, P. P., Tancik, M., Barron, J. T., Ramamoorthi, R., & Ng, R. (2021). Nerf: Representing scenes as neural radiance fields for view synthesis. Communications of the ACM, 65(1), 99-106.
