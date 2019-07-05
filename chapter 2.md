# 第二章、 Unreal Editor 手册

## 第一节、 基本操作

### 1. 获取帮助
- 富工具提示：某些工具提示有一个“富工具提示”，此时按下（Ctrl + Alt）可以了解更多信息文本。
- 帮助图标：编辑器的某些部分旁边可能会显示 “?” 图标，这链接至外部文档。
- 帮助菜单：在窗口按下"F1"可打开相应文档页面。
- 帮助搜索：您可以使用编辑器主窗口右上角的“帮助搜索”栏来搜索帮助。 

### 2. 控制Actor

| 操作 | 行为 |
| :--: | -- |
| 鼠标左键 + 拖拽 | 根据当前激活的 transform 形态，对选中 Actor 进行移动、旋转、缩放 |
| W | 选择移动工具 Move Tool |
| E | 选择旋转工具 Rotate Tool |
| R | 选择缩放工具 Scale Tool |
| V | 开启/关闭位置吸附，这能直接吸附关卡中其他物件上 |
| 鼠标中键 + 拖拽 | 临时移动物体的 Pivot 位置以便于做进一步的旋转缩放调整 |
| Ctrl + W | 复制当前选中的 Actor |
| H  | 隐藏当前选中的 Actor |
| Ctrl + H | 取消隐藏所有的 Actor |
| Shift + E | 依照当前选中的 Actor，选择关卡中所有同类型的其他 Actor |
| Ctrl + 鼠标左键 | 将该 Actor 添加到当前选中 Actor 的集合中 |

### 3. 运行和模拟
虚幻编辑器允许在关卡中任何地方生成玩家,且可以立即从编辑器中预览游戏，不必等待保存文件。有两种可用的预览模式： Play In Editor（在编辑器中运行） (PIE) 功能可以通过位于主工具条上的 Play（运行） 按钮直接访问， 而 Simulate In Editor（在编辑器中模拟） (SIE) 功能则可以通过 Play(运行) 按钮的下拉菜单中访问(或则会按下 Alt+S 键)。 

## 第二节、 关卡
### 1. 使用关卡资源
- 创建：在 Content Browser 中创建关卡的方法和 创建其他资源 相同，如蓝图类、材质，或粒子系统。然而也可从 File 菜单创建关卡，因为它们是项目的布局和组织。 
- 保存：最初保存后的关卡保存是一个极为透明的过程，可从 File 菜单或 Content Browser 开始，但首次保存需要执行几个额外的步骤。
- 打开：在 Content Browser 中双击关卡资源可打开关卡。和创建关卡一样，也可通过 File 菜单执行。 

### 2. 管理多个关卡
关卡通过 关卡（Levels） 窗口来管理。您可以通过 Windows 菜单访问 关卡（Levels） 窗口。 

您将始终拥有一个 固定关卡（Persistent Level），同时您可以拥有一个或多个子关卡，这些关卡将始终加载或使用关卡流送体积（Level Streaming Volume）、蓝图（Blueprint）或C++代码加载流送。

### 3. 世界场景设置
通过 World Settings 选项将特有设置应用到每个关卡。通过 World Settings 选项可执行一系列操作，从游玩关卡时启动正确的 游戏模式，到调整关卡的全局照明。 

### 4. 变更默认关卡
在 项目设置 编辑器中可对一些项目特定设置进行修改。其中包括对项目玩家载入的关卡进行设置。在默认游戏关卡外还可设置一个默认编辑器关卡，即时载入经常使用的关卡，加快工作流程。 

### 5. 通过关卡分段进行协作
关卡是二进制资源，团队成员在项目相同部分协同工作时可能面临一些挑战。 

设置“固定流动”的关卡分段后，多名开发人员即可同时在同一个游戏“空间”中进行工作。例如可设置一个包含场景所有音频的关卡分段，以及包含场景布局静态网格体的关卡分段。每个关卡分段仅限单人单次操作。对场景的 Actor 进行仔细分割后，即可将重复工作的区域缩减到最少。 

