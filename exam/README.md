### Огромное спасибо
- https://github.com/vyragosa/OOP-exam-questions
- https://github.com/po4yka/university-notes/blob/master/2%20course/%D0%9E%D0%9E%D0%9F/theory.md
- https://drive.google.com/file/d/1vVSHTY6vrBenuqdAqJpRjcaCi7CkPXAS/view

# Теория
## 1. Аргументы, передаваемые функции по умолчанию
Иногда в функцию нужно указать аргументы (параметры), которые могут принимать дефолтные значения (например 0). В данном случае их можно не указывать при вызове функции. Аргументы по умолчанию объявляются в прототипе функции. Как правило при объявлении классов, эти аргументы объявляются в конструкторе (а если быть точнее в прототипе/заголовке, не в теле/реализации). 

Особенности аргументов по умолчанию:
- Можно не указывать при вызове функции, потому что они добавляются компилятором автоматически (пример, b = 0)
- Объявляются в прототипе функции, причем **ПОСЛЕДНИМИ**, то есть **ПОСЛЕ** тех аргументов у которых нет значений по умолчанию (иначе возникнет ошибка компиляции)
- Чтобы использовать аргументы по умолчанию, эта функция должна быть соответствующим образом объявлена

Преимущества аргументов по умолчанию:
- сокращается листинг программного кода за счет избежания лишних функций, которые выполняют ту же работу только с другими значениями аргументов
- обеспечивается простой, естественный и эффективный стиль программирования;
- аргументы = сокращенной формой "перегрузки" функции. Улучшает читабельность кода и упрощает вызов функции.

Во время объявления функции, аргументы по умолчанию задаются только 1 раз. Здесь возможны 2 случая:
1. Случай, если функция имеет прототип и реализацию.
2. Случай, если функция не имеет прототипа, а имеет только реализацию.

## 2. Архитектура системы. Иерархия объектов.
**Архитектура** – это набор значимых решений по поводу организации **системы** программного обеспечения, набор структурных элементов и их интерфейсов, при помощи которых компонуется **система**

**Архитектура системы** так или иначе строится путем создания **иерархии** объектов и взаимодействия между объектами.

**Объектная декомпозиция** - разбиение системы на объекты. Такая декомпозиция существенно упрощает конструирование сложных систем. Разработка интерфейсов взаимодействия происходит между объектами системы и внешней средой. Способ организации интерфейса зависит от особенности объекта и его назначения. Схематически это представлено на следующем:

