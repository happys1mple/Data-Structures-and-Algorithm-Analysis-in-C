# Trees（树）

## 预备知识：

定义树的一种自然的方式是递归方式。

从递归定义中我们发现，一棵树是N个节点和N-1条边的集合，其中一个节点叫做根。

路径（path）：节点n1，n2，…,nk的一个序列。

路径的长（length）：改路径上边的条数。

深度（depth）：从根到 ni的唯一路径的长。



### 树的实现

树的节点声明

```c
typedef struct TreeNode *PtrToNode;

struct TreeNode
{
	ElementType Element;
	PtrToNode FirstChild;
	PtrToNode NextSibling;
}
```

由于每个节点的儿子数可以变化很大并且事先不知道，因此在数据结构中建立到个儿子节点的直接链接是不可行的，<u>应为这样会浪费太多的空间。</u>

**解法：**将每个节点的所有儿子都放在树节点的链表中



### 树的遍历及应用

1.用于常用操作系统中的目录结构。

**例：**列出目录中所有文件的名字。

```c
static void ListDir(DirectoryOrFile D, int Depth)
{
	if(D is a legitimate entry)
	{
		PrintName(D, Depth);
		if(D is a directory)
			for each child, C, of D
					ListDir(C, Depth+1);
	}
}
void ListDirectory(DirectoryOrFile D)
{
	ListDir(D,0);
}
```

**列出分级文件系统中目录的例程**

