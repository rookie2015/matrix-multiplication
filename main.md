#include <iostream>
#include <iomanip>
#include "functions.h"
using namespace std;

int main()
{
	int ** matrix1, matrix1_numofRows, matrix1_numofColumns;
	int ** matrix2, matrix2_numofRows, matrix2_numofColumns;
	int ** result;

	cout << "Welcome to the matrix multiplication calcultor! " << endl;
	cout << "Please enter the number of rows and columns for the 1st matrix : ";
	cin >> matrix1_numofRows >> matrix1_numofColumns;
	
	cout << "Please enter the number of rows and columns for the 2nd matrix : ";
	cin >> matrix2_numofRows >> matrix2_numofColumns;
	
	matrix1 = new int *[matrix1_numofRows];//create rows of the matrix1
	for (int Rows = 0; Rows < matrix1_numofRows; Rows++)
		matrix1[Rows] = new int [matrix1_numofColumns];//create the columns of the matrix1

	matrix2 = new int *[matrix2_numofRows];//create rows of the matrix1
	for (int rows = 0; rows < matrix2_numofRows; rows++)
		matrix2[rows] = new int[matrix2_numofColumns];//create the columns of the matrix1

	if (matrix1_numofColumns != matrix2_numofRows)
		cout << "Invaild matrix multiplication, please try again." << endl;
	else
	{	
		matrix1_getElements(matrix1_numofRows, matrix1_numofColumns, matrix1);
		matrix2_getElements(matrix2_numofRows, matrix2_numofColumns, matrix2);
		cout << "Here is the 1st Matrix that you entered: " << endl;
		displayMatrix(matrix1, matrix1_numofRows, matrix1_numofColumns);	
		cout << "Here is the 2nd Matrix that you entered: " << endl;
		displayMatrix(matrix2, matrix2_numofRows, matrix2_numofColumns);
	}
	result = new int *[matrix1_numofRows];
	for (int r = 0; r < matrix1_numofRows; r++)
		result[r] = new int[matrix2_numofColumns];//create the columns of the new matrix

	matrixAfterMultiply(matrix1, matrix2, result, matrix1_numofRows, matrix1_numofColumns, matrix2_numofColumns);
	
	deleteArrays(matrix1, matrix1_numofRows);
	deleteArrays(matrix2, matrix2_numofRows);
	deleteArrays(result, matrix1_numofRows);
	return 0;
}
