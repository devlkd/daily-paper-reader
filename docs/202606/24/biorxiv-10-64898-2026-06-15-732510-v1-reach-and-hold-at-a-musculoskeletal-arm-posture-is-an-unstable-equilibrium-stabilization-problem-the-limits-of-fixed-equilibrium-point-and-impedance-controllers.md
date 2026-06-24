---
title: "Reach-and-hold at a musculoskeletal arm posture is an unstable-equilibrium stabilization problem: the limits of fixed equilibrium-point and impedance controllers"
title_zh: 在肌肉骨骼手臂姿态的伸手保持是一个不稳定平衡稳定问题：固定平衡点和阻抗控制器的局限性
authors: "Kobayashi, J."
date: 2026-06-20
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.15.732510v1.full.pdf"
tags: ["query:grav-offload"]
score: 7.0
evidence: 测试了重力补偿前馈和精确逆静力学重力平衡指令用于抗重力臂姿态
tldr: 在肌肉骨骼运动控制中，冗余肢体抗重力姿态保持是一个基本问题，但固定控制器能否胜任尚不明确。本研究在MyoSuite手臂模型上，用冻结标准评估了平衡点反射、阻抗控制等多种固定无学习控制器。结果显示所有方法均未能实现稳定的近目标保持，系统加速度-位置雅可比矩阵具有正实特征值，揭示局部动力学不稳定。该工作表明伸手保持本质是动力学不稳定镇定问题，固定平衡点控制器仅能放置平衡却无法稳定，推动向学习型阻抗与预测控制方向探索。
source: biorxiv
selection_source: fresh_fetch
motivation: 验证固定、生物启发的控制器是否足以在冗余肌肉骨骼系统中实现抗重力姿态保持，解决长期争议。
method: 在MyoSuite myoArm模型上，采用冻结标准协议，评估lambda反射、端点阻抗、重力补偿等固定控制器，并分析加速度-位置雅可比矩阵特征值。
result: 所有固定控制器均无法实现稳定近任务保持，参考反射存在结构极限环，阻抗控制器落于虚假平衡点，雅可比矩阵正实特征值证实局部不稳定。
conclusion: 伸手保持是动力学不稳定镇定问题，固定平衡点控制器可放置目标平衡但缺乏稳定能力，需转向学习型选择性阻抗与预测内部模型控制。
---

## 摘要
在重力作用下保持冗余肢体在指令姿态是肌肉骨骼运动控制的一个基本问题。固定的、基于生物学的控制器能否实现这一点仍不清楚。使用MyoSuite myoArm，在冻结标准、哈希来源的协议下，我们评估了固定的、非学习的控制器：平衡点/参考（lambda）反射、带共收缩的反射、末端笛卡尔阻抗控制器、重力补偿前馈以及精确的逆静力学重力平衡指令。没有一个能实现稳定的近任务保持。测试的参考反射放置了一个接近目标的平衡（在最低目标处最佳为0.048 m），但维持了一个结构性极限环，速度阻尼未能消除；末端阻抗稳定在远处的虚假平衡点；精确的重力平衡激活可以存在，但部署时却失效。在34和63肌肉模型中评估的姿态匹配目标，缩减的加速度-位置雅可比矩阵具有正实特征值，表明存在局部不稳定的二阶模态。在34肌肉模型中，完整的固定控制器网格也未能产生稳定的近任务保持。在63肌肉模型中，测量的末端刚度跨越了人类量级，并且共收缩扫描下具有类似人类的椭圆轴比，因此失败不能归因于松弛或非生物性装置。我们得出结论，伸手保持是一个不稳定动力学稳定问题：测试的固定平衡点/参考控制器可以放置近目标平衡，但不能稳定它。这些结果促使学习型选择性阻抗和预测/内部模型控制成为下一类机制，将平衡放置与稳定分离开来。

## Abstract
Holding a redundant limb at a commanded posture against gravity is a basic problem in musculoskeletal motor control. Whether fixed, biologically grounded controllers can achieve it remains unclear. Using the MyoSuite myoArm under a frozen-criterion, hash-provenanced protocol, we evaluate fixed, non-learning controllers: an equilibrium-point/referent (lambda) reflex, a reflex with co-contraction, an endpoint Cartesian impedance controller, a gravity-compensation feedforward, and an exact inverse-statics gravity-balancing command. None achieves a stable near-task hold. The tested referent reflex placed a near-target equilibrium (best 0.048 m at the lowest target), but sustained a structural limit cycle that velocity damping did not cure; endpoint impedance settled at far false equilibria; and an exact gravity-balancing activation can exist while deployment falls away. At posture-matched targets evaluated in both the 34- and 63-muscle models, the reduced acceleration-position Jacobian has positive real eigenvalues, indicating locally unstable second-order modes. In the 34-muscle model, the full fixed-controller grid also fails to produce a stable near-task hold. In the 63-muscle model, measured endpoint stiffness spans human-scale magnitudes and human-like ellipse axis ratios across a co-contraction sweep, so the failure is not explained by a limp or non-biological plant. We conclude that reach-and-hold is an unstable-dynamics stabilization problem: the tested fixed equilibrium-point/referent controller can place a near-target equilibrium, but does not stabilize it. These results motivate learned selective impedance and predictive/internal-model control as the next class of mechanisms, separating equilibrium placement from stabilization.