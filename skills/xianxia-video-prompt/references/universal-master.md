# 仙侠视频通用母版

通用母版是平台无关的内部导演级中间格式。它保存剧情、视觉、动作、声音和连续性事实，不包含平台按钮名、专属参数、素材引用语法或未经确认的能力上限。不得把 YAML 母版作为默认交付物；完成验收后必须填入 `prompt-template.md` 的固定输出骨架。

## 母版字段

```yaml
unit: {id: UNIT-001, narrative_goal: 叙事变化, target_duration: 建议时长或待定, aspect_ratio: 构图意图或待定}
state_in:
  characters: 人物位置、朝向、境界、伤势、服装
  artifacts: 法宝位置、形态、能量、完整度
  spells: 法术阶段、灵力颜色、残留效果
  environment: 场景、光源、破坏程度、天气与气机
assets:
  - {id: CH-001, purpose: 锁定人物身份与服装, inherit: 骨相/发型/服装, do_not_inherit: 姿态/背景/构图}
global_direction: {visual_style: 视觉材质与色彩, mood: 情绪与气机, camera_principle: 焦点与运动原则}
shots:
  - id: SH-001
    function: 叙事任务
    framing: 景别、机位、构图、焦点
    camera: 运镜起点、路径、速度、终点
    subject_action: 一个主导物理动作
    spell_action: 当前法术阶段与结果
    dialogue: 原台词、语气、自然语速
    light: 环境光、灵力光与人物受光
    sound: 环境、对白、同步音效
    transition: 可见或可听转接
locks: {must_keep: 人物/法宝/法术/轴线/剧情硬锁, avoid: 可验证禁止项}
state_out: {visible_end_state: 最后一帧状态, audio_tail: 声音尾巴, unresolved_action: 未完成动作或无}
```

## 规则

- 一个镜头只保留一个主导动作；复杂斗法拆成连续阶段。
- 使用物理动词和空间关系，不用“震撼、炸裂、电影感拉满”代替事实。
- 法术写清来源、媒介、轨迹、速度、接触、反制、结果和余波。
- 灵力与法宝发光必须成为场景光源并影响人物受光。
- 不为某个平台的字数提前删除关键状态。
- 未指定平台时使用平台无关措辞填充固定输出模板，不生成平台专属参数。

验收：遮去平台名称后，仍能理解谁在何处、做什么、如何拍、法术如何发生、声音是什么、最后停在哪里。
