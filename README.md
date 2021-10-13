-import java.util.Arrays;

public class SortAbsoluteValue {
    public static void main(String[] args) {
        int[] num = new int[] { -8, -5, -3, -1, 3, 6, 9 };
        int[] result = sortAbsolute(num);

        for (int i = 0; i < num.length; i++) {
            System.out.println(result[i]);
        }
    }

    private static int[] sortAbsolute(int[] num) {
        int size = num.length;
        if (num[0] >= 0)
            return num;
        if (num[size-1] < 0) {
            int[] temp = Arrays.copyOf(num, num.length);
            Arrays.sort(temp);
            return temp;
        }
        int[] result = new int[size];

        int i = 0;
        for (i = 0; i < size - 1; i++) {
            if (num[i] < 0 && num[i + 1] >= 0) {
                break;
            }
        }

        int left = i - 1;
        int right = i + 1;
        result[0] = num[i];
        int k = 0;
        while (left >= 0 && right < size) {
            if (Math.abs(num[left]) < num[right]) {
                result[++k] = num[left];
                left--;
            } else {
                result[++k] = num[right];
                right++;
            }
        
        while(left>=0) {
            result[++k] = num[left--];
        }
        while(right<size) {
            result[++k] = num[right++];
        }
        return result;
    }
}
