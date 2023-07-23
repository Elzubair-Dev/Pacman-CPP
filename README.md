# Pacman-CPP
A simple Pacman game using procedural paradigm with C++

 ## Code:
  
using namespace std;  
#include <iostream>  
#include <conio.h>  
enum Direction {Stop = 0 , Up , Right , Down , Left};  
struct Map { int Height, Width, FruitX[10], FruitY[10]; };  
struct Pac { int PacX, PacY; Direction Dir; };  
struct Law { int Score; bool Lose , Hit[10] , Excit[10]; };  
Map m; Pac p; Law l;  
void Setup()  
{  
	m.Height = 20;  
	m.Width = 60;  
	m.FruitX[0] = 2;   
	m.FruitY[0] = 3;  
	m.FruitX[1] = 14;  
	m.FruitY[1] = 3;  
	m.FruitX[2] = 8;  
	m.FruitY[2] = 11;  
	m.FruitX[3] = 5;  
	m.FruitY[3] = 18;  
	m.FruitX[4] = 20;  
	m.FruitY[4] = 7;  
	m.FruitX[5] = 22;  
	m.FruitY[5] = 15;  
	m.FruitX[6] = 41;  
	m.FruitY[6] = 11;  
	m.FruitX[7] = 43;  
	m.FruitY[7] = 18;  
	m.FruitX[8] = 49;  
	m.FruitY[8] = 5;  
	m.FruitX[9] = 58;  
	m.FruitY[9] = 14;  
	p.PacX = m.Width /2;  
	p.PacY = m.Height / 2;  
	l.Score = 0;  
	l.Lose = false;  
	for (int k = 0; k < 10; k++)  
	{  
		l.Hit[k] = false;  
		l.Excit[k] = true;  
	}  
}  
void Draw()  
{  
	system("cls");  
	for (int i = 0; i < m.Height; i++)  
	{  
		for (int j = 0; j < m.Width; j++)  
		{  
			if (j == 0 || j == m.Width - 1) cout << "█";  
			else if (i == 0 || i == m.Height - 1) cout << "■";  
			else if (i == p.PacY && j == p.PacX) cout << "G";  
			else if (i == m.FruitY[0] && j == m.FruitX[0])  
			{  
				if (l.Hit[0] == false)  
					cout << "o";  
				else cout << " ";  
			}  
			else if( i == m.FruitY[1] && j == m.FruitX[1])  
			{  
				if (l.Hit[1] == false)  
					cout << "o";  
				else cout << " ";  
			}   
			else if ( i == m.FruitY[2] && j == m.FruitX[2])  
			{  
				if (l.Hit[2] == false)  
					cout << "o";  
				else cout << " ";  
			}  
			else if ( i == m.FruitY[3] && j == m.FruitX[3])  
			{  
				if (l.Hit[3] == false)  
					cout << "o";  
				else cout << " ";  
			}  
				else if (i == m.FruitY[4] && j == m.FruitX[4])  
			{  
				if (l.Hit[4] == false)  
					cout << "o";  
				else cout << " ";  
			}  
				else if ( i == m.FruitY[5] && j == m.FruitX[5])  
			{  
				if (l.Hit[5] == false)  
					cout << "o";  
				else cout << " ";  
			}  
				else if ( i == m.FruitY[6] && j == m.FruitX[6])  
			{  
				if (l.Hit[6] == false)  
					cout << "o";  
				else cout << " ";  
			}  
				else if ( i == m.FruitY[7] && j == m.FruitX[7])  
			{  
				if (l.Hit[7] == false)  
					cout << "o";  
				else cout << " ";  
			}  
				else if ( i == m.FruitY[8] && j == m.FruitX[8])  
			{  
				if (l.Hit[8] == false)  
					cout << "o";  
				else cout << " ";  
			}  
				else if ( i == m.FruitY[9] && j == m.FruitX[9])   
			{  
				if (l.Hit[9] == false)  
					cout << "o";  
				else cout << " ";  
			}  
			else if (j == 5 && i <= 5 || j == 13 && i >= 11 && i <= 17 || j == 34 && i >= 7 && i <= 13 || j == 49 && i >= 9 && i <= 19 || j ==  56 && i >= 11 && i <= 17) cout << "█";  
			else if (i == 5 && j >= 8 && j <= 20 || i == 15 && j >= 2 && j <= 9 || i == 9 && j >= 20 && j <= 29 || i == 17 && j >= 29 && j <= 41 || i == 7 && j >= 44 && j <= 55) cout << "■";  
			else cout << " ";  
		}  
		cout << "\n";  
	}  
	cout << "Score : " << l.Score << "\n";  
}  
void Input()  
{  
	if (_kbhit())  
	{  
		char c = _getch();  
		switch (c)  
		{  
		case 'w': p.Dir = Up; break;  
		case 'd': p.Dir = Right; break;  
		case 's': p.Dir = Down; break;  
		case 'a': p.Dir = Left; break;  
		case 'p': p.Dir = Stop; break;  
		case 'x': exit(0); break;  
		default:  
			break;  
		}  
	}  
}  
void Move()  
{  
	switch (p.Dir)  
	{  
	case Stop:; break;  
	case Up: p.PacY--; break;  
	case Right: p.PacX++; break;  
	case Down: p.PacY++; break;  
	case Left: p.PacX--; break;  
	default:  
		break;  
	}  
	if (p.PacX == 0 || p.PacX == m.Width - 1 || p.PacY == 0 || p.PacY == m.Height - 1 || p.PacX == 5 && p.PacY <= 5 || p.PacX == 13 &&  p.PacY >= 11 && p.PacY <= 17 || p.PacX == 34 && p.PacY >= 7 && p.PacY <= 13 || p.PacX == 49 && p.PacY >= 9 && p.PacY <= 19 || p.PacX == 56 && p.PacY >= 11 && p.PacY <= 17 || p.PacY == 5 && p.PacX >= 8 && p.PacX <= 20 || p.PacY == 15 && p.PacX >= 2 && p.PacX <= 9 || p.PacY == 9 && p.PacX >= 20 && p.PacX <= 29 || p.PacY == 17 && p.PacX >= 29 && p.PacX <= 41 || p.PacY == 7 && p.PacX >= 44 && p.PacX <= 55 ) exit(0);  
	else if (p.PacX == m.FruitX[0] && p.PacY == m.FruitY[0])  
	{  
		if (l.Excit[0] == true)  
		{  
			l.Score += 10;  
			l.Hit[0] = true;  
			l.Excit[0] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[1] && p.PacY == m.FruitY[1])  
	{  
		if (l.Excit[1] == true)  
		{  
			l.Score += 10;  
			l.Hit[1] = true;  
			l.Excit[1] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[2] && p.PacY == m.FruitY[2])  
	{  
		if (l.Excit[2] == true)  
		{  
			l.Score += 10;  
			l.Hit[2] = true;  
			l.Excit[2] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[3] && p.PacY == m.FruitY[3])  
	{  
		if (l.Excit[3] == true)  
		{  
			l.Score += 10;  
			l.Hit[3] = true;  
			l.Excit[3] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[4] && p.PacY == m.FruitY[4])  
	{  
		if (l.Excit[4] == true)  
		{  
			l.Score += 10;  
			l.Hit[4] = true;  
			l.Excit[4] = false;   
		}  
	}  
	else if (p.PacX == m.FruitX[5] && p.PacY == m.FruitY[5])  
	{  
		if (l.Excit[5] == true)  
		{  
			l.Score += 10;  
			l.Hit[5] = true;  
			l.Excit[5] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[6] && p.PacY == m.FruitY[6])  
	{  
		if (l.Excit[6] == true)  
		{  
			l.Score += 10;  
			l.Hit[6] = true;  
			l.Excit[6] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[7] && p.PacY == m.FruitY[7])  
	{  
		if (l.Excit[7] == true)  
		{  
			l.Score += 10;  
			l.Hit[7] = true;  
			l.Excit[7] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[8] && p.PacY == m.FruitY[8])  
	{  
		if (l.Excit[8] == true)  
		{  
			l.Score += 10;  
			l.Hit[8] = true;  
			l.Excit[8] = false;  
		}  
	}  
	else if (p.PacX == m.FruitX[9] && p.PacY == m.FruitY[9])  
	{  
		if (l.Excit[9] == true)  
		{  
			l.Score += 10;  
			l.Hit[9] = true;  
			l.Excit[9] = false;  
		}  
	}  
	if (l.Score >= 100)  
	{  
		l.Score += 10;  
		cout << "- You Win! -_-  \n";  
		exit(0);  
	}  
}  
void main()  
{  
	Setup();  
	while (!l.Lose)  
	{  
		Draw();  
		Input();  
		Move();  
	}  
}    

## Screens:
  
![3--pacman-pro-1](https://github.com/Elzubair-Dev/Pacman-CPP/assets/104657152/00378b50-b0a8-4ef7-a63a-fb3a8952daf5)

![3--pacman-pro-2](https://github.com/Elzubair-Dev/Pacman-CPP/assets/104657152/9158eec6-07c2-4526-b0db-cc15b403213d)
  
![3--pacman-pro-3](https://github.com/Elzubair-Dev/Pacman-CPP/assets/104657152/2c766244-d57a-41cd-a230-a8455bc8a3e3)
  
![3--pacman-pro-4](https://github.com/Elzubair-Dev/Pacman-CPP/assets/104657152/9d2c613c-6d51-4e97-96d5-0e0303125505)
  
![3--pacman-pro-5](https://github.com/Elzubair-Dev/Pacman-CPP/assets/104657152/d6721733-29a8-4ce4-a1dc-4a0367acc3de)

## Buy me a Coffee:
  
if you want to support me
(https://www.buymeacoffee.com/zu698air)

## Done  