![системка](https://github.com/mireashik/oop_2sem/assets/123753819/3688e049-3a0a-4a80-905c-69344bd54508)

## 3. Ввод-вывод в С++. Потоки.
В С++ нет встроенных средств ввода-вывода, поэтому поточный ввод-вывод выполняется с помощью функций сторонних библиотек (**stdio.h** и **iostream**)

Библиотекой **iostream** определено 2 типа:
- istream (поток ввода)
- ostream (поток вывода)

**Поток** - последовательность символов, которая записывается на устройство ввода или считывается с него (например консоль). 
<br>
Для **записи / вывода** символов на консоль - объект `cout`, для **чтения** - объект `cin`. Есть еще `cerr` - объект потока вывода сообщений об **ошибках**

Для выполнения операций ввода-вывода переопределены две операции поразрядного сдвига:
<br>
`>>` - получить из входного потока
<br>
`<<` - поместить в выходной поток

Ввод информации: из входного потока читается последовательность символов до пробела, затем эта последовательность преобразуется к типу идентификатора, и получаемое значение помещается в **идентификатор**

**Вывод информации: определяется тип данных переменной**, подлежащей выводу, и выбирается соответствующий оператор вставки потока для отображения значения. Оператор << перегружен для вывода элементов данных встроенных типов и значений указателя

Работа с файлами: функционал для работы с ними предоставляет заголовочный файл fstream.
<br>
Там определены 2 класса:
- ifstream
- ofstream

Реализующие возможности чтения и записи информации

## 4. В чем различие между ссылкой и указателем?
Указатель – переменная, значением которой является адрес ячейки памяти.
<br>
Ссылки – переменная, с особым типом данных, являющийся скрытой формой указателя, значение которой автоматически разыменовывается.

Различия:
- Указатель хранит адрес объекта, ссылка ссылается на него напрямую (скрыто хранит указатель)
- Ссылка, в отличии от указателя, не может быть неинициализированной (она обязательно указывает на какой-то объект)
- Ссылка не может быть изменена после инициализации
- У ссылки нет адреса (это просто другое имя для того же объекта)
- Существует арифметика указателей, но нет арифметики ссылок
- Инициализировать неконстантную ссылку константным объектом нельзя
- Нельзя напрямую изменить значение по константной ссылке, тем не менее мы можем изменить сам объект

```c++
int a; // переменная по адресу 0xdd000075
int &ra = a; // ссылка, которая ссылается на переменную а (по факту просто другое имя переменной, их значения одинаковые)

cout << &a; // 0xdd000075
cout << &ra; // 0xdd000075
```

```c++
int a = 3;
int b = 5;
int &ra = a; // ссылка, которая ссылается на переменную а (по факту просто другое имя переменной, их значения одинаковые
int *p = &a; // указатель содержащий ардес переменной a
p = &b; // указатель получает адрес переменной b
    
cout << *p; // 5
cout << endl;
cout << ra; // 3
```

### **Арифметика указателей**
Адрес указателя можно увеличить и уменьшать на значение равное размеру типа указателя (количеству байтов)

- double = 8
- int = 4
- short = 2
- char = 1

После изменения адреса мы можем получить значение, которое находится по новому адресу, однако это значение может быть неопределенным

Чтобы использовать свойства и методы **объекта** через указатель, необходимо использовать `->` вместо `.`

## 5. Виртуальные базовые классы

> Как известно, в С++ ключевое слово virtual используется для объявления виртуальных функций, которые будут переопределены в производных классах (СМОТРИТЕ БИЛЕТ 61)

**Виртуальный базовый класс** - решение так называемой проблемы ромба, когда существует 2 копии базового класса - по одной для каждого наследника.
<br>
Иногда желательно, чтобы частью обоих классов наследников была 1 базового класса

Ромбовидное наследование — вид множественного наследования, когда 2 класса B и C наследуют от A, а класс D наследует от обоих классов B и C. При этой схеме может возникнуть неоднозначность: если объект класса D вызывает метод, определенный в классе A (и этот метод не был переопределен в классе D), а классы B и C **по-своему** переопределили этот метод, то от какого класса его наследовать: B или C? 

![изображение](https://github.com/mireashik/oop_2sem/assets/123753819/f93b5579-0ac3-4f77-add9-0647baf4529e)

При использовании `virtual` существует только 1 базовый объект. Этот базовый объект используется всеми объектами в дереве наследования и создается только 1 раз.

Встретив ключевое слово virtual, компилятор помечает, что для этого метода должно использоваться позднее связывание: для начала он создает для класса таблицу виртуальных функций, а в класс добавляет новый скрытый для программиста член — указатель на эту таблицу

```c++
// Пример ошибки ромба
class BaseClass {
    public:
    int num;
};

class ParentClass1: public BaseClass{};

class ParentClass2: public BaseClass{};

class ChildClass: public ParentClass1, public ParentClass2 {};

int main() {
   ChildClass obj;
   obj.num = 1; // Ошибка! неявное имя переменной
   return 0;
}
```

### Есть 2 способа решения проблемы
```c++
// Оператор разрешения области видимости :: позволяет явно выбрать вариант производного класса.
// Однако данный способ решения порождает проблемы: Что если нужна лишь 1 копия объекта, дублирование недопустимо
obj.ParentClass1::num = 1;
```

```c++
class BaseClass {
    public:
    int num;
};
// Как видим, перед именем базового класса в спецификации производного класса стоит ключевое слово virtual
class ParentClass1: virtual public BaseClass {};

class ParentClass2: virtual public BaseClass {};

// Теперь оба класса являются наследниками виртуального класса BaseClass, и любые их наследники будут содержать лишь 1 копию базового класса
// Следовательно, выражение obj.num = 1 становится однозначным
class ChildClass: public ParentClass1, public  ParentClass2 {};

int main() {
   ChildClass obj;
   obj.num = 1;
   return 0;
}
```

![5](https://github.com/mireashik/oop_2sem/assets/123753819/0d168ff0-3575-4582-9653-d329961bf67e)
![6](https://github.com/mireashik/oop_2sem/assets/123753819/f4cf4e1b-cd10-4f7c-b4e6-26816b7733a2)
![7](https://github.com/mireashik/oop_2sem/assets/123753819/364f67b7-102c-41c2-9128-a329f34e7141)
![8](https://github.com/mireashik/oop_2sem/assets/123753819/eb1b1099-63ea-4d55-92ca-f1dd4492369e)
![9](https://github.com/mireashik/oop_2sem/assets/123753819/d530da4e-3715-4a28-9fdb-0fbec67cbe43)
![10](https://github.com/mireashik/oop_2sem/assets/123753819/379cfda9-b559-4dfc-823a-9dc0d664131a)
![11](https://github.com/mireashik/oop_2sem/assets/123753819/eca8c124-a6e9-4c95-8454-c8713edcacbb)
![12](https://github.com/mireashik/oop_2sem/assets/123753819/b533bccf-f785-4f3a-a759-f795949dd75b)
![13](https://github.com/mireashik/oop_2sem/assets/123753819/0bb02cbd-d49f-489f-b4c0-a067144c4630)
![14](https://github.com/mireashik/oop_2sem/assets/123753819/10182a31-6154-40ef-b2a3-311377766945)
![15](https://github.com/mireashik/oop_2sem/assets/123753819/d7241c21-2714-45a4-84dd-fc8cb0953edc)
![16](https://github.com/mireashik/oop_2sem/assets/123753819/68fa5e8f-5a6e-4b77-b4d4-252ca2e0c004)
![17](https://github.com/mireashik/oop_2sem/assets/123753819/9913bed2-2997-4176-8e7d-47b96e97dc34)
![18](https://github.com/mireashik/oop_2sem/assets/123753819/9f51e14a-7ef5-4c17-ac12-6f87f4d8fb32)
![19](https://github.com/mireashik/oop_2sem/assets/123753819/6600ea6e-2131-4711-9f3b-e9714611d8e9)
![20](https://github.com/mireashik/oop_2sem/assets/123753819/422299b0-15e0-461b-ba8a-a0f2d337f94f)
![21](https://github.com/mireashik/oop_2sem/assets/123753819/59c0d306-8687-4ba3-b671-96149a05f45e)
![22](https://github.com/mireashik/oop_2sem/assets/123753819/5ae10d17-31d7-439c-b27c-73a4c4e32c8c)
![23](https://github.com/mireashik/oop_2sem/assets/123753819/dfe59b37-df1c-43f6-adb8-0d46ee36f34a)
![24](https://github.com/mireashik/oop_2sem/assets/123753819/c063f5e5-f6df-4251-885f-e4659fc0403a)
![25](https://github.com/mireashik/oop_2sem/assets/123753819/55d55aae-94d9-427c-9b2b-5679c5f4552e)
![26](https://github.com/mireashik/oop_2sem/assets/123753819/6da85700-bde0-45d0-9ab4-0ab50563671b)
![27](https://github.com/mireashik/oop_2sem/assets/123753819/9fc23cfb-0ab7-43c2-be24-6e2d18fba19f)
![28](https://github.com/mireashik/oop_2sem/assets/123753819/41537064-bd1d-4f3f-9c25-48114e428b25)
![29](https://github.com/mireashik/oop_2sem/assets/123753819/c3c9096e-c29f-43c9-b66f-793f8b16fc5d)
![30](https://github.com/mireashik/oop_2sem/assets/123753819/0828b98d-bf50-49c8-a8b9-442ee8394aa5)
![30](https://github.com/mireashik/oop_2sem/assets/123753819/daccc7f2-6c7a-4238-8768-45f70a279c76)
![31](https://github.com/mireashik/oop_2sem/assets/123753819/af7eeb2a-659d-497f-88fc-0abc175cfd79)
![32](https://github.com/mireashik/oop_2sem/assets/123753819/92f6f779-4f42-4b56-8d37-e1f03a860576)
![33](https://github.com/mireashik/oop_2sem/assets/123753819/77bc5c62-77ca-45d5-9af9-8903875840e7)
![34](https://github.com/mireashik/oop_2sem/assets/123753819/8fdea623-267f-495a-92ad-03fd53a7bfc5)
![35](https://github.com/mireashik/oop_2sem/assets/123753819/99ad79bd-efba-4782-a5cf-77b74926f6d3)
![36](https://github.com/mireashik/oop_2sem/assets/123753819/3bf0f5aa-74da-49c6-a723-b822006bb1fa)
![37](https://github.com/mireashik/oop_2sem/assets/123753819/48962adb-e662-4a80-a285-7715b35dd487)
![38](https://github.com/mireashik/oop_2sem/assets/123753819/a8664076-185c-4236-8e6c-2e5092410f57)
![39](https://github.com/mireashik/oop_2sem/assets/123753819/5983300b-d41b-4595-b1ae-316f9f82cfa2)
![40](https://github.com/mireashik/oop_2sem/assets/123753819/0a9c2d4d-794a-4922-9e79-a48b76d58986)
![41](https://github.com/mireashik/oop_2sem/assets/123753819/fcbb1ca0-7b35-4ced-98a1-dce8631b7c5d)
![42](https://github.com/mireashik/oop_2sem/assets/123753819/df0b0b78-5b21-4aaa-a308-31ddac82d9b0)
![43](https://github.com/mireashik/oop_2sem/assets/123753819/3327a53d-3a4c-4e77-ad0a-d1c3dcde557f)
![44](https://github.com/mireashik/oop_2sem/assets/123753819/b00ad65d-b8b0-4d41-97ae-1c3f1438dd42)
![45](https://github.com/mireashik/oop_2sem/assets/123753819/62fad288-dc6d-4d30-99af-f16001253489)
![46](https://github.com/mireashik/oop_2sem/assets/123753819/3d574b01-dbfa-4086-97ae-810d022b9d47)
![47](https://github.com/mireashik/oop_2sem/assets/123753819/28b8e675-a10e-4f62-b477-d40620e63321)
![48](https://github.com/mireashik/oop_2sem/assets/123753819/b239e44a-5587-4439-8cd6-f1b7d089d79a)
![48](https://github.com/mireashik/oop_2sem/assets/123753819/83bff844-c1ce-48df-acbc-de5718725051)
![50](https://github.com/mireashik/oop_2sem/assets/123753819/1bb3f34d-e128-4074-8a29-fd23eb9e9b8f)
![51](https://github.com/mireashik/oop_2sem/assets/123753819/05780803-b9ef-40e3-8896-ad636e96944c)
![52](https://github.com/mireashik/oop_2sem/assets/123753819/355c36fb-62d8-410d-a636-5552649a7e0d)
![53](https://github.com/mireashik/oop_2sem/assets/123753819/0989ac4d-fc4d-4851-bead-ab765cd95869)
![54](https://github.com/mireashik/oop_2sem/assets/123753819/d6cab7e9-1971-4014-8714-7c0221b62bf3)
![55](https://github.com/mireashik/oop_2sem/assets/123753819/278805a8-7152-4a76-a71b-985ad4e628fb)
![56](https://github.com/mireashik/oop_2sem/assets/123753819/ef552601-8139-417f-8725-38c8ecee0c39)
![57](https://github.com/mireashik/oop_2sem/assets/123753819/50c3320a-981e-472c-8a03-1777bf870e3c)
![58](https://github.com/mireashik/oop_2sem/assets/123753819/30abd802-d631-4d30-bd78-9c5a92c86d50)
![59](https://github.com/mireashik/oop_2sem/assets/123753819/e6755aef-2b64-4b0b-8b28-71c8a9fe1cdd)
![60](https://github.com/mireashik/oop_2sem/assets/123753819/9dac7cf8-c4f3-4eb6-9b9d-c5ad86ccc59a)
![61](https://github.com/mireashik/oop_2sem/assets/123753819/dd81d8b3-2d5e-437b-b366-be811db72e3f)
![62](https://github.com/mireashik/oop_2sem/assets/123753819/ce182119-db4e-4b64-aced-25b92404f220)
![63](https://github.com/mireashik/oop_2sem/assets/123753819/030332c6-79e5-4ffd-8cba-3cccdb54e267)
![64](https://github.com/mireashik/oop_2sem/assets/123753819/8fa46cc8-2514-4978-a7a0-bb5e34607b46)
![65](https://github.com/mireashik/oop_2sem/assets/123753819/ef5aec72-7709-47c2-b990-1e8dfc9fd7ae)
![67](https://github.com/mireashik/oop_2sem/assets/123753819/113708e1-17b8-4ff6-af08-3ffdc9601301)
![68](https://github.com/mireashik/oop_2sem/assets/123753819/2660afea-a6d7-4538-8555-974957ece4da)
![69](https://github.com/mireashik/oop_2sem/assets/123753819/e451d7aa-0115-4406-91f4-709dc6dbc233)
![71](https://github.com/mireashik/oop_2sem/assets/123753819/67495f1f-6921-47db-995a-72f08c4bd23f)
![72](https://github.com/mireashik/oop_2sem/assets/123753819/bcfd6276-bb80-4280-a39f-c41972117a92)
![73](https://github.com/mireashik/oop_2sem/assets/123753819/3ca57a03-4966-44a9-a357-d6a45e213fb3)

# Практика
![74](https://github.com/mireashik/oop_2sem/assets/123753819/a05d6403-bdc7-4fd8-ba09-d187f8388604)
![75](https://github.com/mireashik/oop_2sem/assets/123753819/7dcc2a2e-b434-475c-ab19-a3677f3065a3)
![76](https://github.com/mireashik/oop_2sem/assets/123753819/eac7faed-5cfc-419b-8213-07489bb2e54b)
![77](https://github.com/mireashik/oop_2sem/assets/123753819/c1fe4210-feda-4dd1-baa3-71928339c0d4)
![78](https://github.com/mireashik/oop_2sem/assets/123753819/088b0569-8ae0-440e-901b-307aa808dbf9)
![79](https://github.com/mireashik/oop_2sem/assets/123753819/39aa5a88-64b6-40b7-8b5d-c3def5a6fe9f)
![80](https://github.com/mireashik/oop_2sem/assets/123753819/9e9ca898-7078-4687-a444-03dce05196c9)
![81](https://github.com/mireashik/oop_2sem/assets/123753819/d33417a4-82af-41c1-914a-0cafac6f0275)
![82](https://github.com/mireashik/oop_2sem/assets/123753819/fcb4435a-8041-4179-ae28-27ab6afd50ec)
![83](https://github.com/mireashik/oop_2sem/assets/123753819/d8d5c29f-71df-4af5-b01f-2d0550830bd4)
![84](https://github.com/mireashik/oop_2sem/assets/123753819/86d57fdb-d63c-4277-b207-99d2b5ccf6f7)
![85](https://github.com/mireashik/oop_2sem/assets/123753819/706e82ed-0eeb-4c24-831a-5f808305f997)
![86](https://github.com/mireashik/oop_2sem/assets/123753819/e229a184-7732-43b1-babe-b5c017bd5195)
![87](https://github.com/mireashik/oop_2sem/assets/123753819/b14fab75-f3bf-4828-84ea-cc83e92949e9)
![88](https://github.com/mireashik/oop_2sem/assets/123753819/fde6fb23-d962-4a71-ac10-4b1679b23140)
![89](https://github.com/mireashik/oop_2sem/assets/123753819/6e7b6b40-c685-4219-921b-c7c782ca1137)
![90](https://github.com/mireashik/oop_2sem/assets/123753819/c30f8605-4ce2-4a0b-914a-52aa4a2c121f)
![91](https://github.com/mireashik/oop_2sem/assets/123753819/cf2b2dec-0a31-44dc-b0e7-7a43d65c1a6a)
![92](https://github.com/mireashik/oop_2sem/assets/123753819/fe74e4c0-57b4-4fba-8a5d-596243682f0c)
![93](https://github.com/mireashik/oop_2sem/assets/123753819/6c8847dc-30be-4c11-bd89-e7e84a6812e3)
![94](https://github.com/mireashik/oop_2sem/assets/123753819/d273575d-3059-4b93-baae-2804f532d0ee)
![95](https://github.com/mireashik/oop_2sem/assets/123753819/39aad470-1c73-44c4-8ccd-9aff47178b62)
![96](https://github.com/mireashik/oop_2sem/assets/123753819/668ff827-b26c-468d-b581-e0bf40074846)
![97](https://github.com/mireashik/oop_2sem/assets/123753819/0f309455-97e6-477b-9591-13955697ed44)
![98](https://github.com/mireashik/oop_2sem/assets/123753819/59cb2ff4-0db2-463a-ba9c-f3f38de5a647)
![99](https://github.com/mireashik/oop_2sem/assets/123753819/2bc44d81-965c-45b7-9881-e2157b01a6ea)
![100](https://github.com/mireashik/oop_2sem/assets/123753819/6e58ecf6-c3a0-47fd-a9fa-a7103aaad978)
![101](https://github.com/mireashik/oop_2sem/assets/123753819/494534ab-4e06-40fc-b8c0-691c757fc321)
![102](https://github.com/mireashik/oop_2sem/assets/123753819/86446318-eb35-47e1-831c-0e6154115ee5)
![103](https://github.com/mireashik/oop_2sem/assets/123753819/0b8361d3-d05f-44af-b88c-56401f5086c8)



