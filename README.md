# reposit
public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}
Сначала происходит подгрузка  классов 
- Подгружается class JvmComprehension
Затем происходит Linking(связывание)
-Инициализируется psvm ; printAll
-подготовка примитивов в статических полях(int)
-связывание ссылок на другие классы(Integer,System,Object)
main(), system classes...  заносятся в Stack Memory
1 : int i заносится в  Stack Memory
2 : Object o заносится в heap Object-ов
3 : Integer ii заносится в heap Integer-ов
4 : printAll заносится в Stack Memory(создается фрейм в стеке)
5 : Integer uselessVar заносится в heap Integer-ов
6 : Создаётся новый фрейм в стеке, куда заносится  ссылка на o.toString() + i + ii
7 : Создаётся новый фрейм в стеке, куда заносится ссылка на  "finished"

  Недостижимые объекты удаляются
Достижимые объекты группируются по времени жизни (поколения).
Чем дольше объект живёт, тем реже проверяют, нужно ли его удалить
код выполняется построчно, методы компилируются в машинный код с помощью движка выполнения, движок состоит из интерпритатора, JIT компилятора и сборщика мусора

