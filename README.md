#pragma once
#include <iostream>
using namespace std;

void displayMatrix(int **, int, int);

void matrixAfterMultiply(int ** m1, int ** m2, int ** newMatrix, int row_matrix1, int column_matrix1, int column_matrix2)
{
	for (int rw = 0; rw < row_matrix1; rw++)
	{
		for (int cl = 0; cl < column_matrix2; cl++)
		{
			for(int s = 0; s < column_matrix1; s++)
				newMatrix[rw][cl] += m1[rw][s] * m2[s][cl];
		}			
	}
	cout << "After multiplication, your new matrix contains: " << endl;
	displayMatrix(newMatrix, row_matrix1, column_matrix2);
}

void matrix1_getElements(int row_matrix1, int column_matrix1, int ** m1)
{
	cout << "Please enter 1st matrix elements seprated by space: " << endl;
	for (int i = 0; i < row_matrix1; i++)
	{
		for (int j = 0; j < column_matrix1; j++)
			cin >> m1[i][j];
	}
	cout << endl;
}

void matrix2_getElements(int row_matrix2, int column_matrix2, int ** m2)
{
	cout << "Please enter 2nd matrix elements seprated by space: " << endl;
	for (int h = 0; h < row_matrix2; h++)
	{
		for (int k = 0; k<column_matrix2; k++)
			cin >> m2[h][k];
	}
	cout << endl;
}
void displayMatrix(int ** m1, int row_num, int column_num)
{
	for (int row = 0; row < row_num; row++)
	{
		for (int col = 0; col < column_num; col++)
			cout << setw(3)<< m1[row][col];	
		cout << endl;
	}
	cout << endl;
}
void deleteArrays(int** s, int rows)
{
	for (int r = 0; r < rows; r++)
		delete[] s[r];
}
