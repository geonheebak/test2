## 배열을 쉽게 주고받기 위한 방법을 알려주고 싶어서 이 글을 쓰게 되었다. 처음하는 C언어/C++을 접하는 사람들은 많이 햇갈리는데, 3단계를 거치면 간단하다.

**(전역변수/배열을 사용하면 쉽지만, 전역배열을 사용하면 모든 함수와 변수에 영향을 끼쳐서 코드가 섞여버릴 수 가 있어서 전역배열/변수를 사용하지 않고 함수에 보내는 방법을 쓸 것이다.)**

**1. 먼저 main안에 배열을 선언한다**

int main()
{

	int v1[2], v2[3][3]; 
	
	return 0;
	
}

**2. 함수를 생성 한 후 main안에 함수를 호출 한 후 1차원 배열, 2차원 배열을 배열의 선두주소를 함수 괄호 안에 넣는다.**

**ex)**

void func1()
{

}

int main()
{

	int v1[2], v2[3][3]; 
	
	func1(v1,v2);
	
}

**3. 함수옆에 괄호안에 넣어준 1차원, 2차원 베열을 func1의 괄호 안에 자료형을 붙혀서 그대로 넣어준다. (func1의 매개변수 안에 배열들을 넣어준다.)**

#include<iostream>

using namespace std;

void func1(int v1[2], int v2[3][3])

{

	

}

int main()

{

	int v1[2], v2[3][3];

	func1(v1, v2);

}

**아래는 입출력까지 완성된 코드이다.**

#include<*iostream*>

using namespace std;

void func1(int v1[2], int v2[3][3])
{

	for (int x = 0; x < 2; x++)

	{

		cin >> v1[x];

	}

	for (int y = 0; y < 3; y++)

	{

		for (int x = 0; x < 3; x++)

		{

			cin >> v2[y][x];


		}

	}

	for (int x = 0; x < 2; x++)

	{

		cout << v1[x];

	}

	cout << "\n";

	for (int y = 0; y < 3; y++)

	{

		for (int x = 0; x < 3; x++)

		{

			cout << v2[y][x];

		}

		cout << "\n";

	}

}

int main()
{

	int v1[2], v2[3][3];

	func1(v1, v2);

}

**안에 값을 넣은후 출력문 까지 완성한 문장이다 출력을 하면 1차원배열과 2차원 배열에 값을 넣은 후 출력을 하면 순차적으로 나온다.
이제 밑에 예제를 통해 제대로 이해했는지 확인하도록 하자**


## 예제 

#include <*iostream*>

using namespace std;

void func1(int a,int b[2],int c[3][3])
{

}

int main()

{
	int a = 0, b[2] = { 0 }, c[3][3] = { 0 };

	func1(a, b, c);

	return 0;

}


#### func1함수와 일반변수, 1차원 배열, 2차원 배열을 선언했다. 이제 함수에서 변수와 배열들에 숫자를 넣고 다시 main에서 출력할 것 이다.**

#include <iostream>

using namespace std;

void func1(int *a,int b[2],int c[3][3])

**여기서 함수안에 보내기위해 a에 포인터를 붙혀서 보내준다. main에 있는b[2], c[3][3]은 함수로 호출된 이상 이미 포인터가 붙혀져 있기 떄문에 그대로 써주면 된다.**

{

	cin >> *a;

	for (int x = 0; x < 2; x++)

	{

		cin >> b[x];

	}

	for (int y = 0; y < 3; y++)

	{

		for (int x = 0; x < 3; x++)

		{

			cin >> c[y][x];

		}

	}

	return;

}

int main()

{

	int a = 0, b[2] = { 0 }, c[3][3] = { 0 };

	

	func1(&a, b, c);

	cout << a << "\n";

	for (int x = 0; x < 2; x++)
	
	{

		cout << b[x];

	}

	cout << "\n";

	for (int y = 0; y < 3; y++)

	{

		for (int x = 0; x < 3; x++)

		{

			cout << c[y][x] << " ";

		}

		cout << "\n";

	}

	return 0;

}

