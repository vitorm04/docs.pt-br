---
title: Programação orientada a objeto (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 7822b9afa4b568563222d6096ea1b1ecc5d5ee0a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377918"
---
# <a name="object-oriented-programming-c"></a>Programação orientada a objeto (C#)
O C# dá suporte completo à programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.  
  
 *Encapsulamento* significa que um grupo de propriedades, métodos e outros membros relacionados é tratado como uma única unidade ou objeto.  
  
 *Herança* descreve a capacidade de criar novas classes com base em uma classe existente.  
  
 *Polimorfismo* significa que você pode ter várias classes que podem ser usadas de forma intercambiável, ainda que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.  
  
 Esta seção descreve os seguintes conceitos:  
  
-   [Classes e objetos](#Classes)  
  
    -   [Membros de classe](#Members)  
  
         [Propriedades e campos](#Properties)  
  
         [Métodos](#Methods)  
  
         [Construtores](#Constructors)  
  
         [Finalizadores](#Finalizers)  
  
         [Eventos](#Events)  
  
         [Classes aninhadas](#NestedClasses)  
  
    -   [Modificadores de acesso e níveis de acesso](#AccessModifiers)  
  
    -   [Instanciando classes](#InstantiatingClasses)  
  
    -   [Classes e membros estáticos](#Static)  
  
    -   [Tipos Anônimos](#AnonymousTypes)  
  
-   [Herança](#Inheritance)  
  
    -   [Substituindo membros](#Overriding)  
  
-   [Interfaces](#Interfaces)  
  
-   [Genéricos](#Generics)  
  
-   [Delegados](#Delegates)  
  
## <a name="Classes"></a> Classes e objetos  
 Os termos *classe* e *objeto* às vezes são usados de forma intercambiável, mas, na verdade, as classes descrevem o *tipo* dos objetos, enquanto os objetos são *instâncias* utilizáveis das classes. Sendo assim, o ato de criar um objeto é chamado de *instanciação*. Usando a analogia da uma planta, uma classe é a planta e um objeto é a construção feita com base naquela planta.  
  
 Para definir uma classe:  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 O C# também oferece uma versão leve das classes chamada de *estruturas*, que são úteis quando você precisa criar uma matriz grande de objetos e não quer consumir muita memória para isso.  
  
 Para definir uma estrutura:  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 Para obter mais informações, consulte:  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [struct](../../../csharp/language-reference/keywords/struct.md)  
  
### <a name="Members"></a> Membros de classe  
 Cada classe tem diferentes *membros de classe* que incluem propriedades que descrevem dados da classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.  
  
#### <a name="Properties"></a> Propriedades e campos  
 Os campos e as propriedades representam as informações que um objeto contém. Os campos são como variáveis, porque podem ser lidos ou definidos de forma direta.  
  
 Para definir um campo:  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 As propriedades têm procedimentos de obter e definir, que oferecem mais controle sobre como os valores são definidos ou retornados.  
  
 O C# permite criar um campo particular para armazenar o valor da propriedade ou usar as chamadas propriedade autoimplementada que criam esse campo automaticamente em segundo plano e fornecem a lógica básica para os procedimentos de propriedade.  
  
 Para definir uma propriedade autoimplementada:  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 Se você precisar executar operações adicionais para ler e gravar o valor da propriedade, defina um campo para armazenar o valor da propriedade e forneça a lógica básica para armazenar e recuperá-la:  
  
```csharp  
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
  
 A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade. No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas. No C#, é possível omitir o método de propriedade `get` ou `set`. No entanto, propriedades autoimplementadas não podem ser somente leitura ou somente gravação.  
  
 Para obter mais informações, consulte:  
  
-   [get](../../../csharp/language-reference/keywords/get.md)  
  
-   [set](../../../csharp/language-reference/keywords/set.md)  
  
#### <a name="Methods"></a> Métodos  
 Um *método* é uma ação que um objeto pode executar.  
  
 Para definir um método de uma classe:  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 Uma classe pode ter várias implementações ou *sobrecargas*, do mesmo método que diferem quanto ao número de parâmetros ou tipos de parâmetro.  
  
 Para sobrecarregar um método:  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 Na maioria dos casos, você declara um método dentro de uma definição de classe. No entanto, o C# também dá suporte a *métodos de extensão* que permitem adicionar métodos a uma classe existente fora da definição real da classe.  
  
 Para obter mais informações, consulte:  
  
-   [Métodos](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [Métodos de Extensão](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
#### <a name="Constructors"></a> Construtores  
 Construtores são métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado. Os construtores normalmente inicializam os membros de dados do novo objeto. Um construtor pode ser executado apenas uma vez quando uma classe é criada. Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe. No entanto, é possível criar várias sobrecargas de construtor da mesma forma que é feita para qualquer outro método.  
  
 Para definir um construtor para uma classe:  
  
```csharp  
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
  
#### <a name="Finalizers"></a> Finalizadores  
 Finalizadores são usados para destruir instâncias de classes. No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e a liberação de memória para os objetos gerenciados em seu aplicativo. No entanto, talvez ainda seja necessário usar os finalizadores para limpar recursos não gerenciados que seu aplicativo criar. Pode haver apenas um finalizador para uma classe.  
  
 Para obter mais informações sobre os finalizadores e a coleta de lixo no .NET Framework, consulte [Coleta de lixo](../../../standard/garbage-collection/index.md).  
  
#### <a name="Events"></a> Eventos  
 Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer. A classe que envia (ou aciona) o evento é chamada de *editor* e as classes que recebem (ou manipulam) os eventos são chamadas *assinantes*. Para obter mais informações sobre os eventos e como eles são gerados e manipulados, consulte [Eventos](../../../standard/events/index.md).  
  
-   Para declarar um evento em uma classe, use a palavra-chave [event](../../../csharp/language-reference/keywords/event.md).  
  
-   Para acionar um evento, invoque o delegado do evento.  
  
-   Para assinar um evento, use o operador `+=`; para cancelar a assinatura de um evento, use o operador `-=`.  
  
#### <a name="NestedClasses"></a> Classes aninhadas  
 Uma classe definida dentro de outra classe é chamada de *aninhada*. Por padrão, a classe aninhada é particular.  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 Para criar uma instância da classe aninhada, use o nome da classe de contêiner seguido pelo ponto e, em seguida, seguido pelo nome da classe aninhada:  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
### <a name="AccessModifiers"></a> Modificadores de acesso e níveis de acesso  
 Todas as classes e membros de classe podem especificar o nível de acesso que fornecem a outras classes usando *modificadores de acesso*.  
  
 Os modificadores de acesso a seguir estão disponíveis:  
  
|Modificador de C#|Definição|  
|------------------|----------------|  
|[public](../../../csharp/language-reference/keywords/public.md)|O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.|  
|[private](../../../csharp/language-reference/keywords/private.md)|O tipo ou membro pode ser acessado somente pelo código na mesma classe.|  
|[protected](../../../csharp/language-reference/keywords/protected.md)|O tipo ou membro pode ser acessado somente pelo código na mesma classe ou em uma classe derivada.|  
|[internal](../../../csharp/language-reference/keywords/internal.md)|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.|  
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|O tipo ou membro pode ser acessado por qualquer código no mesmo assembly ou por qualquer classe derivada em outro assembly.|  
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|O tipo ou membro pode ser acessado pelo código na mesma classe ou em uma classe derivada no assembly da classe base.|  
  
 Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
### <a name="InstantiatingClasses"></a> Instanciando classes  
 Para criar um objeto, você precisa instanciar uma classe ou criar uma instância da classe.  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 Após instanciar uma classe, você pode atribuir valores às propriedades e campos da instância e invocar métodos da classe.  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Para obter mais informações, consulte:  
  
-   [Operador new](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [Inicializadores de objeto e coleção](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
### <a name="Static"></a> Classes e membros estáticos  
 Um membro estático da classe é uma propriedade, procedimento ou campo que é compartilhado por todas as instâncias de uma classe.  
  
 Para definir um membro estático:  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 Para acessar o membro estático, use o nome da classe sem criar um objeto dessa classe:  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 Classes estáticas em C# têm apenas membros estáticos e não podem ser instanciadas. Membros estáticos também não podem acessar propriedades, métodos ou campos não estáticos  
  
 Para obter mais informações, consulte [static](../../../csharp/language-reference/keywords/static.md).  
  
### <a name="AnonymousTypes"></a> Tipos anônimos  
 Os tipos anônimos permitem criar objetos sem escrever uma definição de classe para o tipo de dados. Em vez disso, o compilador gera uma classe para você. A classe não tem nenhum nome utilizável e contém as propriedades que você especificar ao declarar o objeto.  
  
 Para criar uma instância de um tipo anônimo:  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 Para obter mais informações, consulte: [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
## <a name="Inheritance"></a> Herança  
 A herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento definido em outras classes. A classe cujos membros são herdados é chamada *classe base* e a classe que herda esses membros é chamada *classe derivada*. No entanto, todas as classes em C# herdam implicitamente da classe <xref:System.Object> que dá suporte à hierarquia de classes do .NET e fornece serviços de nível baixo para todas as classes.  
  
> [!NOTE]
>  O C# não dá suporte a várias heranças. Ou seja, você pode especificar apenas uma classe base para uma classe derivada.  
  
 Para herdar de uma classe base:  
  
```csharp  
class DerivedClass:BaseClass {}  
```  
  
 Por padrão, todas as classes podem ser herdadas. No entanto, é possível especificar se uma classe não deve ser usada como classe base ou criar uma classe que possa ser usada apenas como classe base.  
  
 Para especificar que uma classe não pode ser usada como classe base:  
  
```csharp  
public sealed class A { }  
```  
  
 Para especificar que uma classe pode ser usada apenas como classe base e não pode ser instanciada:  
  
```csharp  
public abstract class B { }  
```  
  
 Para obter mais informações, consulte:  
  
-   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
### <a name="Overriding"></a> Substituindo membros  
 Por padrão, uma classe derivada herda todos os membros de sua classe base. Se quiser alterar o comportamento do membro herdado, você precisa substituí-la. Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.  
  
 Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:  
  
|Modificador de C#|Definição|  
|------------------|----------------|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Permite que um membro de classe seja substituído em uma classe derivada.|  
|[override](../../../csharp/language-reference/keywords/override.md)|Substitui um membro virtual (substituível) definido na classe base.|  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Requer que um membro de classe seja substituído na classe derivada.|  
|[Modificador new](../../../csharp/language-reference/keywords/new-modifier.md)|Oculta um membro herdado de uma classe base|  
  
## <a name="Interfaces"></a> Interfaces  
 Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos. Mas, diferente das classes, as interfaces não fornecem implementação. Elas são implementadas por classes e definidas como entidades separadas das classes. Uma interface representa um contrato, no sentido em que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.  
  
 Para definir uma interface:  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 Para implementar uma interface em uma classe:  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 Para obter mais informações, consulte:  
  
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)  
  
 [interface](../../../csharp/language-reference/keywords/interface.md)  
  
## <a name="Generics"></a> Genéricos  
 Classes, estruturas, interfaces e métodos do .NET Framework podem incluir *parâmetros de tipo* que definem tipos de objetos que podem armazenar ou usar. O exemplo mais comum dos genéricos é uma coleção, em que você pode especificar o tipo dos objeto a serem armazenados em uma coleção.  
  
 Para definir uma classe genérica:  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 Para criar uma instância de uma classe genérica:  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 Para obter mais informações, consulte:  
  
-   [Genéricos](~/docs/standard/generics/index.md)  
  
-   [Genéricos](../../../csharp/programming-guide/generics/index.md)  
  
## <a name="Delegates"></a> Delegados  
 Um *delegado* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível. Você pode invocar (ou chamar) o método através do delegado. Delegados são usados para passar métodos como argumentos a outros métodos.  
  
> [!NOTE]
>  Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados. Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [Eventos](../../../standard/events/index.md).  
  
 Para criar um delegado:  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:  
  
```csharp  
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
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
