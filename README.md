# Banking-app// Course:  CS213 - Programming II  - 2018
// Title:   Assignment I Problem 2
// Program: Problem 2
// Purpose: New Declaration for Operators Overloading
// Author 1:  Karim Mohamed Abdelfattah
// Author 2:  Karim Mahmoud Mosaed
// Author 1:  Abdelaziz Mohamed Abdelaziz
// Date:    11 Oct 2018
// Version: 1.0


#include <iostream>
#include <iomanip>
#include <valarray>

using namespace std;


class matrix
{
private:
    valarray<int> data;       //valarray that will simulate matrix
    int row, col;

public:
     void setr(int r)
    {
        row=r;
    }
    int getr()
    {
        return row;
    }
    void setc(int c)
    {
        col=c;
    }
    int getc()
    {
        return col;
    }

    void createMatrix (int row, int col, int num[], matrix& mat)
{
    mat.row = row;
    mat.col = col;
    mat.data.resize (row * col);
    for (int i = 0; i < row * col; i++)
        mat.data [i] = num [i];
}

        matrix(){};

//Addition two matrices

    matrix operator+ ( matrix y)
    {
        matrix z;
        if(col==y.col&&row==y.row)
        {
            z.data.resize(data.size());
            for(int i=0 ; i < y.data.size(); i++)
            {
                z.data[i]=data[i]+y.data[i];
            }
        }
        else
            cout<<"Error The Matrices aren`t The Same Size ";
        return z;
    }

// Subtraction Two Matrices

    matrix operator- ( matrix y)
    {
        matrix z;
        if(col==y.col&&row==y.row)
        {
            z.data.resize(data.size());
            for(int i=0 ; i < y.data.size(); i++)
            {
                z.data[i]=data[i]-y.data[i];
            }
        }
        else
            cout<<"Error The Matrices aren`t The Same Size ";
        return z;
    }

//Multiplication of Two matrices

    matrix operator* ( matrix y)
    {
        matrix z;
        z.data.resize(row*y.col);
        if(col==y.row)
        {
            int x=0;
            for(int i=0 ; i<(row*2) ; i+=2)
            {
                for(int j=0 ; j<y.col ; j++)
                {
                    z.data[x]=(data[i]*y.data[j])+(data[i+1]*y.data[j+y.col]);
                    x++;
                }
            }
        }
        else
        {
            cout<<"Error The Matrices cant`t be multiplied ";
        }
        return z;
    }

// Addition of  Matrix and Number

    matrix operator+ ( int x )
    {
        matrix z;
        z.data.resize(data.size());
        for(int i=0 ; i < data.size(); i++)
        {
            z.data[i]=data[i]+x;
        }

        return z;


    }
// Subtraction of Matrix and Number

    matrix operator- ( int x )
    {
        matrix z;
        z.data.resize(data.size());
        for(int i=0 ; i < data.size(); i++)
        {
            z.data[i]=data[i]-x;
        }

        return z;


    }
//Multiplication of matrix and Number

    matrix operator* ( int x )
    {
        matrix z;
        z.data.resize(data.size());
        for(int i=0 ; i < data.size(); i++)
        {
            z.data[i]=data[i]*x;
        }

        return z;

    }
};

void createMatrix (int row, int col, int num[], matrix& mat);

int main()
{
    int data1 [] = {1,2,3,4,5,6,7,8};
    int data2 [] = {13,233,3,4,5,6};
    int data3 [] = {10,100,10,100,10,100,10,100};
    //int data4 [100]={0};

    matrix mat1, mat2, mat3, mat4;
    mat1.createMatrix(4, 2, data1, mat1);
    mat2.createMatrix (2, 3, data2, mat2);
    mat3.createMatrix (4, 2, data3, mat3);
    //createMatrix (4, 2, data4, mat4);

    return 0;
}


