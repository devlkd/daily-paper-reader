---
title: "ANNet: A first-principles neural network for forward and inverse dynamics"
title_zh: ANNet：一种用于正向与逆向动力学计算的第一性原理神经网络
authors: "Bahdasariants, S., Parola, L., Kacker, K., Feldman, A. K., Zdobinski, Z., Kang, I., Weber, D. J."
date: 2026-06-08
pdf: "https://www.biorxiv.org/content/10.64898/2026.06.03.729998v1.full.pdf"
tags: ["query:grav-offload"]
score: 7.0
evidence: 提出物理信息神经网络用于机器人逆动力学，可应用于主动重力补偿。
tldr: 生物与机器人系统在运动时需分别求解逆动力学和正动力学，常建模为独立映射，忽略共享结构。ANNet通过物理信息神经网络学习标量Appell加速度能量，将两者统一到共同表示。逆动力学直接对能量函数求导获得关节力矩，正动力学则利用相同能量景观构建优化目标，无需重训练。在双摆实验中，未见轨迹的逆解和正向模拟均达到实时精度。该框架为神经科学与机器人学的预测与控制提供了第一原理的统一路径。
source: biorxiv
selection_source: fresh_fetch
motivation: 传统的逆动力学与正动力学通常作为独立映射分开估计或实现，忽视了二者共享的物理结构，难以形成统一表示。
method: ANNet基于物理信息网络学习Appell加速度能量标量函数，逆动力学通过对其求导得到力矩，正动力学通过优化包含该能量景观的目标函数实现。
result: 在双摆任务中，网络未见过的轨迹上，逆动力学计算与基于优化的正向模拟均实时准确。
conclusion: ANNet证明了通过单一学习标量函数可同时支持预测和控制，为统一正逆动力学提供了原理性方案。
---

## 摘要
生物与机器人系统在运动时必须求解两种相关的计算：逆向动力学，确定产生期望运动所需的力或力矩；正向动力学，将施加的力映射为运动。尽管这两种计算通过相同的运动方程耦合在一起，但在基于模型和数据驱动的框架中，它们通常被分别估计或实现为独立的逆向与正向映射。这种分离可能掩盖约束这两个问题的共享结构。为此，我们提出ANNet，一个物理信息神经网络，通过从经典力学中学习单一标量——Appell加速度能量，将两种计算置于共同的表征之上。该网络将运动学状态和候选加速度映射到这一标量函数，而逆向动力学则通过将学习到的能量函数对加速度求导以恢复关节力矩来获得。正向动力学无需重新训练，只需将学得的能量景观嵌入一个优化目标中，其无约束最小值满足吉布斯-Appell方程，即可计算得到，由此产生的加速度则通过时间积分向前推进。我们在双摆范式上评估了ANNet。在网络训练时未见过的试验中，基于逆向和优化的正向仿真均实现了实时精度。我们的结果为使用单一学得表征来同时支持预测和控制提供了一条第一性原理途径。

意义机器人和动物在运动时必须解决两个问题：计算期望运动所需的力或力矩（逆向动力学），以及确定施加力所产生的运动（正向动力学），这两者通常被分开建模。我们展示了这两个问题可以通过经典力学中的一个标量函数——Appell加速度能量——来表达。训练一个神经网络，使其学习到的该函数的导数与参考关节力矩相匹配，即可实现逆向动力学。然后，同一网络通过最小化由学得能量景观构建的目标函数来计算正向动力学，而无需重新训练。这一框架为神经科学和机器人学中的预测与控制提供了统一的表征。

## Abstract
Biological and robotic systems must solve two related computations to move: inverse dynamics, which determines the forces or torques needed to produce a desired movement, and forward dynamics, which maps applied forces to motion. Although these computations are coupled by the same equations of motion, they are usually estimated or implemented as distinct inverse and forward mappings, in both model-based and data-driven formulations. This separation can obscure the shared structure that constrains both problems. Here, we present ANNet, a physics-informed neural network that places both computations on a common learned representation by learning a single scalar quantity from classical mechanics--Appell acceleration energy. The network maps kinematic state and candidate accelerations to this scalar function, and inverse dynamics is obtained by differentiating the learned energy function with respect to acceleration to recover joint torques. Forward dynamics is then calculated without retraining by embedding the same learned energy landscape in an optimization objective whose unconstrained minimum satisfies the Gibbs- Appell equation. The resulting accelerations are integrated forward in time. We evaluate ANNet on a double pendulum paradigm. In trials unseen by the network during training, inverse and optimization-based forward simulations are real-time accurate. Our results provide a first-principles route for using a single learned representation to support both prediction and control.

SignificanceRobots and animals must solve two problems to move: computing the forces or torques needed for a desired motion (inverse dynamics) and determining the motion produced by applied forces (forward dynamics), which are usually modeled separately. We show that both problems can be expressed using a single scalar function from classical mechanics, Appell acceleration energy. A neural network trained so that the derivative of this learned function matches reference joint torques performs inverse dynamics. The same network then computes forward dynamics by minimizing an objective built from the learned energy landscape, without retraining. This framework provides a unified representation for prediction and control in both neuroscience and robotics.