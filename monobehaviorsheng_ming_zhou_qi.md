# MonoBehavior生命周期

Awake()  创建时候  
start()  脚本激活状态执行，位于Awake（）后面  
update() 更新逻辑  
lateUpdate() 延迟更新函数  
fixupdate() 固定时间间隔更新  
onGUI（） 绘制界面  
onDestroy() 销毁  
onENable（） 激活脚本  
onDisable() 脚本禁用时候被调用   

建立脚本后需要将其拖至物体

**C#脚本改名字 选中按F2后输入,不需要输入.cs**

##onGUI函数的使用
```
void OnGUI()
{
    //用标签显示文本
    GUILayout.Label("请输入你的名字：");
    //用文本区域输入名字
    text = GUILayout.TextField(text);
    //
    if (GUILayout.Button("提交"))
    {
        myName = text;
    }
    //当myName不为空的时候，说明我们已经提交了名字，
    //则显示名字
    if (!string.IsNullOrEmpty(myName))
    {
        GUILayout.Label("提交成功，名字：" + myName);
    }

}
```

##习题
onGUI做一个类调查问卷    
创建球体 并通过键盘wasd进行移动控制  






