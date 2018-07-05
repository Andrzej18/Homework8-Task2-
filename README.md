package Task2;
import java.util.ArrayList;
import java.util.List;
import java.util.Objects;
public class Task2 {
    public static void main(String[] args) {
        List<String> list = new ArrayList<String>();

        list.add("a1");
        list.add("a2");
        list.add(null);
        list.add("a3");
        list.add(null);
        list.add("a4");
        list.add(null);
        list.add(null);
        list.add(null);
        list.add("Rest");

        println("Items:");
        list.forEach(item -> println(item));

        // Remove null refs
        println("Items (after nulls removed):");
        boolean useJava8removeIf = false;
        if (useJava8removeIf) {
            list.removeIf(Objects::isNull);
        }
        else {
            println("Using our own helper.");
            list = ListHelper.removeNullReference(list);
        }

        list.forEach(item -> println(item));

    }

    static void println(String msg) {
        System.out.println(msg);
    }
    }
class ListHelper {
    public static List<String> removeNullReference(List<String> list) {
        List<String> newList = new ArrayList<>();

        list.forEach(item -> {
            if (item != null)
                newList.add(item);
        });

        return newList;
    }
}
