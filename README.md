* Загружается информация о классе JvmComprehension подсистемой загрузчиков Application // ClassLoader,  в область памяти Metaspace
public class JvmComprehension {

* Вызываем метод main и в стеке (Stack Memory) создаётся фрейм
 public static void main(String[] args) {

1. В стеке будут храниться примитивы 1, а также ссылки на объекты, которые помещаются в heap(куча)
 int i = 1; 
 
2. Объект o будет храниться в куче, а ссылка на него в стеке 
        Object o = new Object(); 

3. Объект ii будет храниться в куче, а ссылка на него в стеке   
        Integer ii = 2; 

4. Вызывается метод printAll и в стеке создаётся ещё один фрейм printAll()
 printAll(o, i, ii); 
 В стеке во фрейме plrintAll() создаются ссылки на объекты o и ii, которые ссылаются на те же объекты, что и во фрейме main. Также в данном фрейме теперь хранится переменная int = 1
 private static void printAll(Object o, int i, Integer ii) 

5. Это объект нигде не используется и будет удалён сборщиком мусора, находится в heap
 Integer uselessVar = 700;

6. Создастся новый фрейм, где будет переменная i и ссылки на объект ii и строку o.toString() 
        System.out.println(o.toString() + i + ii); 
        
7. Создастся новый фрейм где будет ссылка на строку “готово” 
        System.out.println("готово"); // 7
 