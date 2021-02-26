    public class JvmComprehension { // на этом этапе происходит загрузка класса в Metaspace

        public static void main(String[] args) { // создание фрейма main в Stack memory
            int i = 1;                      // запись переменной i во фрейм main в Stack memory
            Object o = new Object();        // создается объект и помещается в heap; создается переменная о во фрейме main, которая ссылается на адрес в heap
            Integer ii = 2;                 // создается объект в heap и происходит запись ссылки в переменную ii во фрейме main в Stack memory
            printAll(o, i, ii);             // в Stack создается новый фрейм printAll, во фрейме создаются аргументы метода. Для i происходит копирование значения из соответствующей переменной, для ii и о - копируется ссылка на уже созданные объекты
            System.out.println("finished"); // создается фрейм, в который передается ссылка на объект String, после выполнения фрейм удалится, и т.к. это последняя инструкция в программе, остальные фреймы тоже будут удаляться по принципу LIFO. Память Stack будет очищена
        }

        private static void printAll(Object o, int i, Integer ii) {
            Integer uselessVar = 700;                   // создается объект в heap и происходит запись ссылки в переменную uselessVar во фрейме printAll в Stack memory
            System.out.println(o.toString() + i + ii);  // создается фрейм System.out.println и создается объект String в heap, ссылка на который передается во фрейм
        }
    }