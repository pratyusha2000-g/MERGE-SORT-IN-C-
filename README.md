# MERGE-SORT-IN-C++
#include <iostream>
using namespace std;

void mergeofarrays(int a[], int low, int mid, int high)
{
  int i = low, j = mid + 1, index = low, b[100], k;
  while ((i <= mid) && (j <= high)) 
  {
    if (a[i] < a[j]) 
    {
      b[index] = a[i];
      i++;
    }
    else 
    {
      b[index] = a[j];
      j++;
    }
    index++;
  }
 
  if (i > mid)
  {
    while (j <= high) 
      b[index++] = a[j++];
  } 
  else 
  {
    while (i <= mid) 
      b[index++] = a[i++];
     
  }
  for (k = low; k < index; k++) 
  {
    a[k] = b[k];
  }
}
void mergesort(int a[], int low, int high)
{
  if (low < high) 
  {
    int mid = (low + high) / 2; 
    mergesort(a, low, mid); 
    mergesort(a, mid+1, high); 
    mergeofarrays(a, low, mid, high); 
  }
}
int main() {
  int n,i;
  cout<<"Enter the number of terms \n";
  cin>>n;
  int a[n];
  cout<<"Enter "<<n<<" Numbers \n";
  for(i=0;i<n;i++)
  cin>>a[i];
  mergesort(a, 0, n-1);
  for (int i = 0; i < n; i++) {
    cout << a[i] << " ";
  }
}
