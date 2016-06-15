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

##向游戏对象发送消息
```
	public GameObject receiver;
	void Start () {
		//向本脚本所属的游戏对象发送ShowNumber消息并传递参数100
		receiver.SendMessage("ShowNumber",100,SendMessageOptions.DontRequireReceiver);
	}
```
##创建游戏对象
```
if (GUILayout.Button("创建立方体", GUILayout.Height(50)))
{
    //设置该模型默认为立方体
    GameObject obj = GameObject.CreatePrimitive(PrimitiveType.Cube);
    //为对象添加一个刚体，赋予物理属性
    obj.AddComponent<Rigidbody>();
    //赋予对象的材质红色
    obj.GetComponent<Renderer>().material.color = Color.red;
    //设置对象的名称
    obj.name = "Cube";
    //设置此模型材质的位置坐标
    obj.transform.position = new Vector3(0, 5f, 0);
}
```
##获取游戏对象
- 通过指定 代码声明公开游戏对象，然后在inspector属性栏中指定
```
//例如
public GameObject obj;
```
- 通过对象名获取对象
```
//查找只需要名字即可
obj = GameObject.Find("Cube");
```
##克隆预制体

unity的xyz坐标系是左手坐标，x是屏幕左右，y是屏幕上下，Z是屏幕里外

##习题
onGUI做一个类调查问卷    
创建球体 并通过键盘wasd进行移动控制  （完成）
```
using UnityEngine;
using System.Collections;

public class hw1_3 : MonoBehaviour {

    public GameObject sphere;
    void Update()
    {
        //按下键盘W键
        if (Input.GetKeyDown(KeyCode.W))
        {
            sphere.transform.Translate(new Vector3(0f, 0.5f, 0f));
        }
        if (Input.GetKeyDown(KeyCode.A))
        {
            sphere.transform.Translate(new Vector3(-0.5f, 0f, 0f));
        }
        if (Input.GetKeyDown(KeyCode.S))
        {
            sphere.transform.Translate(new Vector3(0f, -0.5f, 0f));
        }
        if (Input.GetKeyDown(KeyCode.D))
        {
            sphere.transform.Translate(new Vector3(0.5f, 0f, 0f));
        }
    }
}

```






