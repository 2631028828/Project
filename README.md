## Welcome to yxd137's Pages

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# 推箱子个人代码
#include <iostream>
#include<queue>
using namespace std;
char zmap[20][20];
int  jmap[20][20][20][20] = { 0 };
int n1, m1;
queue<int>q;
int n2, m2;
int n3, m3;
int n, m;
int  people[4][2] =
{
  {-1,0},
  {0,-1},
  {1,0},
  {0,1},
};
int OutMap(int a, int b)
{
	if (a >= 0 && a < n && b >= 0 && b < m && zmap[a][b] != '#')
		return 0;

	else
		return 1;
}
int bfs()
{
	int p1, p2, x1, x2;
	q.push(n2);
	q.push(m2);
	q.push(n3);
	q.push(m3);
	jmap[n2][m2][n3][m3] = 1;
	while (!q.empty())
	{
		p1 = q.front();
		q.pop();
		p2 = q.front();
		q.pop();
		x1 = q.front();
		q.pop();
		x2 = q.front();
		q.pop();
		if (x1 == n1 && x2 == m1)
			return jmap[p1][p2][x1][x2] - 1;
		for (int i = 0; i < 4; i++)
		{
			if (!OutMap(p1 + people[i][0], p2 + people[i][1]))
			{
				if (p1 + people[i][0] == x1 && p2 + people[i][1] == x2)
				{
					if (!OutMap(x1 + people[i][0], x2 + people[i][1]))
					{
						if (!jmap[p1 + people[i][0]][p2 + people[i][1]][x1 + people[i][0]][x2 + people[i][1]])
						{
							jmap[p1 + people[i][0]][p2 + people[i][1]][x1 + people[i][0]][x2 + people[i][1]] = jmap[p1][p2][x1][x2] + 1;
							q.push(p1 + people[i][0]);
							q.push(p2 + people[i][1]);
							q.push(x1 + people[i][0]);
							q.push(x2 + people[i][1]);
						}
					}
				}
				else
				{
					if (!jmap[p1 + people[i][0]][p2 + people[i][1]][x1][x2])
					{
						jmap[p1 + people[i][0]][p2 + people[i][1]][x1][x2] = jmap[p1][p2][x1][x2] + 1;
						q.push(p1 + people[i][0]);
						q.push(p2 + people[i][1]);
						q.push(x1);
						q.push(x2);
					}
				}

			}
		}
	}
	return -1;
}
int main()
{
	cin >> n >> m;
	for (int i = 0; i < n; i++)
		for (int j = 0; j < m; j++)
		{
			cin >> zmap[i][j];
			if (zmap[i][j] == '@')
			{
				n1 = i; m1 = j;
			}
			if (zmap[i][j] == 'X')
			{
				n2 = i; m2 = j;
			}
			if (zmap[i][j] == '*')
			{
				n3 = i; m3 = j;
			}
		}
	int k;
	k = bfs();
	cout << k;
}
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/2631028828/Project/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.
