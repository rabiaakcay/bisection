# include <stdio.h>
# include <math.h>

double myFunction (double x, double c1, double c2, double c3, double c4)
{
  return(c1*x*x*x + c2*x*x + c3*x + c4);
}
int main()
{
  double c1,c2,c3,c4,x1,min,max,epsilon = 0.01,minpt,maxpt,x1pt;

  printf("\n Finding the root using bisection method \n");
  printf("\n Function is c1*(x^3)+c2*(x^2)+c3*(x^1)+c4 \n");
  printf("\n Please enter the values of c1, c2, c3, c4 : \n");
  scanf("%lf %lf %lf %lf",&c1, &c2, &c3, &c4);
  printf("\n Please enter min and max values for function : \n");
  scanf("%lf %lf",&min, &max);

  minpt=myFunction(min,c1,c2,c3,c4);
  maxpt=myFunction(max,c1,c2,c3,c4);

  if ( minpt*maxpt<0 )
  {
      x1=(min+max)/2;
  }
  else
  {
      printf("\n There is no root \n");
      return;
  }

  while ( (max-min)>epsilon )
  {
      minpt=myFunction(min,c1,c2,c3,c4);
      maxpt=myFunction(max,c1,c2,c3,c4);

      x1=(max+min)/2;
      x1pt=myFunction(x1,c1,c2,c3,c4);

      if ( x1pt*minpt<0 )
      {
          max=x1;
      }
      else
      {
          min=x1;
      }
  }
   printf("\n The root of equation is :%lf \n",x1);

   return 0;
}