## 第三节、 Actor和几何体
### 1. 常见Actor类型
| 类型 | 图标 | 描述 |
| :--: | :--: | -- |
| 网格物体 & 几何体Actor类型 | | |
| StaticMeshActor | ![](\image\3-1.png) | 静态网格物体Actor 是一种简单的Actor类型，用于在场景中显示一个网格物体。尽管其名称暗示该Actor是静态的或者是不能移动的，但是此名称中的“静态”是指这种网格物体类型使用的是StaticMesh（静态网格物体）。由于这些网格物体的几何体不能改变，所以这些网格物体是静态的。但是，实际上在游戏运行过程中可以通过其他方式来移动及修改Actor。这些Actor一般用作为“世界几何体”及装饰性网格物体，以创建关卡的场景。 |
| Brush  | ![](\image\3-2.png)| 画刷是一种基本类型的Actor，用于在场景中显示简单的三维几何体。在关卡编辑器中，可以使用"几何体编辑模式"修改这些Actor。画刷(或BrushActors) 常用于快速设置场景原型，粗略构建出场景来测试游戏性。 |
| SkeletalMeshActor  | ![](\image\3-3.png)| 骨架网格物体Actor，这种Actor类型显示一个带动画的网格物体或骨架网格物体，它的几何体可以发生变形，变形一般通过应用创建的及从外部3D动画用程序中导入的动画序列来完成。这些Actor通常用于类似于角色、活动的生物、及复杂的机器这样的物体；及用于任何需要变形或显示复杂运动的物体。这些Actor也经常同Matinee结合使用，来创建过场动画序列 |
| 游戏性Actor类型 |  |
| PlayerStart  | ![](\image\3-4.png)| Player Start（玩家起点） 是一种放置在关卡中，用于指定游戏开始时玩家起始位置的Actor。 |
| Triggers  | ![](\image\3-5.png) ![](\image\3-6.png) ![](\image\3-7.png)| Triggers（触发器） 是一种Actor，作用是当关卡中的其他对象同其交互时触发事件。 换句话说，它们被用于触发事件从而响应关卡中的其它操作。 触发器一般都是相同的，不同之处仅是其影响区域的形状 - 盒体、胶囊体及球体 - 触发器使用这些影响区域来检测另一个对象是否激活了它。  |
| MatineeActor  | ![](\image\3-8.png)| Matinee Actors 使您可以通过 Matinee 动画工具使得Actor的属性随着时间产生动画，从而创建动态的游戏性或者游戏中的过场动画。该系统是基于专用的动画轨迹的，您可以在该轨迹上放置关键帧来设置关卡中Actor的某些属性的值。Matinee动画编辑器和用于视频编辑的非线性编辑器类似，这使得它对于那些视频制作专业人员来说很熟悉。 |
| 光源Actor类型 |  |
| PointLight  | ![](\image\3-9.png)| 点光源 的工作原理很像一个真实的灯泡，从灯泡的钨丝向四面八方发出光。然而，为了性能考虑，点光源被简化为从空间中的一个点均匀地向各个方向发射光。放置的点光源可以设置为三个移动设置之一：静态、静止和可移动  |
| SpotLight  | ![](\image\3-10.png)| 聚光源 从圆锥形中的单个点发出光照。使用者可通过两个圆锥形来塑造光源的形状：内圆锥角和外圆锥角。在内圆锥角中，光照将达到完整亮度。从内半径的范围进入外圆锥角的范围中时将发生衰减，形成一个半影，或在聚光源照明圆的周围形成柔化效果。光照的半径将定义圆锥的长度。简而言之，它的工作原理类似于手电筒或舞台照明灯。和其他光源一样，聚光源可设为以下三种移动性设置中的一种：静态、静止和可移动|
| DirectionalLight  | ![](\image\3-11.png)| 定向光源 将模拟从无限远的源头处发出的光线。这意味着此光源投射出的阴影均为平行，因此适用于模拟太阳光。定向光源放置后，可对其移动性进行如下设置：静态、静止或可移动 |
| 特效Actor类型 |  |
| ParticleEmitter  | ![](\image\3-12.png)| 粒子发射器 是一种用于通过以平面粒子（相机朝向的平面）或网格物体的方式生成粒子来创建特效(比如烟雾、火焰、火花等)的Actor。粒子的实际行为定义在特殊的资源粒子系统中并由粒子系统进行控制 |
| AmbientSound  | ![](\image\3-13.png)| 环境音效Actors用于在世界中以Sound Cue的形式播放音效。这些音效可以时循环播放的也可以是非循环播放的，可以具有空间化及衰减效果，但所有这些必须在SoundCue中进行设置，而没有暴露在环境音效Actor本身上。 |

