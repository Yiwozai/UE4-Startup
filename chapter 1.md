# 一、 Unreal 4 术语

## 1. Project 
项目（Project） 是一个自成体系的单元，保存所有组成单独游戏的所有内容和代码。

## 2. Object
在虚幻引擎中，最基础的构建单元叫做 Object，它包含了很多游戏资源必需的幕后功能。虚幻引擎4中几乎所有的东西都是继承自Object（或从中获取部分功能）。在C++中，UObject 是所有Object的基类，实现了诸如垃圾回收、开放变量给编辑器的元数据（UProperty），以及存盘和读盘时的序列化功能。 

## 3. Class
类（Class） 用于定义在创建虚幻引擎游戏中使用的特定Actor或对象的行为和属性。

## 4. Actor
可放入关卡中的对象都是 Actor。Actor是支持三维转换（如平移、旋转和缩放）的泛型类。可通过游戏进程代码（C++或蓝图）创建（生成）及销毁Actor。在C++中，AActor是所有Actor的基本类。 

## 5. Component
组件（Component） 是可添加到Actor的一项功能。组件不可独立存在，但在将其添加到Actor后，该Actor便可以访问并可以使用该组件所提供的功能。

## 6. Pawn
Pawn 是Actor的一个子类，充当游戏中的化身，例如游戏中的角色。Pawn可以由玩家或游戏AI以非玩家角色（NPC）的形式控制。 

## 7. Character
角色（Character） 是Pawn Actor的子类，旨在用作玩家角色。角色子类包括碰撞设置、双足运动的输入绑定，以及由玩家控制的运动附加代码。 

## 8. PlayerController
玩家控制器（PlayerController） 类用于在游戏中获取玩家输入并将其转换为交互，每个游戏中至少有一个玩家控制器。

它也是多人游戏的主要网络交互点。在多人游戏中，服务器为游戏中的每个玩家提供一个玩家控制器实例，因为它必须能够对每个玩家进行网络函数调用。每个客户端只有与其玩家相对应的玩家控制器，并且只能使用其玩家控制器与服务器通信。 

## 9. AIController
就像玩家控制器拥有一个兵卒作为游戏中玩家的代表一样，AI控制器也拥有一个兵卒来代表游戏中的非玩家角色（NPC）。

## 10. Level
level （关卡）是用户定义的游戏区域。 我们主要通过放置、变换及编辑Actor的属性来创建、查看及修改关卡。 在虚幻编辑器中，每个关卡都被保存为单独的.umap文件，所以它们有时也被称为“地图”。 

## 11. World
世界场景（World） 中包含载入的关卡列表, 它可处理关卡流送和动态Actor的创建生成。

## 12. GameMode
游戏模式（GameMode） 类负责设置正在执行的游戏的规则。规则可包括玩家如何加入游戏、是否可暂停游戏、关卡过渡，以及任何特定的游戏行为（例如获胜条件）。 

您可以在 项目设置（Project Settings） 中设置默认的游戏模式，但可以逐关卡地对其进行覆盖。无论您选择如何实施游戏模式，每个关卡始终只有一个游戏模式。在多人游戏中，游戏模式只存在于服务器上，规则将被复制（发送）到每个联网的客户端。 

## 13. GameState
游戏状态（GameState） 包含要复制到游戏中的每个客户端的信息，简而言之，它表示每个联网玩家的“游戏状态”。

它通常包含有关游戏分数、比赛是否已开始和基于世界场景玩家人数要生成的AI数量的信息，以及其他特定于游戏的信息。 对于多人游戏，每个玩家的机器上都有一个游戏状态实例，而服务器的实例为权威实例（或客户端从其获得更新信息的实例）。 

## 14. PlayerState
玩家状态（PlayerState） 是游戏玩家的状态，例如人类玩家或模拟玩家的机器人。作为游戏世界场景的一部分而存在的非玩家AI将不会拥有玩家状态。 

在玩家状态中适当的示例数据包括玩家姓名或得分、当前等级或生命值，或当前是否在抢旗游戏中携带旗帜。 对于多人游戏，所有玩家的玩家状态存在于所有机器上（与玩家控制器不同），并且可以将数据从服务器复制到客户端以保持同步。 