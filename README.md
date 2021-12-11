# findinMountainArray-1095-



public class Main{
    public static void main(String[] args){
        int[] arr = {1,2,3,4,13,2};
        int target = 13 ;
        System.out.println(ans(arr,target));
    }
    public static int ans(int[] arr,int target){
        int peak = peak(arr);
        int firstTry = binSea(arr,target,peak);
        if(firstTry!=-1){
            return firstTry;
        }
        else{
            int end = arr.length-1;
            int start = peak;
            return ordAgBin(arr,target,start,end);
        }
        
        
    }
    
    
    public static int peak(int arr[]){
        int start = 0;
        int end = arr.length-1;
        while(start<end){
            int mid = start + (end - start)/2;
            if (arr[mid]<arr[mid+1]){
                start = mid + 1;
            } 
            else{
                end = mid;
            }
        }
        return end;
    }
    public static int binSea(int[] arr,int target,int peak){
        int start = 0;
        int end = peak;
        while(start<=end){
            int mid = start + (end -start)/2;
            if(target<arr[mid]){
                end = mid -1;
            }
            else if(target>arr[mid]){
                start = mid + 1;
            }
            else{
                return mid;
            }
        }
        return -1;
    }
    public static int ordAgBin(int [] arr,int targ,int start,int end){
        if (arr[start]>arr[end]){
           // System.out.println("Descending sort");
        while(start<=end){
            int mid = start + ((end - start)/2);
            //System.out.println(mid);
            if (targ>arr[mid]){
                end = mid - 1;
            }
            else if(targ<arr[mid]){
                start = mid + 1;
            }
            else{
                return mid;
            }
        }
        return -1;
    }

        else{
         //   System.out.println("Ascending sort");

            while(start<=end){
                int mid = start + ((end - start)/2);
                //System.out.println(mid);
                if (targ>arr[mid]){
                    start = mid + 1;
                }
                else if(targ<arr[mid]){
                    end = mid - 1;
                }
                else{
                    return mid;
                }
            }
            return -1;
        }


}}