### 2. Actor操作
- 放置：在最基本的关卡上，Actor是您可以放置在关卡中的任何对象
- 选择：简单选择、场景大纲选择、区域选择框选择和高级选择技术
- 变换：变换是Actor移动、旋转或缩放
- 移动性：移动性（Mobility） 设置控制Actor是否可以在游戏进程中以某种方式移动或改变。其主要适用于静态网格体Actor和光源Actor。 可用时，移动性属性共有3种状态： 静态、静止和可移动
- 合并：用户可以使用“合并Actor”工具将多个静态网格体组合为一个新的单一Actor。
- 分组：在虚幻引擎中，您可以将Actor分组在一起，这可让您轻松地同时管理多个Actor。分组的Actor可以通过旋转、平移和缩放转换为单个单元。

| 热键 | 命令 |
| :--: | -- |
| Ctrl+G | 分组/重新分组 |
| Shift+G+G | 取消分组 |
| Ctrl+Shift+G | 切换组模式 |

## 第四节、 [组件](https://docs.unrealengine.com/zh-CN/Engine/Components/index.html)
组件（Component） 是可添加到Actor的一项功能。组件不可独立存在，但在将其添加到Actor后，该Actor便可以访问并可以使用该组件所提供的功能。

### 1. AI组件
AI 组件是一种可令 Pawn 从环境接收类似感知数据的组件，如噪声来源位置或 Pawn 是否可看到东西。 
- AI Perception Component（ AI 感知组件）：AIPerceptionComponent 用于注册为 AIPerceptionSystem 中的刺激信号监听器，并可收集已注册的刺激信号。当组件获得新刺激信号 (batched) 时，将调用 UpdatePerception。 
- Pawn Noise Emitter Component （Pawn 噪声发射器组件）：PawnNoiseEmitterComponent 追踪 SensingComponents 所使用的噪声事件数据以监听 Pawn。该组件用于存在于 Pawn 上或其控制器上。其在网络客户端上不进行任何操作。 
- Pawn Sensing Component （Pawn 感应组件）：Pawn 感应组件可包含 Actor 的感知（即，视觉和听觉）设置及功能，允许 Actor 在游戏世界中看到/听到 Pawn。其在网络客户端上不进行任何操作。 

### 2. 摄像机组件
CameraComponent （添加一个摄像机视角）和 SpringArmComponent （使其子项延长固定距离，然后在发生碰撞时收回），这两个组件一起使用，可提供一个第三人称视角，您可在游戏世界中对其进行各种调节。
- Camera Component （摄像机组件）：摄像机组件可以让您添加一个摄像机视角作为 Actor 的子对象。如果 ViewTarget 是 CameraActor，或者 Actor 包含摄像机组件且它的 bFindCameraComponentWhenViewTarget 选项设置为 True。 例如，如果在游戏过程中，您想要在关卡中切换多个摄像机。通过使用 SetViewTargetWithBlend 和 CameraActor，您可在各摄像机之间进行切换，并使用在 CameraActor 中为各摄像机定义的属性（包括视野、角度或任何后处理效果等）。 
- Spring Arm Component （弹簧臂组件）：弹簧臂组件会努力与其子对象之间保持一个固定距离，但如果发生碰撞，就会使子对象收回，如果没有碰撞，则使之发生回弹。通常，弹簧臂组件用作“摄像机摇臂”，可防止玩家的跟拍摄像机在游戏时间中发生碰撞。

