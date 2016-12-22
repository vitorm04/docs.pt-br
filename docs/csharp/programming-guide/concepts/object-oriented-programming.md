---
title: "Programa&#231;&#227;o orientada a objeto (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Programa&#231;&#227;o orientada a objeto (c#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# oferece suporte completo para a programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.  
  
 *Encapsulamento* significa que um grupo de propriedades relacionadas, métodos e outros membros são tratados como uma única unidade ou um objeto.  
  
 *Herança* descreve a capacidade de criar novas classes com base em uma classe existente.  
  
 *Polimorfismo* significa que você pode ter várias classes que podem ser usadas intercambiavelmente, mesmo que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.  
  
 Esta seção descreve os seguintes conceitos:  
  
-   [Classes e objetos](#Classes)  
  
    -   [Membros de classe](#Members)  
  
         [Campos e propriedades](#Properties)  
  
         [Métodos](#Methods)  
  
         [Construtores](#Constructors)  
  
         [Destruidores](#Destructors)  
  
         [Eventos](#Events)  
  
         [Classes aninhadas](#NestedClasses)  
  
    -   [Modificadores de acesso e níveis de acesso](#AccessModifiers)  
  
    -   [Instanciação de Classes](#InstantiatingClasses)  
  
    -   [Classes static e membros](#Static)  
  
    -   [Tipos anônimos](#AnonymousTypes)  
  
-   [Herança](#Inheritance)  
  
    -   [Substituindo membros](#Overriding)  
  
-   [Interfaces](#Interfaces)  
  
-   [Genéricos](#Generics)  
  
-   [Delegados](#Delegates)  
  
##  <a name="Classes"></a> Classes e objetos  
 Os termos *classe* e *objeto* são às vezes usados alternadamente, mas na verdade, as classes descrevem o *tipo* de objetos, enquanto objetos são utilizáveis *instâncias* de classes. Assim, o ato de criar um objeto é chamado *instanciação*. Usando a analogia da planta, uma classe é a planta e um objeto é a construção feita daquela planta.  
  
 Para definir uma classe:  
  
```c#  
class SampleClass  
{  
}  
```  
  
 C\# também oferece uma versão leve de classes chamado *estruturas* que são úteis quando você precisa criar uma matriz grande de objetos e não deseja consumir muita memória para isso.  
  
 Para definir uma estrutura:  
  
```c#  
struct SampleStruct  
{  
}  
```  
  
 Para obter mais informações, consulte:  
  
-   [classe](../../../csharp/language-reference/keywords/class.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> Membros de classe  
 Cada classe pode ter diferentes *membros de classe* que incluem propriedades que descrevem os dados de classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.  
  
####  <a name="Properties"></a> Campos e propriedades  
 Campos e propriedades representam informações que um objeto contém. Campos são como variáveis, porque eles podem ser lidos ou definidos diretamente.  
  
 Para definir um campo:  
  
```c#  
Class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 Propriedades têm get e definir procedimentos, que oferecem mais controle sobre como os valores são definidos ou retornados.  
  
 C\# permite que você crie um campo particular para armazenar o valor da propriedade ou use chamadas propriedades implementadas automaticamente que criar esse campo automaticamente em segundo plano e fornecerem a lógica básica para os procedimentos de propriedade.  
  
 Para definir uma propriedade implementada automaticamente:  
  
```c#  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 Se você precisa executar algumas operações adicionais para ler e gravar o valor de propriedade, defina um campo para armazenar o valor da propriedade e fornecer a lógica básica para armazenar e recuperar:  
  
```c#  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade. No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas. No c\#, você pode omitir o `get` ou `set` o método de propriedade. No entanto, as propriedades implementadas automaticamente não podem ser somente leitura ou somente gravação.  
  
 Para obter mais informações, consulte:  
  
-   [get](../../../csharp/language-reference/keywords/get.md)  
  
-   [set](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> Métodos  
 Um *método* é uma ação que um objeto pode executar.  
  
 Para definir um método de uma classe:  
  
```c#  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 Uma classe pode ter várias implementações, ou *sobrecargas*, do mesmo método que diferem no número de parâmetros ou tipos de parâmetro.  
  
 Para sobrecarregar um método:  
  
```c#  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 Na maioria dos casos você declarar um método dentro de uma definição de classe. No entanto, c\# também oferece suporte a *métodos de extensão* que permitem que você adicione métodos a uma classe existente fora a definição real da classe.  
  
 Para obter mais informações, consulte:  
  
-   [Métodos](../../../fsharp/language-reference/members/methods.md)  
  
-   [Métodos de extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> Construtores  
 Construtores são os métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado. Construtores geralmente inicializam os membros de dados do novo objeto. Um construtor pode executar apenas uma vez quando uma classe é criada. Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe. No entanto, você pode criar várias sobrecargas de construtor da mesma forma e qualquer outro método.  
  
 Para definir um construtor para uma classe:  
  
```c#  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 Para obter mais informações, consulte:  
  
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md).  
  
####  <a name="Destructors"></a> Destruidores  
 Destruidores são usados para destruct instâncias de classes. No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e liberação de memória para os objetos gerenciados no seu aplicativo. No entanto, talvez ainda seja necessário usar destruidores para limpar os recursos não gerenciados que seu aplicativo cria. Pode haver apenas um destruidor para uma classe.  
  
 Para obter mais informações sobre destruidores e coleta de lixo no .NET Framework, consulte [Garbage Collection](../Topic/Garbage%20Collection.md).  
  
####  <a name="Events"></a> Eventos  
 Eventos permitem que uma classe ou objeto para notificar outras classes ou objetos quando algo interessante ocorre. A classe que envia \(ou gera\) o evento é chamada de *publisher* e as classes de evento receberem \(ou manipularem\) são chamadas *assinantes*. Para obter mais informações sobre eventos, como eles são gerados e manipulados, consulte [Eventos](../Topic/Handling%20and%20Raising%20Events.md).  
  
-   Para declarar um evento em uma classe, use o [event](../../../csharp/language-reference/keywords/event.md) palavra\-chave.  
  
-   Para gerar um evento, invocar o delegado de evento.  
  
-   Para assinar um evento, use o `+=` operador; para cancelar a assinatura de um evento, use o `-=` operador.  
  
####  <a name="NestedClasses"></a> Classes aninhadas  
 Uma classe definida dentro de outra classe é chamada *aninhada*. Por padrão, a classe aninhada é particular.  
  
```c#  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 Para criar uma instância da classe aninhada, use o nome da classe de contêiner, seguido do ponto e, em seguida, seguido do nome da classe aninhada:  
  
```c#  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> Modificadores de acesso e níveis de acesso  
 Todas as classes e membros de classe podem especificar o nível de acesso que eles fornecem a outras classes usando *modificadores de acesso*.  
  
 Os modificadores de acesso a seguir estão disponíveis:  
  
|Modificador de c\#|Definição|  
|------------------------|---------------|  
|[public](../../../csharp/language-reference/keywords/public.md)|O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.|  
|[private](../../../csharp/language-reference/keywords/private.md)|O tipo ou membro só pode ser acessado pelo código na mesma classe.|  
|[protected](../../../csharp/language-reference/keywords/protected.md)|O tipo ou membro só pode ser acessado pelo código na mesma classe ou em uma classe derivada.|  
|[interno](../../../csharp/language-reference/keywords/internal.md)|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.|  
|`protected internal`|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, ou por qualquer classe derivada em outro assembly.|  
  
 Para obter mais informações, consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
###  <a name="InstantiatingClasses"></a> Instanciação de Classes  
 Para criar um objeto, você precisa criar uma instância de uma classe, ou criar uma instância da classe.  
  
```c#  
SampleClass sampleObject = new SampleClass();  
```  
  
 Depois de instanciar uma classe, você pode atribuir valores a propriedades e campos de instância e chamar os métodos da classe.  
  
```c#  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:  
  
```c#  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Para obter mais informações, consulte:  
  
-   [Operador new](../../../visual-basic/language-reference/operators/new-operator.md)  
  
-   [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> Classes static e membros  
 Um membro estático da classe é uma propriedade, procedimento ou campo que é compartilhado por todas as instâncias de uma classe.  
  
 Para definir um membro estático:  
  
```c#  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 Para acessar o membro estático, use o nome da classe sem criar um objeto dessa classe:  
  
```c#  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 Classes estáticas em c\# tem apenas membros estáticos e não podem ser instanciadas. Membros estáticos também não é possível acessar métodos, campos ou propriedades não estático  
  
 Para obter mais informações, consulte: [static](../../../csharp/language-reference/keywords/static.md).  
  
###  <a name="AnonymousTypes"></a> Tipos anônimos  
 Tipos anônimos permitem que você crie objetos sem escrever uma definição de classe para o tipo de dados. Em vez disso, o compilador gera uma classe para você. A classe não tem nenhum nome utilizável e contém as propriedades que você especificar no declarar o objeto.  
  
 Para criar uma instância de um tipo anônimo:  
  
```c#  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Para obter mais informações, consulte: [Tipos anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
##  <a name="Inheritance"></a> Herança  
 Herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento que é definido em outra classe. A classe cujos membros são herdados é chamada a *classe base*, e a classe que herda os membros é chamada de *classe derivada*. No entanto, todas as classes em c\# implicitamente herdam o <xref:System.Object> classe que oferece suporte a hierarquia de classe do .NET e fornece serviços de nível baixo para todas as classes.  
  
> [!NOTE]
>  C\# não oferece suporte a herança múltipla, ou seja, você pode especificar apenas uma classe base para uma classe derivada.  
  
 Para herdar de uma classe base:  
  
```c#  
class DerivedClass:BaseClass{}  
```  
  
 Por padrão, todas as classes podem ser herdadas. No entanto, você pode especificar se uma classe não deve ser usada como uma classe base ou cria uma classe que pode ser usada como apenas uma classe base.  
  
 Para especificar que uma classe não pode ser usada como uma classe base:  
  
```c#  
public sealed class A { }  
```  
  
 Para especificar que uma classe pode ser usada como uma classe base apenas e não pode ser instanciada:  
  
```c#  
public abstract class B { }  
```  
  
 Para obter mais informações, consulte:  
  
-   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> Substituindo membros  
 Por padrão, uma classe derivada herda todos os membros de sua classe base. Se você quiser alterar o comportamento do membro herdado, você precisa substituí\-la. Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.  
  
 Seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:  
  
|Modificador de c\#|Definição|  
|------------------------|---------------|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Permite que um membro da classe a ser substituído em uma classe derivada.|  
|[override](../../../csharp/language-reference/keywords/override.md)|Substitui um membro \(substituível\) virtual definido na classe base.|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Requer que um membro da classe a ser substituído na classe derivada.|  
|[Modificador new](../../../csharp/language-reference/keywords/new-modifier.md)|Oculta um membro herdado de uma classe base|  
  
##  <a name="Interfaces"></a> Interfaces  
 Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos. Mas, diferentemente das classes, interfaces não fornecem implementação. Eles são implementados por classes e definidos como entidades separadas de classes. Uma interface representa um contrato que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.  
  
 Para definir uma interface:  
  
```c#  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 Para implementar uma interface em uma classe:  
  
```c#  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 Para obter mais informações, consulte:  
  
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)  
  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> Genéricos  
 Classes, estruturas, interfaces e métodos do .NET Framework podem incluir *parâmetros de tipo* que definem os tipos de objetos que podem armazenar ou usar. O exemplo mais comum de genéricos é uma coleção, onde você pode especificar o tipo de objeto a ser armazenado em uma coleção.  
  
 Para definir uma classe genérica:  
  
```c#  
Public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 Para criar uma instância de uma classe genérica:  
  
```c#  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 Para obter mais informações, consulte:  
  
-   [Genéricos](../Topic/Generics%20in%20the%20.NET%20Framework.md)  
  
-   [Genéricos](../../../visual-basic/reference/command-line-compiler/index.md)  
  
##  <a name="Delegates"></a> Delegados  
 Um *Delegar* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível. Você pode invocar \(ou chamar\) o método por meio do delegado. Delegados são usados para passar métodos como argumentos para outros métodos.  
  
> [!NOTE]
>  Manipuladores de eventos são nada mais do que os métodos são chamados por meio de delegados. Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [Eventos](../Topic/Handling%20and%20Raising%20Events.md).  
  
 Para criar um delegado:  
  
```c#  
public delegate void SampleDelegate(string str);  
```  
  
 Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:  
  
```c#  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 Para obter mais informações, consulte:  
  
-   [Delegados](../../../csharp/programming-guide/delegates/index.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)