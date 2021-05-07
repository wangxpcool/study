package cn.me.al2.sort;

import java.util.HashMap;
import java.util.Map;

public class quickSortTest {


    public static void main(String[] args) {

//        int s[] = {1,1,1,1,1};
//        int s[] = {0,1,3,8,10};
        int s[] = {8,3,1,0,10};
        Map []maps = new Map[s.length];

        for (int i=0;i<s.length;i++){
            System.out.print(s[i]);
            Map map = new HashMap<String,Object>();
            map.put("index",i);
            map.put("key",s[i]);
            maps[i]= map;
        }
        System.out.println();
        for (int i=0;i<s.length;i++){
            Map map = maps[i];
            System.out.println(map);
        }
        quickSort(maps,0,maps.length-1);

        System.out.println();
        for (int i=0;i<s.length;i++){
            Map map = maps[i];
            System.out.println(map);
        }

//        quickSort(s,0,s.length-1);
//        System.out.println();
//        for (int i:s){
//            System.out.print(i);
//        }

    }

    public static void quickSort(Map[] arr, int start, int end) {

        //当开始位置小于结束位置时（数组有数据）  进行排序  也就是递归入口
        if (start < end) {
            //首先找到基准数  作为比较的标准数  取数组开始位置   从哪里开始  用哪个数当标准数 这个就是标准数
            Map stard = arr[start];
            //记录需要进行排序的下标
            int low = start;
            int high = end;

            //循环比对比标准数大和小的数字
            while (low < high) {
                //如果标准数小于右边的数字  把右边的游标卡尺向左移动
                while (low < high && (Integer)(stard.get("key")) <= (Integer)(arr[high].get("key"))) {
                    high--;
                }
                //如果标准数大于 右边的数字
                //用低位数字替换右边数字
//                arr[low] = arr[high];
                Integer key = (Integer)(arr[high].get("key"));
                Integer index = (Integer)(arr[high].get("index"));
                arr[low].put("key",key);
                arr[low].put("index",index);
                //如果左边的数字比标准数小
                while (low < high && (Integer)(arr[low].get("key")) <= (Integer)(stard.get("key"))) {
                    low++;
                }
                //如果左边的数字比标准数大
                //用左边数字替换右边数字
//                arr[high] = arr[low];
                Integer key2 = (Integer)(arr[low].get("key"));
                Integer index2 = (Integer)(arr[low].get("index"));
                arr[high].put("key",key2);
                arr[high].put("index",index2);
            }
            System.out.println("排序后");
            for (int i=0;i<arr.length;i++){
                Map map = arr[i];
                System.out.println(map);
            }
            //把标准数赋给高或者低所在的元素
            arr[low] = stard;
            //处理所有比标准数小的数字
            quickSort(arr, start, low);
            //处理所有比标准数大的数字
            quickSort(arr, low + 1, end);
        }
    }



    public static void  sort(Map[]a ){

        for (int i = 0;i<a.length-1;i++){
            for (int j = i;j<a.length;j++){
                Integer valuea = (Integer)(a[i].get("key"));
                Integer valueb = (Integer)(a[j].get("key"));
                if (valuea>valueb){
                    a[i].put("key",valueb);
                    a[j].put("key",valuea);
                    Integer indexa = (Integer)(a[i].get("index"));
                    Integer indexb = (Integer)(a[j].get("index"));
                    a[i].put("index",indexb);
                    a[j].put("index",indexa);
                }
            }
        }

    }


}