![摄像机和弹簧臂组件](\image\4-1.jpg)

### 3. 灯光组件
不同类型的 Light Components 可将光照添加为 Actor 的子对象，取决于您想要实现的效果。无论您选择哪种灯光组件类型，都有一些总体灯光设置（灯光颜色或强度）或单独设置（参见各独立灯光的特定设置）可供调节。
- Directional Light Component （方向性灯光组件）：DirectionalLightComponent 模拟了从无穷远的光源发射出的灯光。这也就是说，这种灯光所投射的所有阴影都是平行的，使其成为模拟阳光的最佳选择。 
- Point Light Component （点灯光组件）：PointLightComponent 感觉上很像是现实世界中的灯泡，从灯泡的钨丝向着所有方向发射灯光。但是，为了提高运行性能，点光源组件被简化了，只从空间中的一个点均匀地向所有方向发射光线。 
- Sky Light Component （天空灯光组件）：SkyLightComponents 用于捕捉关卡中的远距离物体（距离大于 SkyDistanceThreshold 的所有物体），并将其作为灯光应用到场景中。这也就是说，天空的外观及其光线/反射将匹配。 
- Spot Light Component （射光圈组件）：SpotLightComponent 从锥形的单点发射出方向性光线。有一些设置可调节内锥角和外锥角，另外还有一些其他类型的光线设置，如强度、光线颜色和阴影设置。这种光线很适合作为手电筒，因为它可以定义内/外锥角半径。 

### 4. 移动组件
Movement Components 提供了朝着 Actor（或角色）所作的一种形式的移动，移动组件是该 Actor（或角色）的子对象。 
- Character Movement Component （人物移动组件）：CharacterMovementComponent 允许形象不使用物理刚体移动（走、跑、跳、飞、跌落和游泳）。 该组件专用于 Characters，任何其他类无法执行它。在创建 Blueprints 时，将根据角色类自动添加该组件，而不是手动添加。 
- Projectile Movement Component （抛射物移动组件）：在转动过程中，ProjectileMovementComponent 会更新另一个组件的位置。碰撞后弹跳以及朝着目标归位等行为由此类组件支持。 
- Rotating Movement Component （旋转移动组件）：RotatingMovementComponent 以指定旋转速率执行组件的连续旋转，也可围绕枢轴点偏置旋转。请记住，在移动过程中，无法进行碰撞测试。使用旋转移动组件的示例可以是飞机的螺旋桨、风车，甚至是一系列围绕太阳旋转的星球。 

### 5. 寻路组件
寻路组件是一种可在虚幻引擎 4 中修改或扩展 NavMesh(Pathfinding) 系统功能的组件。 
- Nav Modifier Component （导航修改器组件）：Nav Modifier Component 本身没有任何功能，但是，如果您有一个基本形状组件作为 Actor 的根，该根组件的音量将根据导航修改器组件的 Area Class 属性来修改 Actor 内的 NavMesh 生成。这些区域类可定义基本设置（如 Cost）以输入一个区域，或更加高级的设置，如蹲伏角色可移动的区域。
>成本是 NavMesh 系统的重要概念。简单地来说，使用 NavMesh 从一个点移动到另一个点的总成本等于所有移动路径的区域成本总和（单个区域的大小在项目首选项中定义）。但是，求解器将始终寻找成本最低的路径，因此，您可通过增加通过该区域的成本来让它避免某些区域（如湿滑的油腻地区或崎岖不平的地区）。例如，通过红色区域的成本非常高，但是 Pawn 没有其他选择，只能从中通过:
![](\image\4-2.jpg)
但是，如果您移除了墙壁,Pawn 将避免经过红色区域，即使它要绕更长的路线:
![](\image\4-3.jpg)

