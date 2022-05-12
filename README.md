# understanding-JVM-challenge


public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1 int примитив создается в памяти стека (Stack Memory) фрейма метода main
        Object o = new Object();        // 2 создание объекта "о", оператором new выделается память в куче(heap) и с помощью контсруктора без параметров создается экземпляр класса Object, расположенный в выделенной области. Cсылка "o" на объект Object из heap помещается в Stack Memory. 
        Integer ii = 2;                 // 3 создается экземпляр класса Integer в heap. Ссылка на объект и его значение в области heap помещается в тот же фрейм main.
        printAll(o, i, ii);             // 4 Создается новый фрейм printAll() в Stack Memory, в него перадются ссылки на o, i, ii из heap
        System.out.println("finished"); // 7 Создается новый фрейм в Stack Memory. В данный фрейм передается ссылка на экземпляр класса String с содержимым "finished", расположенный в heap.
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 В созданном ранее фрейме printAll() помещается ссылка uselessVar на эземпляр класса Integer и его значение расположенные в heap.
        System.out.println(o.toString() + i + ii);  // 6 Создается новый фрейм System.out.println() в Stack Memory. В него помещаются ссылки на "i", "ii" и ссылка на новый объект полученный при вызове toString. 
    }
}
