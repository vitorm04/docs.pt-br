---
title: Programação orientada a objeto (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 2b6be3384f76fa210c2b52c55ecf9bd865df43a6
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200087"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="59a4f-102">Programação orientada a objeto (C#)</span><span class="sxs-lookup"><span data-stu-id="59a4f-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="59a4f-103">O C# dá suporte completo à programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.</span><span class="sxs-lookup"><span data-stu-id="59a4f-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="59a4f-104">*Encapsulamento* significa que um grupo de propriedades, métodos e outros membros relacionados é tratado como uma única unidade ou objeto.</span><span class="sxs-lookup"><span data-stu-id="59a4f-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="59a4f-105">*Herança* descreve a capacidade de criar novas classes com base em uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="59a4f-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="59a4f-106">*Polimorfismo* significa que você pode ter várias classes que podem ser usadas de forma intercambiável, ainda que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="59a4f-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="59a4f-107">Classes e objetos</span><span class="sxs-lookup"><span data-stu-id="59a4f-107">Classes and objects</span></span>

<span data-ttu-id="59a4f-108">A *classe* de termos e o *objeto* descrevem o *tipo* de objetos e as *instâncias* de classes, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="59a4f-108">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="59a4f-109">Sendo assim, o ato de criar um objeto é chamado de *instanciação*.</span><span class="sxs-lookup"><span data-stu-id="59a4f-109">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="59a4f-110">Usando a analogia da uma planta, uma classe é a planta e um objeto é a construção feita com base naquela planta.</span><span class="sxs-lookup"><span data-stu-id="59a4f-110">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="59a4f-111">Para definir uma classe:</span><span class="sxs-lookup"><span data-stu-id="59a4f-111">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="59a4f-112">O C# também fornece tipos chamados de *estruturas* que são úteis quando você não precisa de suporte para herança ou polimorfismo.</span><span class="sxs-lookup"><span data-stu-id="59a4f-112">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span>

<span data-ttu-id="59a4f-113">Para definir uma estrutura:</span><span class="sxs-lookup"><span data-stu-id="59a4f-113">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="59a4f-114">Para obter mais informações, consulte os artigos sobre as palavras-chave [Class](../../language-reference/keywords/class.md) e [struct](../../language-reference/builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="59a4f-114">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="59a4f-115">Membros de classe</span><span class="sxs-lookup"><span data-stu-id="59a4f-115">Class members</span></span>

<span data-ttu-id="59a4f-116">Cada classe tem diferentes *membros de classe* que incluem propriedades que descrevem dados da classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="59a4f-116">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="59a4f-117">Propriedades e campos</span><span class="sxs-lookup"><span data-stu-id="59a4f-117">Properties and fields</span></span>

<span data-ttu-id="59a4f-118">Os campos e as propriedades representam as informações que um objeto contém.</span><span class="sxs-lookup"><span data-stu-id="59a4f-118">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="59a4f-119">Os campos são como variáveis porque podem ser lidos ou definidos diretamente, sujeitos a modificadores de acesso aplicáveis.</span><span class="sxs-lookup"><span data-stu-id="59a4f-119">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="59a4f-120">Para definir um campo que pode ser acessado de dentro de instâncias da classe:</span><span class="sxs-lookup"><span data-stu-id="59a4f-120">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="59a4f-121">As propriedades `get` têm `set` e acessadores, que fornecem mais controle sobre como os valores são definidos ou retornados.</span><span class="sxs-lookup"><span data-stu-id="59a4f-121">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="59a4f-122">O C# permite criar um campo particular para armazenar o valor da propriedade ou usar Propriedades autoimplementadas que criam esse campo automaticamente nos bastidores e fornecer a lógica básica para os procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="59a4f-122">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="59a4f-123">Para definir uma propriedade autoimplementada:</span><span class="sxs-lookup"><span data-stu-id="59a4f-123">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="59a4f-124">Se você precisar executar operações adicionais para ler e gravar o valor da propriedade, defina um campo para armazenar o valor da propriedade e forneça a lógica básica para armazenar e recuperá-la:</span><span class="sxs-lookup"><span data-stu-id="59a4f-124">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="59a4f-125">A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59a4f-125">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="59a4f-126">No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas.</span><span class="sxs-lookup"><span data-stu-id="59a4f-126">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="59a4f-127">No C#, é possível omitir o método de propriedade `get` ou `set`.</span><span class="sxs-lookup"><span data-stu-id="59a4f-127">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="59a4f-128">No entanto, as propriedades implementadas automaticamente não podem ser somente gravação.</span><span class="sxs-lookup"><span data-stu-id="59a4f-128">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="59a4f-129">Propriedades implementadas automaticamente de somente leitura podem ser definidas em construtores da classe que a contém.</span><span class="sxs-lookup"><span data-stu-id="59a4f-129">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="59a4f-130">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="59a4f-130">For more information, see:</span></span>

- [<span data-ttu-id="59a4f-131">get</span><span class="sxs-lookup"><span data-stu-id="59a4f-131">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="59a4f-132">set</span><span class="sxs-lookup"><span data-stu-id="59a4f-132">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="59a4f-133">Métodos</span><span class="sxs-lookup"><span data-stu-id="59a4f-133">Methods</span></span>

<span data-ttu-id="59a4f-134">Um *método* é uma ação que um objeto pode executar.</span><span class="sxs-lookup"><span data-stu-id="59a4f-134">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="59a4f-135">Para definir um método de uma classe:</span><span class="sxs-lookup"><span data-stu-id="59a4f-135">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="59a4f-136">Uma classe pode ter várias implementações ou *sobrecargas*, do mesmo método que diferem quanto ao número de parâmetros ou tipos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="59a4f-136">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="59a4f-137">Para sobrecarregar um método:</span><span class="sxs-lookup"><span data-stu-id="59a4f-137">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="59a4f-138">Na maioria dos casos, você declara um método dentro de uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-138">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="59a4f-139">No entanto, o C# também dá suporte a *métodos de extensão* que permitem adicionar métodos a uma classe existente fora da definição real da classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-139">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="59a4f-140">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="59a4f-140">For more information, see:</span></span>

- [<span data-ttu-id="59a4f-141">Métodos</span><span class="sxs-lookup"><span data-stu-id="59a4f-141">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="59a4f-142">Métodos de extensão</span><span class="sxs-lookup"><span data-stu-id="59a4f-142">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="59a4f-143">Construtores</span><span class="sxs-lookup"><span data-stu-id="59a4f-143">Constructors</span></span>

<span data-ttu-id="59a4f-144">Construtores são métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado.</span><span class="sxs-lookup"><span data-stu-id="59a4f-144">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="59a4f-145">Os construtores normalmente inicializam os membros de dados do novo objeto.</span><span class="sxs-lookup"><span data-stu-id="59a4f-145">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="59a4f-146">Um construtor pode ser executado apenas uma vez quando uma classe é criada.</span><span class="sxs-lookup"><span data-stu-id="59a4f-146">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="59a4f-147">Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-147">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="59a4f-148">No entanto, é possível criar várias sobrecargas de construtor da mesma forma que é feita para qualquer outro método.</span><span class="sxs-lookup"><span data-stu-id="59a4f-148">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="59a4f-149">Para definir um construtor para uma classe:</span><span class="sxs-lookup"><span data-stu-id="59a4f-149">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="59a4f-150">Para saber mais, veja [Construtores](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-150">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="59a4f-151">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="59a4f-151">Finalizers</span></span>

<span data-ttu-id="59a4f-152">Um finalizador é usado para destruir instâncias de classes.</span><span class="sxs-lookup"><span data-stu-id="59a4f-152">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="59a4f-153">No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e a liberação de memória para os objetos gerenciados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="59a4f-153">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="59a4f-154">No entanto, talvez ainda seja necessário usar os finalizadores para limpar recursos não gerenciados que seu aplicativo criar.</span><span class="sxs-lookup"><span data-stu-id="59a4f-154">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="59a4f-155">Pode haver apenas um finalizador para uma classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-155">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="59a4f-156">Para obter mais informações sobre os finalizadores e a coleta de lixo no .NET Framework, consulte [Coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-156">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="59a4f-157">Eventos</span><span class="sxs-lookup"><span data-stu-id="59a4f-157">Events</span></span>

<span data-ttu-id="59a4f-158">Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer.</span><span class="sxs-lookup"><span data-stu-id="59a4f-158">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="59a4f-159">A classe que envia (ou gera) o evento é chamada de *Editor* e as classes que recebem (ou manipulam) o evento são chamadas de *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="59a4f-159">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="59a4f-160">Para obter mais informações sobre os eventos e como eles são gerados e manipulados, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-160">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="59a4f-161">Para declarar um evento em uma classe, use a palavra-chave [event](../../language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-161">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="59a4f-162">Para acionar um evento, invoque o delegado do evento.</span><span class="sxs-lookup"><span data-stu-id="59a4f-162">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="59a4f-163">Para assinar um evento, use o operador `+=`; para cancelar a assinatura de um evento, use o operador `-=`.</span><span class="sxs-lookup"><span data-stu-id="59a4f-163">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="59a4f-164">Classes aninhadas</span><span class="sxs-lookup"><span data-stu-id="59a4f-164">Nested classes</span></span>

<span data-ttu-id="59a4f-165">Uma classe definida dentro de outra classe é chamada de *aninhada*.</span><span class="sxs-lookup"><span data-stu-id="59a4f-165">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="59a4f-166">Por padrão, a classe aninhada é particular.</span><span class="sxs-lookup"><span data-stu-id="59a4f-166">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="59a4f-167">Para criar uma instância da classe aninhada, use o nome da classe de contêiner seguido pelo ponto e, em seguida, seguido pelo nome da classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="59a4f-167">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="59a4f-168">Modificadores de acesso e níveis de acesso</span><span class="sxs-lookup"><span data-stu-id="59a4f-168">Access modifiers and access levels</span></span>

<span data-ttu-id="59a4f-169">Todas as classes e membros de classe podem especificar o nível de acesso que fornecem a outras classes usando *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="59a4f-169">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="59a4f-170">Os modificadores de acesso a seguir estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="59a4f-170">The following access modifiers are available:</span></span>

|<span data-ttu-id="59a4f-171">Modificador de C#</span><span class="sxs-lookup"><span data-stu-id="59a4f-171">C# Modifier</span></span>|<span data-ttu-id="59a4f-172">Definição</span><span class="sxs-lookup"><span data-stu-id="59a4f-172">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="59a4f-173">publicada</span><span class="sxs-lookup"><span data-stu-id="59a4f-173">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="59a4f-174">O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="59a4f-174">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="59a4f-175">pessoal</span><span class="sxs-lookup"><span data-stu-id="59a4f-175">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="59a4f-176">O tipo ou membro pode ser acessado somente pelo código na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-176">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="59a4f-177">Protected</span><span class="sxs-lookup"><span data-stu-id="59a4f-177">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="59a4f-178">O tipo ou membro pode ser acessado somente pelo código na mesma classe ou em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="59a4f-178">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="59a4f-179">interno</span><span class="sxs-lookup"><span data-stu-id="59a4f-179">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="59a4f-180">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="59a4f-180">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="59a4f-181">internos protegidos</span><span class="sxs-lookup"><span data-stu-id="59a4f-181">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="59a4f-182">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly ou por qualquer classe derivada em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="59a4f-182">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="59a4f-183">particular protegido</span><span class="sxs-lookup"><span data-stu-id="59a4f-183">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="59a4f-184">O tipo ou membro pode ser acessado pelo código na mesma classe ou em uma classe derivada no assembly da classe base.</span><span class="sxs-lookup"><span data-stu-id="59a4f-184">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="59a4f-185">Para obter mais informações, consulte [Modificadores de Acesso](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-185">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="59a4f-186">Instanciando classes</span><span class="sxs-lookup"><span data-stu-id="59a4f-186">Instantiating classes</span></span>

<span data-ttu-id="59a4f-187">Para criar um objeto, você precisa instanciar uma classe ou criar uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-187">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="59a4f-188">Após instanciar uma classe, você pode atribuir valores às propriedades e campos da instância e invocar métodos da classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-188">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="59a4f-189">Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:</span><span class="sxs-lookup"><span data-stu-id="59a4f-189">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="59a4f-190">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="59a4f-190">For more information, see:</span></span>

- [<span data-ttu-id="59a4f-191">novo operador</span><span class="sxs-lookup"><span data-stu-id="59a4f-191">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="59a4f-192">Inicializadores de objeto e coleção</span><span class="sxs-lookup"><span data-stu-id="59a4f-192">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="59a4f-193">Classes e membros estáticos</span><span class="sxs-lookup"><span data-stu-id="59a4f-193">Static Classes and Members</span></span>

<span data-ttu-id="59a4f-194">Um membro estático da classe é uma propriedade, procedimento ou campo que é compartilhado por todas as instâncias de uma classe.</span><span class="sxs-lookup"><span data-stu-id="59a4f-194">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="59a4f-195">Para definir um membro estático:</span><span class="sxs-lookup"><span data-stu-id="59a4f-195">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="59a4f-196">Para acessar o membro estático, use o nome da classe sem criar um objeto dessa classe:</span><span class="sxs-lookup"><span data-stu-id="59a4f-196">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="59a4f-197">Classes estáticas em C# têm apenas membros estáticos e não podem ser instanciadas.</span><span class="sxs-lookup"><span data-stu-id="59a4f-197">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="59a4f-198">Membros estáticos também não podem acessar propriedades, métodos ou campos não estáticos</span><span class="sxs-lookup"><span data-stu-id="59a4f-198">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="59a4f-199">Para obter mais informações, consulte [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-199">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="59a4f-200">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="59a4f-200">Anonymous types</span></span>

<span data-ttu-id="59a4f-201">Os tipos anônimos permitem criar objetos sem escrever uma definição de classe para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="59a4f-201">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="59a4f-202">Em vez disso, o compilador gera uma classe para você.</span><span class="sxs-lookup"><span data-stu-id="59a4f-202">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="59a4f-203">A classe não tem nenhum nome utilizável e contém as propriedades que você especificar ao declarar o objeto.</span><span class="sxs-lookup"><span data-stu-id="59a4f-203">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="59a4f-204">Para criar uma instância de um tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="59a4f-204">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="59a4f-205">Para obter mais informações, consulte: [tipos anônimos](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-205">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="59a4f-206">Herança</span><span class="sxs-lookup"><span data-stu-id="59a4f-206">Inheritance</span></span>

<span data-ttu-id="59a4f-207">A herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento definido em outras classes.</span><span class="sxs-lookup"><span data-stu-id="59a4f-207">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="59a4f-208">A classe cujos membros são herdados é chamada *classe base* e a classe que herda esses membros é chamada *classe derivada*.</span><span class="sxs-lookup"><span data-stu-id="59a4f-208">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="59a4f-209">No entanto, todas as classes em C# herdam implicitamente da classe <xref:System.Object> que dá suporte à hierarquia de classes do .NET e fornece serviços de nível baixo para todas as classes.</span><span class="sxs-lookup"><span data-stu-id="59a4f-209">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="59a4f-210">O C# não dá suporte a várias heranças.</span><span class="sxs-lookup"><span data-stu-id="59a4f-210">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="59a4f-211">Ou seja, você pode especificar apenas uma classe base para uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="59a4f-211">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="59a4f-212">Para herdar de uma classe base:</span><span class="sxs-lookup"><span data-stu-id="59a4f-212">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="59a4f-213">Por padrão, todas as classes podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="59a4f-213">By default all classes can be inherited.</span></span> <span data-ttu-id="59a4f-214">No entanto, é possível especificar se uma classe não deve ser usada como classe base ou criar uma classe que possa ser usada apenas como classe base.</span><span class="sxs-lookup"><span data-stu-id="59a4f-214">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="59a4f-215">Para especificar que uma classe não pode ser usada como classe base:</span><span class="sxs-lookup"><span data-stu-id="59a4f-215">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="59a4f-216">Para especificar que uma classe pode ser usada apenas como classe base e não pode ser instanciada:</span><span class="sxs-lookup"><span data-stu-id="59a4f-216">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="59a4f-217">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="59a4f-217">For more information, see:</span></span>

- [<span data-ttu-id="59a4f-218">sealed</span><span class="sxs-lookup"><span data-stu-id="59a4f-218">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="59a4f-219">resume</span><span class="sxs-lookup"><span data-stu-id="59a4f-219">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="59a4f-220">Substituindo membros</span><span class="sxs-lookup"><span data-stu-id="59a4f-220">Overriding Members</span></span>

<span data-ttu-id="59a4f-221">Por padrão, uma classe derivada herda todos os membros de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="59a4f-221">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="59a4f-222">Se quiser alterar o comportamento do membro herdado, você precisa substituí-la.</span><span class="sxs-lookup"><span data-stu-id="59a4f-222">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="59a4f-223">Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="59a4f-223">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="59a4f-224">Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:</span><span class="sxs-lookup"><span data-stu-id="59a4f-224">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="59a4f-225">Modificador de C#</span><span class="sxs-lookup"><span data-stu-id="59a4f-225">C# Modifier</span></span>|<span data-ttu-id="59a4f-226">Definição</span><span class="sxs-lookup"><span data-stu-id="59a4f-226">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="59a4f-227">virtual</span><span class="sxs-lookup"><span data-stu-id="59a4f-227">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="59a4f-228">Permite que um membro de classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="59a4f-228">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="59a4f-229">override</span><span class="sxs-lookup"><span data-stu-id="59a4f-229">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="59a4f-230">Substitui um membro virtual (substituível) definido na classe base.</span><span class="sxs-lookup"><span data-stu-id="59a4f-230">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="59a4f-231">resume</span><span class="sxs-lookup"><span data-stu-id="59a4f-231">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="59a4f-232">Requer que um membro de classe seja substituído na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="59a4f-232">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="59a4f-233">Modificador new</span><span class="sxs-lookup"><span data-stu-id="59a4f-233">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="59a4f-234">Oculta um membro herdado de uma classe base</span><span class="sxs-lookup"><span data-stu-id="59a4f-234">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="59a4f-235">Interfaces</span><span class="sxs-lookup"><span data-stu-id="59a4f-235">Interfaces</span></span>

<span data-ttu-id="59a4f-236">Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="59a4f-236">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="59a4f-237">Mas, diferente das classes, as interfaces não fornecem implementação.</span><span class="sxs-lookup"><span data-stu-id="59a4f-237">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="59a4f-238">Elas são implementadas por classes e definidas como entidades separadas das classes.</span><span class="sxs-lookup"><span data-stu-id="59a4f-238">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="59a4f-239">Uma interface representa um contrato, no sentido em que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.</span><span class="sxs-lookup"><span data-stu-id="59a4f-239">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="59a4f-240">Para definir uma interface:</span><span class="sxs-lookup"><span data-stu-id="59a4f-240">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="59a4f-241">Para implementar uma interface em uma classe:</span><span class="sxs-lookup"><span data-stu-id="59a4f-241">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="59a4f-242">Para obter mais informações, consulte o artigo guia de programação em [interfaces](../interfaces/index.md) e o artigo referência de idioma na palavra-chave [interface](../../language-reference/keywords/interface.md) .</span><span class="sxs-lookup"><span data-stu-id="59a4f-242">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="59a4f-243">Genéricos</span><span class="sxs-lookup"><span data-stu-id="59a4f-243">Generics</span></span>

<span data-ttu-id="59a4f-244">Classes, estruturas, interfaces e métodos do .NET Framework podem incluir *parâmetros de tipo* que definem tipos de objetos que podem armazenar ou usar.</span><span class="sxs-lookup"><span data-stu-id="59a4f-244">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="59a4f-245">O exemplo mais comum dos genéricos é uma coleção, em que você pode especificar o tipo dos objeto a serem armazenados em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="59a4f-245">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="59a4f-246">Para definir uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="59a4f-246">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="59a4f-247">Para criar uma instância de uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="59a4f-247">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="59a4f-248">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="59a4f-248">For more information, see:</span></span>

- [<span data-ttu-id="59a4f-249">Genéricos</span><span class="sxs-lookup"><span data-stu-id="59a4f-249">Generics</span></span>](../../../standard/generics/index.md)

- [<span data-ttu-id="59a4f-250">Genéricos</span><span class="sxs-lookup"><span data-stu-id="59a4f-250">Generics</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="59a4f-251">Delegados</span><span class="sxs-lookup"><span data-stu-id="59a4f-251">Delegates</span></span>

<span data-ttu-id="59a4f-252">Um *delegado* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível.</span><span class="sxs-lookup"><span data-stu-id="59a4f-252">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="59a4f-253">Você pode invocar (ou chamar) o método através do delegado.</span><span class="sxs-lookup"><span data-stu-id="59a4f-253">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="59a4f-254">Delegados são usados para passar métodos como argumentos a outros métodos.</span><span class="sxs-lookup"><span data-stu-id="59a4f-254">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="59a4f-255">Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados.</span><span class="sxs-lookup"><span data-stu-id="59a4f-255">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="59a4f-256">Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="59a4f-256">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="59a4f-257">Para criar um delegado:</span><span class="sxs-lookup"><span data-stu-id="59a4f-257">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="59a4f-258">Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:</span><span class="sxs-lookup"><span data-stu-id="59a4f-258">To create a reference to a method that matches the signature specified by the delegate:</span></span>

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

<span data-ttu-id="59a4f-259">Para obter mais informações, consulte o artigo guia de programação em [delegados](../delegates/index.md) e o artigo referência de idioma na palavra-chave [delegate](../../language-reference/builtin-types/reference-types.md) .</span><span class="sxs-lookup"><span data-stu-id="59a4f-259">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="59a4f-260">Confira também</span><span class="sxs-lookup"><span data-stu-id="59a4f-260">See also</span></span>

- [<span data-ttu-id="59a4f-261">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="59a4f-261">C# Programming Guide</span></span>](../index.md)