### 6. 物理组件
物理组件用于影响那些在您的场景中以不同方式应用物理效果的任意对象。 
- Destructible Component （可毁组件）：DestructibleComponent 用于存放 Destructible Actor 的物理数据。在添加该组件作为子对象时，您必须指定要使用的 Destructible Mesh 资源。
![可毁的玻璃](\image\4-4.jpg)
- Physics Constraint Component （物理约束组件）：PhysicsConstraintComponent 是一种能连接两个刚性物体的接合点，通过使用一个 PhysicsConstraintComponent 和两个 StaticMeshComponents，您可以创建悬摆型对象，如秋千、重沙袋或标牌，它们可以对世界中的物理作用做出响应，让玩家与组件进行互动。
![相互约束的物体](\image\4-5.jpg)
- Physics Handle Component （物理句柄组件）：PhysicsHandleComponent 用于“抓取”和“移动”物理对象，同时让您抓取的对象继续使用物理效果。这样的例子可能以“重力枪”的形式存在，此时您可以拾取和掉落物理对象。
![被抓取的物体](\image\4-6.jpg)
- Physics Thruster Component （物理推进器组件）：PhysicsThrusterComponent 适用于沿着 X 轴负方向施加特定物理作用力的对象（例如，您所推动的方向上的 X 点）。推力组件使用连续作用力，而且能通过脚本来自动激活、一般激活或取消激活。 
![物理推进](\image\4-7.jpg)
- Radial Force Component （径向力组件）：RadialForceComponent 用于发出径向力或脉冲来影响物理对象或可摧毁对象。与 PhysicsThrusterComponent 不同，这类组件会施加“发射后不用管”类型的作用力，而且并不持续。 
![径向力](\image\4-8.jpg)
### 7. 渲染组件
渲染组件影响游戏场景或物体如何渲染表现。
- Atmospheric Fog Component （大气雾组件）：AtmosphericFogComponents 用于创建雾化效果，如场景中的云或大气雾。该组件拥有几项可调整的设置，可以影响此效果在关卡中的生成方式。
>![密度衰减高度为0.5 (8 km)](\image\4-9.jpg) ![密度衰减高度为0.35 (2.744 km)](\image\4-10.jpg)
- Exponential Height Fog Component （指数高度雾组件）：ExponentialHeightFogComponent 用于创建雾化效果，而其密度与雾的高度相关。指数级高度雾在地图中较低的地方产生密度较大的雾，在较高的地方产生密度较小的雾。随着您增加高度，雾会进行平滑的过渡，您不会看到明显的切换效果。
![指数高度雾](\image\4-11.jpg)
- Decal Component （贴花组件）:DecalComponent 是一个被渲染到网格模型表面上的材质（一种适用于模型的“保险杠标贴”）。贴花组件可用于任何目的，如发射子弹时在墙上撞出的痕迹，车辆在道路上擦出的打滑印记，被击中时在地上溅出的血迹等（下面有一个相关的示例）。 
![贴花](\image\4-12.jpg)
- Text Render Component （字体渲染组件）:TextRenderComponent 可以用指定的字体渲染世界中的文本。其中包含与常用字体有关的属性，如 Scale、Alignment、Color 等。
![字体渲染](\image\4-13.jpg)
- Vector Field Component （向量场组件）:VectorFieldComponent 用于引用 Vector Field，这是一种带有速度向量网格的 3D 容器，可用于确定 GPU 子画面的速度或加速度。 向量场可用于场景中的小规模效果（如强风粒子效果）和大规模效果（如暴雪）。
![强风粒子](\image\4-14.jpg)
- Billboard Component （看板组件）:BillboardComponent 是一个会被渲染为始终朝向摄像机的 2D 贴图，其功能与 ArrowComponent 类似，可用于某种放置方法且能够轻松选取。
- Post Process Component （后处理组件）:PostProcessComponets 可以为 Blueprints 开启后处理控制。它将使用一个父级 UShapeComponent 来提供体积数据（如可用）。这类组件可以在某一场景应用了后处理设置时变换场景的色调。