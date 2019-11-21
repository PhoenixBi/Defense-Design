# Defense-Design
first game of three classmate.

Hi, here is the first, simple game by three freshman of game developing. This is of course nothing flashy, but it don't refuse any possibilities.
We plan to develop it on Qt, though need to learn from now.

**Reference and Acknowledgements**:<br/>
https://qtguide.ustclug.org/<br/>
https://blog.csdn.net/satanzw/article/details/10418063

最终决定复刻王国保卫战塔防。

## 概要设计

### 系统总体设计

塔防游戏主要由以下几部分组成

- 地图（建塔位置、敌人移动路径）
- 塔（类型，费用，攻击方式，攻击伤害）
- 敌人（类型，移动速度，生命值）
- 难度（间隔时间，敌人数）
- 参数（生命值，金币数）

### 主要数据结构

```c++
class MainWindow
{
private:
	Ui::MainWindow *	ui;
	int	m_waves;	//波数
	int	m_playerHp;	//己方血量
	int	m_playrGold;	//资金
	bool	m_gameEnded;	//游戏是否结束
	bool	m_gameWin;	//是否胜利
    /*好像还需要维护屏幕上所有对象的表*/
}

class towerpostion
{
private:
	bool	m_hasTower;	//是否有塔
	QPoint	m_pos;	//位置信息
	QPixmap	m_sprite;	//置塔点图片
}

class tower
{
private:
	bool	m_attacking;	//是否正在攻击
	int	m_attackRange;	//射程
	int	m_damage;	//伤害
	int	m_fireRate;	//火力间隔

	Enemy *	m_chooseEnemy;	//选定的目标

	const QPoint	m_pos;	//位置
	const QPixmap	m_sprite;	//图
}

class bullet
{
private:
	const QPoint	m_startPos;	//子弹起始位置
	const QPoint	m_targetPos;	//子弹消失位置
	const QPixmap	m_sprite;	//子弹图片
	QPoint	m_currentPos;	//子弹现在位置
	Enemy *	m_target;	//目标
	int	m_damage;	//伤害值
}

class waypoint
{
private:
	const QPoint	m_pos;	//坐标
	WayPoint *	m_nextWayPoint;	//下一个路径点
}

class enemy
{
private:
    bool	m_active;	//敌人活动状态
	int	m_maxHp;	//敌人最大血量
	int	m_currentHp;	//目前血量
	qreal	m_walkingSpeed;	//移动速度

	QPoint	m_pos;	//位置
	WayPoint *	m_destinationWayPoint;	//下一个路径点

	const QPixmap	m_sprite;
}
```

### 模块

*主要由以下几个模块组成*

地图

操作菜单与帮助

地图设计


### 接口

### 逻辑

 - 交互
 	- 塔的建立（花费）与拆除（返现）

 - 塔对敌人的攻击

 - 敌人的出现时间与运动状态

 - 敌人受到攻击的影响

 - 敌人成功的效果

 - 游戏进度提示
 
 - 己方被入侵扣血
 
 - 成功失败效果


