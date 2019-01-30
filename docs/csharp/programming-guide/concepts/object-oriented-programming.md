---
title: Programação orientada a objeto (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 8f7a810b3f3ec74723ca5e715b7428e1b60928f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702477"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="c5afc-102">Programação orientada a objeto (C#)</span><span class="sxs-lookup"><span data-stu-id="c5afc-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="c5afc-103">O C# dá suporte completo à programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.</span><span class="sxs-lookup"><span data-stu-id="c5afc-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="c5afc-104">*Encapsulamento* significa que um grupo de propriedades, métodos e outros membros relacionados é tratado como uma única unidade ou objeto.</span><span class="sxs-lookup"><span data-stu-id="c5afc-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="c5afc-105">*Herança* descreve a capacidade de criar novas classes com base em uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="c5afc-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="c5afc-106">*Polimorfismo* significa que você pode ter várias classes que podem ser usadas de forma intercambiável, ainda que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="c5afc-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="c5afc-107">Esta seção descreve os seguintes conceitos:</span><span class="sxs-lookup"><span data-stu-id="c5afc-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="c5afc-108">Classes e objetos</span><span class="sxs-lookup"><span data-stu-id="c5afc-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="c5afc-109">Membros de classe</span><span class="sxs-lookup"><span data-stu-id="c5afc-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="c5afc-110">Propriedades e campos</span><span class="sxs-lookup"><span data-stu-id="c5afc-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="c5afc-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5afc-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="c5afc-112">Construtores</span><span class="sxs-lookup"><span data-stu-id="c5afc-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="c5afc-113">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="c5afc-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="c5afc-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="c5afc-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="c5afc-115">Classes aninhadas</span><span class="sxs-lookup"><span data-stu-id="c5afc-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="c5afc-116">Modificadores de acesso e níveis de acesso</span><span class="sxs-lookup"><span data-stu-id="c5afc-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="c5afc-117">Instanciando classes</span><span class="sxs-lookup"><span data-stu-id="c5afc-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="c5afc-118">Classes e membros estáticos</span><span class="sxs-lookup"><span data-stu-id="c5afc-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="c5afc-119">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="c5afc-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="c5afc-120">Herança</span><span class="sxs-lookup"><span data-stu-id="c5afc-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="c5afc-121">Substituindo membros</span><span class="sxs-lookup"><span data-stu-id="c5afc-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="c5afc-122">Interfaces</span><span class="sxs-lookup"><span data-stu-id="c5afc-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="c5afc-123">Genéricos</span><span class="sxs-lookup"><span data-stu-id="c5afc-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="c5afc-124">Delegados</span><span class="sxs-lookup"><span data-stu-id="c5afc-124">Delegates</span></span>](#Delegates)  
  
##  <a name="Classes"></a> <span data-ttu-id="c5afc-125">Classes e objetos</span><span class="sxs-lookup"><span data-stu-id="c5afc-125">Classes and Objects</span></span>  
 <span data-ttu-id="c5afc-126">Os termos *classe* e *objeto* às vezes são usados de forma intercambiável, mas, na verdade, as classes descrevem o *tipo* dos objetos, enquanto os objetos são *instâncias* utilizáveis das classes.</span><span class="sxs-lookup"><span data-stu-id="c5afc-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="c5afc-127">Sendo assim, o ato de criar um objeto é chamado de *instanciação*.</span><span class="sxs-lookup"><span data-stu-id="c5afc-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="c5afc-128">Usando a analogia da uma planta, uma classe é a planta e um objeto é a construção feita com base naquela planta.</span><span class="sxs-lookup"><span data-stu-id="c5afc-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="c5afc-129">Para definir uma classe:</span><span class="sxs-lookup"><span data-stu-id="c5afc-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="c5afc-130">O C# também oferece uma versão leve das classes chamada de *estruturas*, que são úteis quando você precisa criar uma matriz grande de objetos e não quer consumir muita memória para isso.</span><span class="sxs-lookup"><span data-stu-id="c5afc-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="c5afc-131">Para definir uma estrutura:</span><span class="sxs-lookup"><span data-stu-id="c5afc-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="c5afc-132">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c5afc-133">class</span><span class="sxs-lookup"><span data-stu-id="c5afc-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="c5afc-134">struct</span><span class="sxs-lookup"><span data-stu-id="c5afc-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <a name="Members"></a> <span data-ttu-id="c5afc-135">Membros de classe</span><span class="sxs-lookup"><span data-stu-id="c5afc-135">Class Members</span></span>  
 <span data-ttu-id="c5afc-136">Cada classe tem diferentes *membros de classe* que incluem propriedades que descrevem dados da classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="c5afc-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <a name="Properties"></a> <span data-ttu-id="c5afc-137">Propriedades e campos</span><span class="sxs-lookup"><span data-stu-id="c5afc-137">Properties and Fields</span></span>  
 <span data-ttu-id="c5afc-138">Os campos e as propriedades representam as informações que um objeto contém.</span><span class="sxs-lookup"><span data-stu-id="c5afc-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="c5afc-139">Os campos são como variáveis, porque podem ser lidos ou definidos de forma direta.</span><span class="sxs-lookup"><span data-stu-id="c5afc-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="c5afc-140">Para definir um campo:</span><span class="sxs-lookup"><span data-stu-id="c5afc-140">To define a field:</span></span>  
  
```csharp  
class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="c5afc-141">As propriedades têm procedimentos de obter e definir, que oferecem mais controle sobre como os valores são definidos ou retornados.</span><span class="sxs-lookup"><span data-stu-id="c5afc-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="c5afc-142">O C# permite criar um campo particular para armazenar o valor da propriedade ou usar as chamadas propriedade autoimplementada que criam esse campo automaticamente em segundo plano e fornecem a lógica básica para os procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="c5afc-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="c5afc-143">Para definir uma propriedade autoimplementada:</span><span class="sxs-lookup"><span data-stu-id="c5afc-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="c5afc-144">Se você precisar executar operações adicionais para ler e gravar o valor da propriedade, defina um campo para armazenar o valor da propriedade e forneça a lógica básica para armazenar e recuperá-la:</span><span class="sxs-lookup"><span data-stu-id="c5afc-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="c5afc-145">A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="c5afc-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="c5afc-146">No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas.</span><span class="sxs-lookup"><span data-stu-id="c5afc-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="c5afc-147">No C#, é possível omitir o método de propriedade `get` ou `set`.</span><span class="sxs-lookup"><span data-stu-id="c5afc-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="c5afc-148">No entanto, propriedades autoimplementadas não podem ser somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="c5afc-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="c5afc-149">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c5afc-150">get</span><span class="sxs-lookup"><span data-stu-id="c5afc-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="c5afc-151">set</span><span class="sxs-lookup"><span data-stu-id="c5afc-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <a name="Methods"></a> <span data-ttu-id="c5afc-152">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5afc-152">Methods</span></span>  
 <span data-ttu-id="c5afc-153">Um *método* é uma ação que um objeto pode executar.</span><span class="sxs-lookup"><span data-stu-id="c5afc-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="c5afc-154">Para definir um método de uma classe:</span><span class="sxs-lookup"><span data-stu-id="c5afc-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="c5afc-155">Uma classe pode ter várias implementações ou *sobrecargas*, do mesmo método que diferem quanto ao número de parâmetros ou tipos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c5afc-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="c5afc-156">Para sobrecarregar um método:</span><span class="sxs-lookup"><span data-stu-id="c5afc-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="c5afc-157">Na maioria dos casos, você declara um método dentro de uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="c5afc-158">No entanto, o C# também dá suporte a *métodos de extensão* que permitem adicionar métodos a uma classe existente fora da definição real da classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="c5afc-159">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c5afc-160">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5afc-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="c5afc-161">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="c5afc-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <a name="Constructors"></a> <span data-ttu-id="c5afc-162">Construtores</span><span class="sxs-lookup"><span data-stu-id="c5afc-162">Constructors</span></span>  
 <span data-ttu-id="c5afc-163">Construtores são métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado.</span><span class="sxs-lookup"><span data-stu-id="c5afc-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="c5afc-164">Os construtores normalmente inicializam os membros de dados do novo objeto.</span><span class="sxs-lookup"><span data-stu-id="c5afc-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="c5afc-165">Um construtor pode ser executado apenas uma vez quando uma classe é criada.</span><span class="sxs-lookup"><span data-stu-id="c5afc-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="c5afc-166">Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="c5afc-167">No entanto, é possível criar várias sobrecargas de construtor da mesma forma que é feita para qualquer outro método.</span><span class="sxs-lookup"><span data-stu-id="c5afc-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="c5afc-168">Para definir um construtor para uma classe:</span><span class="sxs-lookup"><span data-stu-id="c5afc-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="c5afc-169">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-169">For more information, see:</span></span>  
  
 <span data-ttu-id="c5afc-170">[Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <a name="Finalizers"></a> <span data-ttu-id="c5afc-171">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="c5afc-171">Finalizers</span></span>  
 <span data-ttu-id="c5afc-172">Finalizadores são usados para destruir instâncias de classes.</span><span class="sxs-lookup"><span data-stu-id="c5afc-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="c5afc-173">No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e a liberação de memória para os objetos gerenciados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5afc-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="c5afc-174">No entanto, talvez ainda seja necessário usar os finalizadores para limpar recursos não gerenciados que seu aplicativo criar.</span><span class="sxs-lookup"><span data-stu-id="c5afc-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="c5afc-175">Pode haver apenas um finalizador para uma classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="c5afc-176">Para obter mais informações sobre os finalizadores e a coleta de lixo no .NET Framework, consulte [Coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <a name="Events"></a> <span data-ttu-id="c5afc-177">Eventos</span><span class="sxs-lookup"><span data-stu-id="c5afc-177">Events</span></span>  
 <span data-ttu-id="c5afc-178">Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer.</span><span class="sxs-lookup"><span data-stu-id="c5afc-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="c5afc-179">A classe que envia (ou aciona) o evento é chamada de *editor* e as classes que recebem (ou manipulam) os eventos são chamadas *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="c5afc-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="c5afc-180">Para obter mais informações sobre os eventos e como eles são gerados e manipulados, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="c5afc-181">Para declarar um evento em uma classe, use a palavra-chave [event](../../../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="c5afc-182">Para acionar um evento, invoque o delegado do evento.</span><span class="sxs-lookup"><span data-stu-id="c5afc-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="c5afc-183">Para assinar um evento, use o operador `+=`; para cancelar a assinatura de um evento, use o operador `-=`.</span><span class="sxs-lookup"><span data-stu-id="c5afc-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <a name="NestedClasses"></a> <span data-ttu-id="c5afc-184">Classes aninhadas</span><span class="sxs-lookup"><span data-stu-id="c5afc-184">Nested Classes</span></span>  
 <span data-ttu-id="c5afc-185">Uma classe definida dentro de outra classe é chamada de *aninhada*.</span><span class="sxs-lookup"><span data-stu-id="c5afc-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="c5afc-186">Por padrão, a classe aninhada é particular.</span><span class="sxs-lookup"><span data-stu-id="c5afc-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="c5afc-187">Para criar uma instância da classe aninhada, use o nome da classe de contêiner seguido pelo ponto e, em seguida, seguido pelo nome da classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="c5afc-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <a name="AccessModifiers"></a> <span data-ttu-id="c5afc-188">Modificadores de acesso e níveis de acesso</span><span class="sxs-lookup"><span data-stu-id="c5afc-188">Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="c5afc-189">Todas as classes e membros de classe podem especificar o nível de acesso que fornecem a outras classes usando *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="c5afc-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="c5afc-190">Os modificadores de acesso a seguir estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="c5afc-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="c5afc-191">Modificador de C#</span><span class="sxs-lookup"><span data-stu-id="c5afc-191">C# Modifier</span></span>|<span data-ttu-id="c5afc-192">Definição</span><span class="sxs-lookup"><span data-stu-id="c5afc-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="c5afc-193">public</span><span class="sxs-lookup"><span data-stu-id="c5afc-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="c5afc-194">O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="c5afc-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="c5afc-195">private</span><span class="sxs-lookup"><span data-stu-id="c5afc-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="c5afc-196">O tipo ou membro pode ser acessado somente pelo código na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="c5afc-197">protected</span><span class="sxs-lookup"><span data-stu-id="c5afc-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="c5afc-198">O tipo ou membro pode ser acessado somente pelo código na mesma classe ou em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c5afc-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="c5afc-199">internal</span><span class="sxs-lookup"><span data-stu-id="c5afc-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="c5afc-200">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="c5afc-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|[<span data-ttu-id="c5afc-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="c5afc-201">protected internal</span></span>](../../../csharp/language-reference/keywords/protected-internal.md)|<span data-ttu-id="c5afc-202">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly ou por qualquer classe derivada em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="c5afc-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
|[<span data-ttu-id="c5afc-203">private protected</span><span class="sxs-lookup"><span data-stu-id="c5afc-203">private protected</span></span>](../../../csharp/language-reference/keywords/private-protected.md)|<span data-ttu-id="c5afc-204">O tipo ou membro pode ser acessado pelo código na mesma classe ou em uma classe derivada no assembly da classe base.</span><span class="sxs-lookup"><span data-stu-id="c5afc-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|  
  
 <span data-ttu-id="c5afc-205">Para obter mais informações, consulte [Modificadores de Acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-205">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <a name="InstantiatingClasses"></a> <span data-ttu-id="c5afc-206">Instanciando classes</span><span class="sxs-lookup"><span data-stu-id="c5afc-206">Instantiating Classes</span></span>  
 <span data-ttu-id="c5afc-207">Para criar um objeto, você precisa instanciar uma classe ou criar uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="c5afc-208">Após instanciar uma classe, você pode atribuir valores às propriedades e campos da instância e invocar métodos da classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="c5afc-209">Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:</span><span class="sxs-lookup"><span data-stu-id="c5afc-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="c5afc-210">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-210">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c5afc-211">Operador new</span><span class="sxs-lookup"><span data-stu-id="c5afc-211">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="c5afc-212">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="c5afc-212">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <a name="Static"></a> <span data-ttu-id="c5afc-213">Classes e membros estáticos</span><span class="sxs-lookup"><span data-stu-id="c5afc-213">Static Classes and Members</span></span>  
 <span data-ttu-id="c5afc-214">Um membro estático da classe é uma propriedade, procedimento ou campo que é compartilhado por todas as instâncias de uma classe.</span><span class="sxs-lookup"><span data-stu-id="c5afc-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="c5afc-215">Para definir um membro estático:</span><span class="sxs-lookup"><span data-stu-id="c5afc-215">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="c5afc-216">Para acessar o membro estático, use o nome da classe sem criar um objeto dessa classe:</span><span class="sxs-lookup"><span data-stu-id="c5afc-216">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="c5afc-217">Classes estáticas em C# têm apenas membros estáticos e não podem ser instanciadas.</span><span class="sxs-lookup"><span data-stu-id="c5afc-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="c5afc-218">Membros estáticos também não podem acessar propriedades, métodos ou campos não estáticos</span><span class="sxs-lookup"><span data-stu-id="c5afc-218">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="c5afc-219">Para obter mais informações, consulte [static](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-219">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <a name="AnonymousTypes"></a> <span data-ttu-id="c5afc-220">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="c5afc-220">Anonymous Types</span></span>  
 <span data-ttu-id="c5afc-221">Os tipos anônimos permitem criar objetos sem escrever uma definição de classe para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="c5afc-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="c5afc-222">Em vez disso, o compilador gera uma classe para você.</span><span class="sxs-lookup"><span data-stu-id="c5afc-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="c5afc-223">A classe não tem nenhum nome utilizável e contém as propriedades que você especificar ao declarar o objeto.</span><span class="sxs-lookup"><span data-stu-id="c5afc-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="c5afc-224">Para criar uma instância de um tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="c5afc-224">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="c5afc-225">Para obter mais informações, consulte: [Tipos Anônimos](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-225">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <a name="Inheritance"></a> <span data-ttu-id="c5afc-226">Herança</span><span class="sxs-lookup"><span data-stu-id="c5afc-226">Inheritance</span></span>  
 <span data-ttu-id="c5afc-227">A herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento definido em outras classes.</span><span class="sxs-lookup"><span data-stu-id="c5afc-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="c5afc-228">A classe cujos membros são herdados é chamada *classe base* e a classe que herda esses membros é chamada *classe derivada*.</span><span class="sxs-lookup"><span data-stu-id="c5afc-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="c5afc-229">No entanto, todas as classes em C# herdam implicitamente da classe <xref:System.Object> que dá suporte à hierarquia de classes do .NET e fornece serviços de nível baixo para todas as classes.</span><span class="sxs-lookup"><span data-stu-id="c5afc-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5afc-230">O C# não dá suporte a várias heranças.</span><span class="sxs-lookup"><span data-stu-id="c5afc-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="c5afc-231">Ou seja, você pode especificar apenas uma classe base para uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c5afc-231">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="c5afc-232">Para herdar de uma classe base:</span><span class="sxs-lookup"><span data-stu-id="c5afc-232">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass {}  
```  
  
 <span data-ttu-id="c5afc-233">Por padrão, todas as classes podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="c5afc-233">By default all classes can be inherited.</span></span> <span data-ttu-id="c5afc-234">No entanto, é possível especificar se uma classe não deve ser usada como classe base ou criar uma classe que possa ser usada apenas como classe base.</span><span class="sxs-lookup"><span data-stu-id="c5afc-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="c5afc-235">Para especificar que uma classe não pode ser usada como classe base:</span><span class="sxs-lookup"><span data-stu-id="c5afc-235">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="c5afc-236">Para especificar que uma classe pode ser usada apenas como classe base e não pode ser instanciada:</span><span class="sxs-lookup"><span data-stu-id="c5afc-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="c5afc-237">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-237">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c5afc-238">sealed</span><span class="sxs-lookup"><span data-stu-id="c5afc-238">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="c5afc-239">abstract</span><span class="sxs-lookup"><span data-stu-id="c5afc-239">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <a name="Overriding"></a> <span data-ttu-id="c5afc-240">Substituindo membros</span><span class="sxs-lookup"><span data-stu-id="c5afc-240">Overriding Members</span></span>  
 <span data-ttu-id="c5afc-241">Por padrão, uma classe derivada herda todos os membros de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="c5afc-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="c5afc-242">Se quiser alterar o comportamento do membro herdado, você precisa substituí-la.</span><span class="sxs-lookup"><span data-stu-id="c5afc-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="c5afc-243">Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c5afc-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="c5afc-244">Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:</span><span class="sxs-lookup"><span data-stu-id="c5afc-244">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="c5afc-245">Modificador de C#</span><span class="sxs-lookup"><span data-stu-id="c5afc-245">C# Modifier</span></span>|<span data-ttu-id="c5afc-246">Definição</span><span class="sxs-lookup"><span data-stu-id="c5afc-246">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="c5afc-247">virtual</span><span class="sxs-lookup"><span data-stu-id="c5afc-247">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="c5afc-248">Permite que um membro de classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c5afc-248">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="c5afc-249">override</span><span class="sxs-lookup"><span data-stu-id="c5afc-249">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="c5afc-250">Substitui um membro virtual (substituível) definido na classe base.</span><span class="sxs-lookup"><span data-stu-id="c5afc-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="c5afc-251">abstract</span><span class="sxs-lookup"><span data-stu-id="c5afc-251">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="c5afc-252">Requer que um membro de classe seja substituído na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="c5afc-252">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="c5afc-253">Modificador new</span><span class="sxs-lookup"><span data-stu-id="c5afc-253">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="c5afc-254">Oculta um membro herdado de uma classe base</span><span class="sxs-lookup"><span data-stu-id="c5afc-254">Hides a member inherited from a base class</span></span>|  
  
##  <a name="Interfaces"></a> <span data-ttu-id="c5afc-255">Interfaces</span><span class="sxs-lookup"><span data-stu-id="c5afc-255">Interfaces</span></span>  
 <span data-ttu-id="c5afc-256">Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="c5afc-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="c5afc-257">Mas, diferente das classes, as interfaces não fornecem implementação.</span><span class="sxs-lookup"><span data-stu-id="c5afc-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="c5afc-258">Elas são implementadas por classes e definidas como entidades separadas das classes.</span><span class="sxs-lookup"><span data-stu-id="c5afc-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="c5afc-259">Uma interface representa um contrato, no sentido em que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.</span><span class="sxs-lookup"><span data-stu-id="c5afc-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="c5afc-260">Para definir uma interface:</span><span class="sxs-lookup"><span data-stu-id="c5afc-260">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="c5afc-261">Para implementar uma interface em uma classe:</span><span class="sxs-lookup"><span data-stu-id="c5afc-261">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="c5afc-262">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-262">For more information, see:</span></span>  
  
 [<span data-ttu-id="c5afc-263">Interfaces</span><span class="sxs-lookup"><span data-stu-id="c5afc-263">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="c5afc-264">interface</span><span class="sxs-lookup"><span data-stu-id="c5afc-264">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <a name="Generics"></a> <span data-ttu-id="c5afc-265">Genéricos</span><span class="sxs-lookup"><span data-stu-id="c5afc-265">Generics</span></span>  
 <span data-ttu-id="c5afc-266">Classes, estruturas, interfaces e métodos do .NET Framework podem incluir *parâmetros de tipo* que definem tipos de objetos que podem armazenar ou usar.</span><span class="sxs-lookup"><span data-stu-id="c5afc-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="c5afc-267">O exemplo mais comum dos genéricos é uma coleção, em que você pode especificar o tipo dos objeto a serem armazenados em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="c5afc-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="c5afc-268">Para definir uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="c5afc-268">To define a generic class:</span></span>  
  
```csharp  
public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="c5afc-269">Para criar uma instância de uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="c5afc-269">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="c5afc-270">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c5afc-271">Genéricos</span><span class="sxs-lookup"><span data-stu-id="c5afc-271">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="c5afc-272">Genéricos</span><span class="sxs-lookup"><span data-stu-id="c5afc-272">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <a name="Delegates"></a> <span data-ttu-id="c5afc-273">Delegados</span><span class="sxs-lookup"><span data-stu-id="c5afc-273">Delegates</span></span>  
 <span data-ttu-id="c5afc-274">Um *delegado* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível.</span><span class="sxs-lookup"><span data-stu-id="c5afc-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="c5afc-275">Você pode invocar (ou chamar) o método através do delegado.</span><span class="sxs-lookup"><span data-stu-id="c5afc-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="c5afc-276">Delegados são usados para passar métodos como argumentos a outros métodos.</span><span class="sxs-lookup"><span data-stu-id="c5afc-276">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5afc-277">Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados.</span><span class="sxs-lookup"><span data-stu-id="c5afc-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="c5afc-278">Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="c5afc-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="c5afc-279">Para criar um delegado:</span><span class="sxs-lookup"><span data-stu-id="c5afc-279">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="c5afc-280">Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:</span><span class="sxs-lookup"><span data-stu-id="c5afc-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="c5afc-281">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="c5afc-281">For more information, see:</span></span>  
  
-   [<span data-ttu-id="c5afc-282">Delegados</span><span class="sxs-lookup"><span data-stu-id="c5afc-282">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="c5afc-283">delegate</span><span class="sxs-lookup"><span data-stu-id="c5afc-283">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="c5afc-284">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c5afc-284">See also</span></span>

- [<span data-ttu-id="c5afc-285">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="c5afc-285">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
