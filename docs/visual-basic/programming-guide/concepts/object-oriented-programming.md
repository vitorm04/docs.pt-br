---
title: Programação orientada a objeto
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348156"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="55022-102">Programação orientada a objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55022-102">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="55022-103">Visual Basic fornece suporte completo para a programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.</span><span class="sxs-lookup"><span data-stu-id="55022-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="55022-104">*Encapsulamento* significa que um grupo de propriedades, métodos e outros membros relacionados é tratado como uma única unidade ou objeto.</span><span class="sxs-lookup"><span data-stu-id="55022-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="55022-105">*Herança* descreve a capacidade de criar novas classes com base em uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="55022-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="55022-106">*Polimorfismo* significa que você pode ter várias classes que podem ser usadas de forma intercambiável, ainda que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="55022-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="55022-107">Esta seção descreve os seguintes conceitos:</span><span class="sxs-lookup"><span data-stu-id="55022-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="55022-108">Classes e objetos</span><span class="sxs-lookup"><span data-stu-id="55022-108">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="55022-109">Membros de classe</span><span class="sxs-lookup"><span data-stu-id="55022-109">Class members</span></span>](#class-members)
    - [<span data-ttu-id="55022-110">Propriedades e campos</span><span class="sxs-lookup"><span data-stu-id="55022-110">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="55022-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="55022-111">Methods</span></span>](#methods)
    - [<span data-ttu-id="55022-112">Construtores</span><span class="sxs-lookup"><span data-stu-id="55022-112">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="55022-113">Destruidores</span><span class="sxs-lookup"><span data-stu-id="55022-113">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="55022-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="55022-114">Events</span></span>](#events)
    - [<span data-ttu-id="55022-115">Classes aninhadas</span><span class="sxs-lookup"><span data-stu-id="55022-115">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="55022-116">Modificadores de acesso e níveis de acesso</span><span class="sxs-lookup"><span data-stu-id="55022-116">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="55022-117">Instanciando classes</span><span class="sxs-lookup"><span data-stu-id="55022-117">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="55022-118">Classes e membros compartilhados</span><span class="sxs-lookup"><span data-stu-id="55022-118">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="55022-119">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="55022-119">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="55022-120">Herança</span><span class="sxs-lookup"><span data-stu-id="55022-120">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="55022-121">Substituindo membros</span><span class="sxs-lookup"><span data-stu-id="55022-121">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="55022-122">Interfaces</span><span class="sxs-lookup"><span data-stu-id="55022-122">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="55022-123">Genéricos</span><span class="sxs-lookup"><span data-stu-id="55022-123">Generics</span></span>](#generics)
- [<span data-ttu-id="55022-124">Delegados</span><span class="sxs-lookup"><span data-stu-id="55022-124">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="55022-125">Classes e objetos</span><span class="sxs-lookup"><span data-stu-id="55022-125">Classes and objects</span></span>

<span data-ttu-id="55022-126">Os termos *classe* e *objeto* às vezes são usados de forma intercambiável, mas, na verdade, as classes descrevem o *tipo* dos objetos, enquanto os objetos são *instâncias* utilizáveis das classes.</span><span class="sxs-lookup"><span data-stu-id="55022-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="55022-127">Sendo assim, o ato de criar um objeto é chamado de *instanciação*.</span><span class="sxs-lookup"><span data-stu-id="55022-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="55022-128">Usando a analogia da uma planta, uma classe é a planta e um objeto é a construção feita com base naquela planta.</span><span class="sxs-lookup"><span data-stu-id="55022-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="55022-129">Para definir uma classe:</span><span class="sxs-lookup"><span data-stu-id="55022-129">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="55022-130">O Visual Basic também fornece uma versão leve das classes chamadas *estruturas* que são úteis quando você precisa criar uma grande matriz de objetos e não deseja consumir muita memória para isso.</span><span class="sxs-lookup"><span data-stu-id="55022-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="55022-131">Para definir uma estrutura:</span><span class="sxs-lookup"><span data-stu-id="55022-131">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="55022-132">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-132">For more information, see:</span></span>

- [<span data-ttu-id="55022-133">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="55022-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="55022-134">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="55022-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="55022-135">Membros de classe</span><span class="sxs-lookup"><span data-stu-id="55022-135">Class members</span></span>

<span data-ttu-id="55022-136">Cada classe tem diferentes *membros de classe* que incluem propriedades que descrevem dados da classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="55022-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="55022-137">Propriedades e campos</span><span class="sxs-lookup"><span data-stu-id="55022-137">Properties and fields</span></span>

<span data-ttu-id="55022-138">Os campos e as propriedades representam as informações que um objeto contém.</span><span class="sxs-lookup"><span data-stu-id="55022-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="55022-139">Os campos são como variáveis, porque podem ser lidos ou definidos de forma direta.</span><span class="sxs-lookup"><span data-stu-id="55022-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="55022-140">Para definir um campo:</span><span class="sxs-lookup"><span data-stu-id="55022-140">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="55022-141">As propriedades têm procedimentos de obter e definir, que oferecem mais controle sobre como os valores são definidos ou retornados.</span><span class="sxs-lookup"><span data-stu-id="55022-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="55022-142">Visual Basic permite que você crie um campo particular para armazenar o valor da propriedade ou use as chamadas de propriedades implementadas automaticamente que criam esse campo automaticamente nos bastidores e fornecem a lógica básica para os procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="55022-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="55022-143">Para definir uma propriedade autoimplementada:</span><span class="sxs-lookup"><span data-stu-id="55022-143">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="55022-144">Se você precisar executar operações adicionais para ler e gravar o valor da propriedade, defina um campo para armazenar o valor da propriedade e forneça a lógica básica para armazenar e recuperá-la:</span><span class="sxs-lookup"><span data-stu-id="55022-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="55022-145">A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="55022-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="55022-146">No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas.</span><span class="sxs-lookup"><span data-stu-id="55022-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="55022-147">No Visual Basic você pode usar `ReadOnly` e `WriteOnly` palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="55022-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="55022-148">No entanto, propriedades autoimplementadas não podem ser somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="55022-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="55022-149">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-149">For more information, see:</span></span>

- [<span data-ttu-id="55022-150">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="55022-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="55022-151">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="55022-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="55022-152">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="55022-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="55022-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="55022-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="55022-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="55022-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="55022-155">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="55022-155">Methods</span></span>

 <span data-ttu-id="55022-156">Um *método* é uma ação que um objeto pode executar.</span><span class="sxs-lookup"><span data-stu-id="55022-156">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="55022-157">Em Visual Basic, há duas maneiras de criar um método: a instrução `Sub` será usada se o método não retornar um valor; a instrução `Function` será usada se um método retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="55022-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="55022-158">Para definir um método de uma classe:</span><span class="sxs-lookup"><span data-stu-id="55022-158">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="55022-159">Uma classe pode ter várias implementações ou *sobrecargas*, do mesmo método que diferem quanto ao número de parâmetros ou tipos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="55022-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="55022-160">Para sobrecarregar um método:</span><span class="sxs-lookup"><span data-stu-id="55022-160">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="55022-161">Na maioria dos casos, você declara um método dentro de uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="55022-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="55022-162">No entanto, Visual Basic também dá suporte a *métodos de extensão* que permitem adicionar métodos a uma classe existente fora da definição real da classe.</span><span class="sxs-lookup"><span data-stu-id="55022-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="55022-163">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-163">For more information, see:</span></span>

- [<span data-ttu-id="55022-164">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="55022-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="55022-165">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="55022-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="55022-166">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="55022-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="55022-167">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="55022-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="55022-168">{1&gt;Construtores&lt;1}</span><span class="sxs-lookup"><span data-stu-id="55022-168">Constructors</span></span>

<span data-ttu-id="55022-169">Construtores são métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado.</span><span class="sxs-lookup"><span data-stu-id="55022-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="55022-170">Os construtores normalmente inicializam os membros de dados do novo objeto.</span><span class="sxs-lookup"><span data-stu-id="55022-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="55022-171">Um construtor pode ser executado apenas uma vez quando uma classe é criada.</span><span class="sxs-lookup"><span data-stu-id="55022-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="55022-172">Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe.</span><span class="sxs-lookup"><span data-stu-id="55022-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="55022-173">No entanto, é possível criar várias sobrecargas de construtor da mesma forma que é feita para qualquer outro método.</span><span class="sxs-lookup"><span data-stu-id="55022-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="55022-174">Para definir um construtor para uma classe:</span><span class="sxs-lookup"><span data-stu-id="55022-174">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="55022-175">Para obter mais informações, consulte: [tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="55022-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="55022-176">Destruidores</span><span class="sxs-lookup"><span data-stu-id="55022-176">Destructors</span></span>

<span data-ttu-id="55022-177">Destruidores são usados para destruir instâncias de classes.</span><span class="sxs-lookup"><span data-stu-id="55022-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="55022-178">No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e a liberação de memória para os objetos gerenciados em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55022-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="55022-179">No entanto, talvez ainda seja necessário usar os destruidores para limpar recursos não gerenciados que seu aplicativo criar.</span><span class="sxs-lookup"><span data-stu-id="55022-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="55022-180">Pode haver apenas um destruidor para uma classe.</span><span class="sxs-lookup"><span data-stu-id="55022-180">There can be only one destructor for a class.</span></span>

<span data-ttu-id="55022-181">Para obter mais informações sobre os destruidores e a coleta de lixo no .NET Framework, consulte [Coleta de lixo](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="55022-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="55022-182">Eventos</span><span class="sxs-lookup"><span data-stu-id="55022-182">Events</span></span>

<span data-ttu-id="55022-183">Eventos permitem que uma classe ou objeto notifique outras classes ou objetos quando algo interessante ocorrer.</span><span class="sxs-lookup"><span data-stu-id="55022-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="55022-184">A classe que envia (ou aciona) o evento é chamada de *editor* e as classes que recebem (ou manipulam) os eventos são chamadas *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="55022-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="55022-185">Para obter mais informações sobre os eventos e como eles são gerados e manipulados, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="55022-185">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="55022-186">Para declarar eventos, use a [instrução de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="55022-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="55022-187">Para gerar eventos, use a [instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="55022-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="55022-188">Para especificar os manipuladores de eventos usando uma forma declarativa, use a instrução [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) e a cláusula [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="55022-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="55022-189">Para poder adicionar, remover e alterar dinamicamente o manipulador de eventos associado a um evento, use a [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) e a [instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) junto com o [operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="55022-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="55022-190">Classes aninhadas</span><span class="sxs-lookup"><span data-stu-id="55022-190">Nested classes</span></span>

<span data-ttu-id="55022-191">Uma classe definida dentro de outra classe é chamada de *aninhada*.</span><span class="sxs-lookup"><span data-stu-id="55022-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="55022-192">Por padrão, a classe aninhada é particular.</span><span class="sxs-lookup"><span data-stu-id="55022-192">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="55022-193">Para criar uma instância da classe aninhada, use o nome da classe de contêiner seguido pelo ponto e, em seguida, seguido pelo nome da classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="55022-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="55022-194">Modificadores de acesso e níveis de acesso</span><span class="sxs-lookup"><span data-stu-id="55022-194">Access modifiers and access levels</span></span>

<span data-ttu-id="55022-195">Todas as classes e membros de classe podem especificar o nível de acesso que fornecem a outras classes usando *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="55022-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="55022-196">Os modificadores de acesso a seguir estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="55022-196">The following access modifiers are available:</span></span>

|<span data-ttu-id="55022-197">Modificador de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55022-197">Visual Basic Modifier</span></span>|<span data-ttu-id="55022-198">Definição</span><span class="sxs-lookup"><span data-stu-id="55022-198">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="55022-199">Público</span><span class="sxs-lookup"><span data-stu-id="55022-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="55022-200">O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="55022-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="55022-201">Privado</span><span class="sxs-lookup"><span data-stu-id="55022-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="55022-202">O tipo ou membro pode ser acessado somente pelo código na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="55022-202">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="55022-203">Protegido</span><span class="sxs-lookup"><span data-stu-id="55022-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="55022-204">O tipo ou membro pode ser acessado somente pelo código na mesma classe ou em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="55022-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="55022-205">Friend</span><span class="sxs-lookup"><span data-stu-id="55022-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="55022-206">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="55022-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="55022-207">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly ou por qualquer classe derivada em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="55022-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="55022-208">Para obter mais informações, consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="55022-208">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="55022-209">Instanciando classes</span><span class="sxs-lookup"><span data-stu-id="55022-209">Instantiating classes</span></span>

<span data-ttu-id="55022-210">Para criar um objeto, você precisa instanciar uma classe ou criar uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="55022-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="55022-211">Após instanciar uma classe, você pode atribuir valores às propriedades e campos da instância e invocar métodos da classe.</span><span class="sxs-lookup"><span data-stu-id="55022-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="55022-212">Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:</span><span class="sxs-lookup"><span data-stu-id="55022-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="55022-213">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-213">For more information, see:</span></span>

- [<span data-ttu-id="55022-214">Operador New</span><span class="sxs-lookup"><span data-stu-id="55022-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="55022-215">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="55022-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="55022-216">Classes e membros compartilhados</span><span class="sxs-lookup"><span data-stu-id="55022-216">Shared classes and members</span></span>

 <span data-ttu-id="55022-217">Um membro compartilhado da classe é uma propriedade, um procedimento ou um campo que é compartilhado por todas as instâncias de uma classe.</span><span class="sxs-lookup"><span data-stu-id="55022-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="55022-218">Para definir um membro compartilhado:</span><span class="sxs-lookup"><span data-stu-id="55022-218">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="55022-219">Para acessar o membro compartilhado, use o nome da classe sem criar um objeto desta classe:</span><span class="sxs-lookup"><span data-stu-id="55022-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="55022-220">Os módulos compartilhados no Visual Basic têm somente membros compartilhados e não podem ser instanciados.</span><span class="sxs-lookup"><span data-stu-id="55022-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="55022-221">Membros compartilhados também não podem acessar propriedades, campos ou métodos não compartilhados</span><span class="sxs-lookup"><span data-stu-id="55022-221">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="55022-222">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-222">For more information, see:</span></span>

- [<span data-ttu-id="55022-223">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="55022-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="55022-224">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="55022-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="55022-225">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="55022-225">Anonymous types</span></span>

<span data-ttu-id="55022-226">Os tipos anônimos permitem criar objetos sem escrever uma definição de classe para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="55022-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="55022-227">Em vez disso, o compilador gera uma classe para você.</span><span class="sxs-lookup"><span data-stu-id="55022-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="55022-228">A classe não tem nenhum nome utilizável e contém as propriedades que você especificar ao declarar o objeto.</span><span class="sxs-lookup"><span data-stu-id="55022-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="55022-229">Para criar uma instância de um tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="55022-229">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="55022-230">Para obter mais informações, consulte [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="55022-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="55022-231">{1&gt;Herança&lt;1}</span><span class="sxs-lookup"><span data-stu-id="55022-231">Inheritance</span></span>

<span data-ttu-id="55022-232">A herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento definido em outras classes.</span><span class="sxs-lookup"><span data-stu-id="55022-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="55022-233">A classe cujos membros são herdados é chamada *classe base* e a classe que herda esses membros é chamada *classe derivada*.</span><span class="sxs-lookup"><span data-stu-id="55022-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="55022-234">No entanto, todas as classes em Visual Basic herdam implicitamente da classe <xref:System.Object> que oferece suporte à hierarquia de classes .NET e fornece serviços de nível baixo a todas as classes.</span><span class="sxs-lookup"><span data-stu-id="55022-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="55022-235">Visual Basic não dá suporte a várias heranças.</span><span class="sxs-lookup"><span data-stu-id="55022-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="55022-236">Ou seja, você pode especificar apenas uma classe base para uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="55022-236">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="55022-237">Para herdar de uma classe base:</span><span class="sxs-lookup"><span data-stu-id="55022-237">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="55022-238">Por padrão, todas as classes podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="55022-238">By default all classes can be inherited.</span></span> <span data-ttu-id="55022-239">No entanto, é possível especificar se uma classe não deve ser usada como classe base ou criar uma classe que possa ser usada apenas como classe base.</span><span class="sxs-lookup"><span data-stu-id="55022-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="55022-240">Para especificar que uma classe não pode ser usada como classe base:</span><span class="sxs-lookup"><span data-stu-id="55022-240">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="55022-241">Para especificar que uma classe pode ser usada apenas como classe base e não pode ser instanciada:</span><span class="sxs-lookup"><span data-stu-id="55022-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="55022-242">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-242">For more information, see:</span></span>

- [<span data-ttu-id="55022-243">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="55022-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="55022-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="55022-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="55022-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="55022-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="55022-246">Substituindo membros</span><span class="sxs-lookup"><span data-stu-id="55022-246">Overriding members</span></span>

<span data-ttu-id="55022-247">Por padrão, uma classe derivada herda todos os membros de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="55022-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="55022-248">Se quiser alterar o comportamento do membro herdado, você precisa substituí-la.</span><span class="sxs-lookup"><span data-stu-id="55022-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="55022-249">Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="55022-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="55022-250">Os seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:</span><span class="sxs-lookup"><span data-stu-id="55022-250">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="55022-251">Modificador de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55022-251">Visual Basic Modifier</span></span>|<span data-ttu-id="55022-252">Definição</span><span class="sxs-lookup"><span data-stu-id="55022-252">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="55022-253">Substituível</span><span class="sxs-lookup"><span data-stu-id="55022-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="55022-254">Permite que um membro de classe seja substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="55022-254">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="55022-255">Substituições</span><span class="sxs-lookup"><span data-stu-id="55022-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="55022-256">Substitui um membro virtual (substituível) definido na classe base.</span><span class="sxs-lookup"><span data-stu-id="55022-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="55022-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="55022-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="55022-258">Impede que um membro seja substituído em uma classe de herança.</span><span class="sxs-lookup"><span data-stu-id="55022-258">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="55022-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="55022-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="55022-260">Requer que um membro de classe seja substituído na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="55022-260">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="55022-261">Sombras</span><span class="sxs-lookup"><span data-stu-id="55022-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="55022-262">Oculta um membro herdado de uma classe base</span><span class="sxs-lookup"><span data-stu-id="55022-262">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="55022-263">Interfaces</span><span class="sxs-lookup"><span data-stu-id="55022-263">Interfaces</span></span>

<span data-ttu-id="55022-264">Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="55022-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="55022-265">Mas, diferente das classes, as interfaces não fornecem implementação.</span><span class="sxs-lookup"><span data-stu-id="55022-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="55022-266">Elas são implementadas por classes e definidas como entidades separadas das classes.</span><span class="sxs-lookup"><span data-stu-id="55022-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="55022-267">Uma interface representa um contrato, no sentido em que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.</span><span class="sxs-lookup"><span data-stu-id="55022-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="55022-268">Para definir uma interface:</span><span class="sxs-lookup"><span data-stu-id="55022-268">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="55022-269">Para implementar uma interface em uma classe:</span><span class="sxs-lookup"><span data-stu-id="55022-269">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="55022-270">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-270">For more information, see:</span></span>

- [<span data-ttu-id="55022-271">Interfaces</span><span class="sxs-lookup"><span data-stu-id="55022-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [<span data-ttu-id="55022-272">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="55022-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="55022-273">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="55022-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="55022-274">Genéricos</span><span class="sxs-lookup"><span data-stu-id="55022-274">Generics</span></span>

<span data-ttu-id="55022-275">Classes, estruturas, interfaces e métodos no .NET podem incluir *parâmetros de tipo* que definem tipos de objetos que eles podem armazenar ou usar.</span><span class="sxs-lookup"><span data-stu-id="55022-275">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="55022-276">O exemplo mais comum dos genéricos é uma coleção, em que você pode especificar o tipo dos objeto a serem armazenados em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="55022-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="55022-277">Para definir uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="55022-277">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="55022-278">Para criar uma instância de uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="55022-278">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="55022-279">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-279">For more information, see:</span></span>

- [<span data-ttu-id="55022-280">Genéricos</span><span class="sxs-lookup"><span data-stu-id="55022-280">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="55022-281">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55022-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="55022-282">Delegados</span><span class="sxs-lookup"><span data-stu-id="55022-282">Delegates</span></span>

 <span data-ttu-id="55022-283">Um *delegado* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível.</span><span class="sxs-lookup"><span data-stu-id="55022-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="55022-284">Você pode invocar (ou chamar) o método através do delegado.</span><span class="sxs-lookup"><span data-stu-id="55022-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="55022-285">Delegados são usados para passar métodos como argumentos a outros métodos.</span><span class="sxs-lookup"><span data-stu-id="55022-285">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="55022-286">Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados.</span><span class="sxs-lookup"><span data-stu-id="55022-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="55022-287">Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [Eventos](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="55022-287">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="55022-288">Para criar um delegado:</span><span class="sxs-lookup"><span data-stu-id="55022-288">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="55022-289">Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:</span><span class="sxs-lookup"><span data-stu-id="55022-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="55022-290">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="55022-290">For more information, see:</span></span>

- [<span data-ttu-id="55022-291">Delegados</span><span class="sxs-lookup"><span data-stu-id="55022-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="55022-292">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="55022-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="55022-293">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="55022-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="55022-294">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55022-294">See also</span></span>

- [<span data-ttu-id="55022-295">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55022-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
