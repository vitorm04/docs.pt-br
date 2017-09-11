---
title: "Programação orientada a objeto (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5491b3bd5a25908194d02063f688a319509bb77
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="3b20d-102">Programação orientada a objeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b20d-102">Object-Oriented Programming (Visual Basic)</span></span>
<span data-ttu-id="3b20d-103">Visual Basic fornece suporte completo para a programação orientada a objeto, incluindo encapsulamento, herança e polimorfismo.</span><span class="sxs-lookup"><span data-stu-id="3b20d-103">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="3b20d-104">*Encapsulamento* significa que um grupo de propriedades relacionadas, métodos e outros membros são tratados como uma única unidade ou um objeto.</span><span class="sxs-lookup"><span data-stu-id="3b20d-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="3b20d-105">*Herança* descreve a capacidade de criar novas classes com base em uma classe existente.</span><span class="sxs-lookup"><span data-stu-id="3b20d-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="3b20d-106">*Polimorfismo* significa que você pode ter várias classes que podem ser usadas intercambiavelmente, mesmo que cada classe implemente as mesmas propriedades ou métodos de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="3b20d-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="3b20d-107">Esta seção descreve os seguintes conceitos:</span><span class="sxs-lookup"><span data-stu-id="3b20d-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="3b20d-108">Classes e objetos</span><span class="sxs-lookup"><span data-stu-id="3b20d-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="3b20d-109">Membros de classe</span><span class="sxs-lookup"><span data-stu-id="3b20d-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="3b20d-110">Campos e propriedades</span><span class="sxs-lookup"><span data-stu-id="3b20d-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="3b20d-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="3b20d-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="3b20d-112">Construtores</span><span class="sxs-lookup"><span data-stu-id="3b20d-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="3b20d-113">Destruidores</span><span class="sxs-lookup"><span data-stu-id="3b20d-113">Destructors</span></span>](#Destructors)  
  
         [<span data-ttu-id="3b20d-114">Eventos</span><span class="sxs-lookup"><span data-stu-id="3b20d-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="3b20d-115">Classes aninhadas</span><span class="sxs-lookup"><span data-stu-id="3b20d-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="3b20d-116">Modificadores de acesso e níveis de acesso</span><span class="sxs-lookup"><span data-stu-id="3b20d-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="3b20d-117">Instanciação de Classes</span><span class="sxs-lookup"><span data-stu-id="3b20d-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="3b20d-118">Classes compartilhadas e membros</span><span class="sxs-lookup"><span data-stu-id="3b20d-118">Shared Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="3b20d-119">Tipos Anônimos</span><span class="sxs-lookup"><span data-stu-id="3b20d-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="3b20d-120">Herança</span><span class="sxs-lookup"><span data-stu-id="3b20d-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="3b20d-121">Substituindo membros</span><span class="sxs-lookup"><span data-stu-id="3b20d-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="3b20d-122">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3b20d-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="3b20d-123">Genéricos</span><span class="sxs-lookup"><span data-stu-id="3b20d-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="3b20d-124">Delegados</span><span class="sxs-lookup"><span data-stu-id="3b20d-124">Delegates</span></span>](#Delegates)  
  
##  <span data-ttu-id="3b20d-125"><a name="Classes"></a>Classes e objetos</span><span class="sxs-lookup"><span data-stu-id="3b20d-125"><a name="Classes"></a> Classes and Objects</span></span>  
 <span data-ttu-id="3b20d-126">Os termos de *classe* e *objeto* são às vezes usados alternadamente, mas na verdade, as classes descrevem o *tipo* de objetos, enquanto objetos são utilizáveis *instâncias* de classes.</span><span class="sxs-lookup"><span data-stu-id="3b20d-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="3b20d-127">Assim, o ato de criar um objeto é chamado *instanciação*.</span><span class="sxs-lookup"><span data-stu-id="3b20d-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="3b20d-128">Usando a analogia da planta, uma classe é a planta e um objeto é a construção feita daquela planta.</span><span class="sxs-lookup"><span data-stu-id="3b20d-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="3b20d-129">Para definir uma classe:</span><span class="sxs-lookup"><span data-stu-id="3b20d-129">To define a class:</span></span>  
  
```vb  
Class SampleClass  
End Class  
```  
  
 <span data-ttu-id="3b20d-130">Visual Basic também fornece uma versão leve de classes chamado *estruturas* que são úteis quando você precisa criar uma matriz grande de objetos e não deseja consumir muita memória para isso.</span><span class="sxs-lookup"><span data-stu-id="3b20d-130">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="3b20d-131">Para definir uma estrutura:</span><span class="sxs-lookup"><span data-stu-id="3b20d-131">To define a structure:</span></span>  
  
```vb  
Structure SampleStructure  
End Structure  
```  
  
 <span data-ttu-id="3b20d-132">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-133">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="3b20d-133">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [<span data-ttu-id="3b20d-134">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="3b20d-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
###  <span data-ttu-id="3b20d-135"><a name="Members"></a>Membros de classe</span><span class="sxs-lookup"><span data-stu-id="3b20d-135"><a name="Members"></a> Class Members</span></span>  
 <span data-ttu-id="3b20d-136">Cada classe pode ter diferentes *membros de classe* que incluem propriedades que descrevem os dados de classe, métodos que definem o comportamento da classe e eventos que fornecem comunicação entre diferentes classes e objetos.</span><span class="sxs-lookup"><span data-stu-id="3b20d-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <span data-ttu-id="3b20d-137"><a name="Properties"></a>Campos e propriedades</span><span class="sxs-lookup"><span data-stu-id="3b20d-137"><a name="Properties"></a> Properties and Fields</span></span>  
 <span data-ttu-id="3b20d-138">Campos e propriedades representam informações que um objeto contém.</span><span class="sxs-lookup"><span data-stu-id="3b20d-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="3b20d-139">Campos são como variáveis, porque eles podem ser lidos ou definidos diretamente.</span><span class="sxs-lookup"><span data-stu-id="3b20d-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="3b20d-140">Para definir um campo:</span><span class="sxs-lookup"><span data-stu-id="3b20d-140">To define a field:</span></span>  
  
```vb  
Class SampleClass  
    Public SampleField As String  
End Class  
```  
  
 <span data-ttu-id="3b20d-141">Propriedades têm get e definir procedimentos, que oferecem mais controle sobre como os valores são definidos ou retornados.</span><span class="sxs-lookup"><span data-stu-id="3b20d-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="3b20d-142">Visual Basic permite que você crie um campo particular para armazenar o valor da propriedade ou use chamadas propriedades implementadas automaticamente que criar esse campo automaticamente em segundo plano e fornecerem a lógica básica para os procedimentos de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3b20d-142">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="3b20d-143">Para definir uma propriedade implementada automaticamente:</span><span class="sxs-lookup"><span data-stu-id="3b20d-143">To define an auto-implemented property:</span></span>  
  
```vb  
Class SampleClass  
    Public Property SampleProperty as String  
End Class  
```  
  
 <span data-ttu-id="3b20d-144">Se você precisa executar algumas operações adicionais para ler e gravar o valor de propriedade, defina um campo para armazenar o valor da propriedade e fornecer a lógica básica para armazenar e recuperar:</span><span class="sxs-lookup"><span data-stu-id="3b20d-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
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
  
 <span data-ttu-id="3b20d-145">A maioria das propriedades têm métodos ou procedimentos para definir e obter o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="3b20d-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="3b20d-146">No entanto, você pode criar propriedades somente leitura ou somente gravação para impedir que elas sejam modificadas ou lidas.</span><span class="sxs-lookup"><span data-stu-id="3b20d-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="3b20d-147">No Visual Basic, você pode usar `ReadOnly` e `WriteOnly` palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="3b20d-147">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="3b20d-148">No entanto, as propriedades implementadas automaticamente não podem ser somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="3b20d-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="3b20d-149">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-150">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="3b20d-150">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="3b20d-151">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="3b20d-151">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [<span data-ttu-id="3b20d-152">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="3b20d-152">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [<span data-ttu-id="3b20d-153">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="3b20d-153">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [<span data-ttu-id="3b20d-154">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="3b20d-154">WriteOnly</span></span>](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
####  <span data-ttu-id="3b20d-155"><a name="Methods"></a> Métodos</span><span class="sxs-lookup"><span data-stu-id="3b20d-155"><a name="Methods"></a> Methods</span></span>  
 <span data-ttu-id="3b20d-156">A *método* é uma ação que um objeto pode executar.</span><span class="sxs-lookup"><span data-stu-id="3b20d-156">A *method* is an action that an object can perform.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b20d-157">No Visual Basic, existem duas maneiras de criar um método: o `Sub` instrução é usada se o método retornar um valor; o `Function` instrução é usada se um método retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="3b20d-157">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>  
  
 <span data-ttu-id="3b20d-158">Para definir um método de uma classe:</span><span class="sxs-lookup"><span data-stu-id="3b20d-158">To define a method of a class:</span></span>  
  
```vb  
Class SampleClass  
    Public Function SampleFunc(ByVal SampleParam As String)  
        ' Add code here  
    End Function  
End Class  
```  
  
 <span data-ttu-id="3b20d-159">Uma classe pode ter várias implementações, ou *sobrecargas*, do mesmo método que diferem no número de parâmetros ou tipos de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="3b20d-159">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="3b20d-160">Para sobrecarregar um método:</span><span class="sxs-lookup"><span data-stu-id="3b20d-160">To overload a method:</span></span>  
  
```vb  
Overloads Sub Display(ByVal theChar As Char)  
    ' Add code that displays Char data.  
End Sub  
Overloads Sub Display(ByVal theInteger As Integer)  
    ' Add code that displays Integer data.  
End Sub  
```  
  
 <span data-ttu-id="3b20d-161">Na maioria dos casos você declarar um método dentro de uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-161">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="3b20d-162">No entanto, o Visual Basic também ofereça suporte *métodos de extensão* que permitem que você adicione métodos a uma classe existente fora a definição real da classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-162">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="3b20d-163">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-163">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-164">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="3b20d-164">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="3b20d-165">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="3b20d-165">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [<span data-ttu-id="3b20d-166">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="3b20d-166">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
-   [<span data-ttu-id="3b20d-167">Métodos de Extensão</span><span class="sxs-lookup"><span data-stu-id="3b20d-167">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
  
####  <span data-ttu-id="3b20d-168"><a name="Constructors"></a> Construtores</span><span class="sxs-lookup"><span data-stu-id="3b20d-168"><a name="Constructors"></a> Constructors</span></span>  
 <span data-ttu-id="3b20d-169">Construtores são os métodos de classe que são executados automaticamente quando um objeto de um determinado tipo é criado.</span><span class="sxs-lookup"><span data-stu-id="3b20d-169">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="3b20d-170">Construtores geralmente inicializam os membros de dados do novo objeto.</span><span class="sxs-lookup"><span data-stu-id="3b20d-170">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="3b20d-171">Um construtor pode executar apenas uma vez quando uma classe é criada.</span><span class="sxs-lookup"><span data-stu-id="3b20d-171">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="3b20d-172">Além disso, o código no construtor sempre é executado antes de qualquer outro código em uma classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-172">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="3b20d-173">No entanto, você pode criar várias sobrecargas de construtor da mesma forma e qualquer outro método.</span><span class="sxs-lookup"><span data-stu-id="3b20d-173">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="3b20d-174">Para definir um construtor para uma classe:</span><span class="sxs-lookup"><span data-stu-id="3b20d-174">To define a constructor for a class:</span></span>  
  
```vb  
Class SampleClass  
    Sub New(ByVal s As String)  
        // Add code here.  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="3b20d-175">Para obter mais informações, consulte: [tempo de vida do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="3b20d-175">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
####  <span data-ttu-id="3b20d-176"><a name="Destructors"></a>Destruidores</span><span class="sxs-lookup"><span data-stu-id="3b20d-176"><a name="Destructors"></a> Destructors</span></span>  
 <span data-ttu-id="3b20d-177">Destruidores são usados para destruct instâncias de classes.</span><span class="sxs-lookup"><span data-stu-id="3b20d-177">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="3b20d-178">No .NET Framework, o coletor de lixo gerencia automaticamente a alocação e liberação de memória para os objetos gerenciados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3b20d-178">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="3b20d-179">No entanto, talvez ainda seja necessário usar destruidores para limpar os recursos não gerenciados que seu aplicativo cria.</span><span class="sxs-lookup"><span data-stu-id="3b20d-179">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="3b20d-180">Pode haver apenas um destruidor para uma classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-180">There can be only one destructor for a class.</span></span>  
  
 <span data-ttu-id="3b20d-181">Para obter mais informações sobre destruidores e coleta de lixo no .NET Framework, consulte [coleta de lixo](../../../standard/garbagecollection/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b20d-181">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbagecollection/index.md).</span></span>  
  
####  <span data-ttu-id="3b20d-182"><a name="Events"></a> Eventos</span><span class="sxs-lookup"><span data-stu-id="3b20d-182"><a name="Events"></a> Events</span></span>  
 <span data-ttu-id="3b20d-183">Eventos permitem que uma classe ou objeto para notificar outras classes ou objetos quando algo interessante ocorre.</span><span class="sxs-lookup"><span data-stu-id="3b20d-183">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="3b20d-184">A classe que envia (ou gera) o evento é chamada de *publisher* e as classes de evento receberem (ou manipularem) são chamadas *assinantes*.</span><span class="sxs-lookup"><span data-stu-id="3b20d-184">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="3b20d-185">Para obter mais informações sobre eventos, como eles são gerados e manipulados, consulte [eventos](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).</span><span class="sxs-lookup"><span data-stu-id="3b20d-185">For more information about events, how they are raised and handled, see [Events](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).</span></span>  
  
-   <span data-ttu-id="3b20d-186">Para declarar eventos, use o [declaração de evento](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b20d-186">To declare events, use the [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
-   <span data-ttu-id="3b20d-187">Para gerar eventos, use o [instrução RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3b20d-187">To raise events, use the [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
-   <span data-ttu-id="3b20d-188">Para especificar os manipuladores de eventos usando uma forma declarativa, use o [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) instrução e o [manipula](../../../visual-basic/language-reference/statements/handles-clause.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="3b20d-188">To specify event handlers using a declarative way, use the [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) statement and the [Handles](../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span>  
  
-   <span data-ttu-id="3b20d-189">Para poder adicionar, remover e alterar o manipulador de eventos associado a um evento dinamicamente, use o [instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) e [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) junto com o [operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3b20d-189">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md).</span></span>  
  
####  <span data-ttu-id="3b20d-190"><a name="NestedClasses"></a>Classes aninhadas</span><span class="sxs-lookup"><span data-stu-id="3b20d-190"><a name="NestedClasses"></a> Nested Classes</span></span>  
 <span data-ttu-id="3b20d-191">Uma classe definida dentro de outra classe é chamada *aninhada*.</span><span class="sxs-lookup"><span data-stu-id="3b20d-191">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="3b20d-192">Por padrão, a classe aninhada é particular.</span><span class="sxs-lookup"><span data-stu-id="3b20d-192">By default, the nested class is private.</span></span>  
  
```vb  
Class Container  
    Class Nested  
    ' Add code here.  
    End Class  
End Class  
```  
  
 <span data-ttu-id="3b20d-193">Para criar uma instância da classe aninhada, use o nome da classe de contêiner, seguido do ponto e, em seguida, seguido do nome da classe aninhada:</span><span class="sxs-lookup"><span data-stu-id="3b20d-193">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```vb  
Dim nestedInstance As Container.Nested = New Container.Nested()  
```  
  
###  <span data-ttu-id="3b20d-194"><a name="AccessModifiers"></a>Modificadores de acesso e níveis de acesso</span><span class="sxs-lookup"><span data-stu-id="3b20d-194"><a name="AccessModifiers"></a> Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="3b20d-195">Todas as classes e membros de classe podem especificar o nível de acesso que eles fornecem a outras classes usando *modificadores de acesso*.</span><span class="sxs-lookup"><span data-stu-id="3b20d-195">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="3b20d-196">Os modificadores de acesso a seguir estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="3b20d-196">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="3b20d-197">Modificador de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b20d-197">Visual Basic Modifier</span></span>|<span data-ttu-id="3b20d-198">Definição</span><span class="sxs-lookup"><span data-stu-id="3b20d-198">Definition</span></span>|  
|---------------------------|----------------|  
|[<span data-ttu-id="3b20d-199">Público</span><span class="sxs-lookup"><span data-stu-id="3b20d-199">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)|<span data-ttu-id="3b20d-200">O tipo ou membro pode ser acessado por qualquer outro código no mesmo assembly ou em outro assembly que faz referência a ele.</span><span class="sxs-lookup"><span data-stu-id="3b20d-200">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="3b20d-201">Privado</span><span class="sxs-lookup"><span data-stu-id="3b20d-201">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)|<span data-ttu-id="3b20d-202">O tipo ou membro só pode ser acessado pelo código na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-202">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="3b20d-203">Protegido</span><span class="sxs-lookup"><span data-stu-id="3b20d-203">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)|<span data-ttu-id="3b20d-204">O tipo ou membro só pode ser acessado pelo código na mesma classe ou em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3b20d-204">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="3b20d-205">Friend</span><span class="sxs-lookup"><span data-stu-id="3b20d-205">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)|<span data-ttu-id="3b20d-206">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, mas não de outro assembly.</span><span class="sxs-lookup"><span data-stu-id="3b20d-206">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|`Protected Friend`|<span data-ttu-id="3b20d-207">O tipo ou membro pode ser acessado por qualquer código no mesmo assembly, ou por qualquer classe derivada em outro assembly.</span><span class="sxs-lookup"><span data-stu-id="3b20d-207">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
  
 <span data-ttu-id="3b20d-208">Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3b20d-208">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
###  <span data-ttu-id="3b20d-209"><a name="InstantiatingClasses"></a>Instanciação de Classes</span><span class="sxs-lookup"><span data-stu-id="3b20d-209"><a name="InstantiatingClasses"></a> Instantiating Classes</span></span>  
 <span data-ttu-id="3b20d-210">Para criar um objeto, você precisa criar uma instância de uma classe, ou criar uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-210">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```vb  
Dim sampleObject as New SampleClass()  
```  
  
 <span data-ttu-id="3b20d-211">Depois de instanciar uma classe, você pode atribuir valores a propriedades e campos de instância e chamar os métodos da classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-211">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```vb  
' Set a property value.  
sampleObject.SampleProperty = "Sample String"  
' Call a method.  
sampleObject.SampleMethod()  
```  
  
 <span data-ttu-id="3b20d-212">Para atribuir valores a propriedades durante o processo de instanciação de classe, use os inicializadores de objeto:</span><span class="sxs-lookup"><span data-stu-id="3b20d-212">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```vb  
Dim sampleObject = New SampleClass With   
    {.FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 <span data-ttu-id="3b20d-213">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-213">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-214">Operador New</span><span class="sxs-lookup"><span data-stu-id="3b20d-214">New Operator</span></span>](../../../visual-basic/language-reference/operators/new-operator.md)  
  
-   [<span data-ttu-id="3b20d-215">Inicializadores de objeto: tipos nomeados e anônimos</span><span class="sxs-lookup"><span data-stu-id="3b20d-215">Object Initializers: Named and Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
  
###  <span data-ttu-id="3b20d-216"><a name="Static"></a>Classes compartilhadas e membros</span><span class="sxs-lookup"><span data-stu-id="3b20d-216"><a name="Static"></a> Shared Classes and Members</span></span>  
 <span data-ttu-id="3b20d-217">Um membro compartilhado da classe é uma propriedade, procedimento ou campo que é compartilhado por todas as instâncias de uma classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-217">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="3b20d-218">Para definir um membro compartilhado:</span><span class="sxs-lookup"><span data-stu-id="3b20d-218">To define a shared member:</span></span>  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 <span data-ttu-id="3b20d-219">Para acessar o membro compartilhado, use o nome da classe sem criar um objeto dessa classe:</span><span class="sxs-lookup"><span data-stu-id="3b20d-219">To access the shared member, use the name of the class without creating an object of this class:</span></span>  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 <span data-ttu-id="3b20d-220">Módulos compartilhados no Visual Basic somente membros compartilhados e não podem ser instanciados.</span><span class="sxs-lookup"><span data-stu-id="3b20d-220">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="3b20d-221">Membros compartilhados também não é possível acessar métodos, campos ou propriedades não compartilhados</span><span class="sxs-lookup"><span data-stu-id="3b20d-221">Shared members also cannot access non-shared properties, fields or methods</span></span>  
  
 <span data-ttu-id="3b20d-222">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-222">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-223">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="3b20d-223">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [<span data-ttu-id="3b20d-224">Instrução Module</span><span class="sxs-lookup"><span data-stu-id="3b20d-224">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
###  <span data-ttu-id="3b20d-225"><a name="AnonymousTypes"></a>Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="3b20d-225"><a name="AnonymousTypes"></a> Anonymous Types</span></span>  
 <span data-ttu-id="3b20d-226">Tipos anônimos permitem que você crie objetos sem escrever uma definição de classe para o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="3b20d-226">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="3b20d-227">Em vez disso, o compilador gera uma classe para você.</span><span class="sxs-lookup"><span data-stu-id="3b20d-227">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="3b20d-228">A classe não tem nenhum nome utilizável e contém as propriedades que você especificar no declarar o objeto.</span><span class="sxs-lookup"><span data-stu-id="3b20d-228">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="3b20d-229">Para criar uma instância de um tipo anônimo:</span><span class="sxs-lookup"><span data-stu-id="3b20d-229">To create an instance of an anonymous type:</span></span>  
  
```vb  
' sampleObject is an instance of a simple anonymous type.  
Dim sampleObject =   
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}  
```  
  
 <span data-ttu-id="3b20d-230">Para obter mais informações, consulte: [tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="3b20d-230">For more information, see: [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
##  <span data-ttu-id="3b20d-231"><a name="Inheritance"></a>Herança</span><span class="sxs-lookup"><span data-stu-id="3b20d-231"><a name="Inheritance"></a> Inheritance</span></span>  
 <span data-ttu-id="3b20d-232">Herança permite que você crie uma nova classe que reutiliza, estende e modifica o comportamento que é definido em outra classe.</span><span class="sxs-lookup"><span data-stu-id="3b20d-232">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="3b20d-233">A classe cujos membros são herdados é chamada a *classe base*, e a classe que herda os membros é chamada de *classe derivada*.</span><span class="sxs-lookup"><span data-stu-id="3b20d-233">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="3b20d-234">No entanto, todas as classes no Visual Basic implicitamente herdam o <xref:System.Object>classe que oferece suporte a hierarquia de classe do .NET e fornece serviços de nível baixo para todas as classes.</xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="3b20d-234">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b20d-235">Visual Basic não dá suporte a várias heranças.</span><span class="sxs-lookup"><span data-stu-id="3b20d-235">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="3b20d-236">Ou seja, você pode especificar apenas uma classe base para uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3b20d-236">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="3b20d-237">Para herdar de uma classe base:</span><span class="sxs-lookup"><span data-stu-id="3b20d-237">To inherit from a base class:</span></span>  
  
```vb  
Class DerivedClass  
    Inherits BaseClass  
End Class  
```  
  
 <span data-ttu-id="3b20d-238">Por padrão, todas as classes podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="3b20d-238">By default all classes can be inherited.</span></span> <span data-ttu-id="3b20d-239">No entanto, você pode especificar se uma classe não deve ser usada como uma classe base ou cria uma classe que pode ser usada como apenas uma classe base.</span><span class="sxs-lookup"><span data-stu-id="3b20d-239">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="3b20d-240">Para especificar que uma classe não pode ser usada como uma classe base:</span><span class="sxs-lookup"><span data-stu-id="3b20d-240">To specify that a class cannot be used as a base class:</span></span>  
  
```vb  
NotInheritable Class SampleClass  
End Class  
```  
  
 <span data-ttu-id="3b20d-241">Para especificar que uma classe pode ser usada como uma classe base apenas e não pode ser instanciada:</span><span class="sxs-lookup"><span data-stu-id="3b20d-241">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```vb  
MustInherit Class BaseClass  
End Class  
```  
  
 <span data-ttu-id="3b20d-242">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-242">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-243">Instrução Inherits</span><span class="sxs-lookup"><span data-stu-id="3b20d-243">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
  
-   [<span data-ttu-id="3b20d-244">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="3b20d-244">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
  
-   [<span data-ttu-id="3b20d-245">MustInherit</span><span class="sxs-lookup"><span data-stu-id="3b20d-245">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
  
###  <span data-ttu-id="3b20d-246"><a name="Overriding"></a>Substituindo membros</span><span class="sxs-lookup"><span data-stu-id="3b20d-246"><a name="Overriding"></a> Overriding Members</span></span>  
 <span data-ttu-id="3b20d-247">Por padrão, uma classe derivada herda todos os membros de sua classe base.</span><span class="sxs-lookup"><span data-stu-id="3b20d-247">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="3b20d-248">Se você quiser alterar o comportamento do membro herdado, você precisa substituí-la.</span><span class="sxs-lookup"><span data-stu-id="3b20d-248">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="3b20d-249">Ou seja, você pode definir uma nova implementação de método, propriedade ou evento na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3b20d-249">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="3b20d-250">Seguintes modificadores são usados para controlar como as propriedades e métodos são substituídos:</span><span class="sxs-lookup"><span data-stu-id="3b20d-250">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="3b20d-251">Modificador de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b20d-251">Visual Basic Modifier</span></span>|<span data-ttu-id="3b20d-252">Definição</span><span class="sxs-lookup"><span data-stu-id="3b20d-252">Definition</span></span>|  
|---------------------------|----------------|  
|[<span data-ttu-id="3b20d-253">Substituível</span><span class="sxs-lookup"><span data-stu-id="3b20d-253">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)|<span data-ttu-id="3b20d-254">Permite que um membro da classe a ser substituído em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3b20d-254">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="3b20d-255">Substituições</span><span class="sxs-lookup"><span data-stu-id="3b20d-255">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)|<span data-ttu-id="3b20d-256">Substitui um membro (substituível) virtual definido na classe base.</span><span class="sxs-lookup"><span data-stu-id="3b20d-256">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="3b20d-257">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="3b20d-257">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)|<span data-ttu-id="3b20d-258">Impede que um membro que está sendo substituído em uma classe herdada.</span><span class="sxs-lookup"><span data-stu-id="3b20d-258">Prevents a member from being overridden in an inheriting class.</span></span>|  
|[<span data-ttu-id="3b20d-259">MustOverride</span><span class="sxs-lookup"><span data-stu-id="3b20d-259">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)|<span data-ttu-id="3b20d-260">Requer que um membro da classe a ser substituído na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="3b20d-260">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="3b20d-261">Sombras</span><span class="sxs-lookup"><span data-stu-id="3b20d-261">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)|<span data-ttu-id="3b20d-262">Oculta um membro herdado de uma classe base</span><span class="sxs-lookup"><span data-stu-id="3b20d-262">Hides a member inherited from a base class</span></span>|  
  
##  <span data-ttu-id="3b20d-263"><a name="Interfaces"></a>Interfaces</span><span class="sxs-lookup"><span data-stu-id="3b20d-263"><a name="Interfaces"></a> Interfaces</span></span>  
 <span data-ttu-id="3b20d-264">Interfaces, como classes, definem um conjunto de propriedades, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="3b20d-264">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="3b20d-265">Mas, diferentemente das classes, interfaces não fornecem implementação.</span><span class="sxs-lookup"><span data-stu-id="3b20d-265">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="3b20d-266">Eles são implementados por classes e definidos como entidades separadas de classes.</span><span class="sxs-lookup"><span data-stu-id="3b20d-266">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="3b20d-267">Uma interface representa um contrato que uma classe que implementa uma interface deve implementar todos os aspectos da interface exatamente como ela está definida.</span><span class="sxs-lookup"><span data-stu-id="3b20d-267">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="3b20d-268">Para definir uma interface:</span><span class="sxs-lookup"><span data-stu-id="3b20d-268">To define an interface:</span></span>  
  
```vb  
Public Interface ISampleInterface  
    Sub DoSomething()  
End Interface  
```  
  
 <span data-ttu-id="3b20d-269">Para implementar uma interface em uma classe:</span><span class="sxs-lookup"><span data-stu-id="3b20d-269">To implement an interface in a class:</span></span>  
  
```vb  
Class SampleClass  
    Implements ISampleInterface  
    Sub DoSomething  
        ' Method implementation.  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="3b20d-270">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-270">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-271">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3b20d-271">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
  
-   [<span data-ttu-id="3b20d-272">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="3b20d-272">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
-   [<span data-ttu-id="3b20d-273">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="3b20d-273">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
  
##  <span data-ttu-id="3b20d-274"><a name="Generics"></a>Classes genéricas</span><span class="sxs-lookup"><span data-stu-id="3b20d-274"><a name="Generics"></a> Generics</span></span>  
 <span data-ttu-id="3b20d-275">Classes, estruturas, interfaces e métodos do .NET Framework podem incluir *parâmetros de tipo* que definem os tipos de objetos que podem armazenar ou usar.</span><span class="sxs-lookup"><span data-stu-id="3b20d-275">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="3b20d-276">O exemplo mais comum de genéricos é uma coleção, onde você pode especificar o tipo de objeto a ser armazenado em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="3b20d-276">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="3b20d-277">Para definir uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="3b20d-277">To define a generic class:</span></span>  
  
```vb  
Class SampleGeneric(Of T)  
    Public Field As T  
End Class  
```  
  
 <span data-ttu-id="3b20d-278">Para criar uma instância de uma classe genérica:</span><span class="sxs-lookup"><span data-stu-id="3b20d-278">To create an instance of a generic class:</span></span>  
  
```vb  
Dim sampleObject As New SampleGeneric(Of String)  
sampleObject.Field = "Sample string"  
```  
  
 <span data-ttu-id="3b20d-279">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-279">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-280">Genéricos</span><span class="sxs-lookup"><span data-stu-id="3b20d-280">Generics</span></span>](https://msdn.microsoft.com/library/ms172192)  
  
-   [<span data-ttu-id="3b20d-281">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b20d-281">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
  
##  <span data-ttu-id="3b20d-282"><a name="Delegates"></a>Delegados</span><span class="sxs-lookup"><span data-stu-id="3b20d-282"><a name="Delegates"></a> Delegates</span></span>  
 <span data-ttu-id="3b20d-283">A *delegar* é um tipo que define uma assinatura de método e pode fornecer uma referência a qualquer método com uma assinatura compatível.</span><span class="sxs-lookup"><span data-stu-id="3b20d-283">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="3b20d-284">Você pode invocar (ou chamar) o método por meio do delegado.</span><span class="sxs-lookup"><span data-stu-id="3b20d-284">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="3b20d-285">Delegados são usados para passar métodos como argumentos a outros métodos.</span><span class="sxs-lookup"><span data-stu-id="3b20d-285">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b20d-286">Os manipuladores de eventos nada mais são do que métodos chamados por meio de delegados.</span><span class="sxs-lookup"><span data-stu-id="3b20d-286">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="3b20d-287">Para obter mais informações sobre como usar delegados na manipulação de eventos, consulte [eventos](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).</span><span class="sxs-lookup"><span data-stu-id="3b20d-287">For more information about using delegates in event handling, see [Events](http://msdn.microsoft.com/library/b6f65241-e0ad-4590-a99f-200ce741bb1f).</span></span>  
  
 <span data-ttu-id="3b20d-288">Para criar um delegado:</span><span class="sxs-lookup"><span data-stu-id="3b20d-288">To create a delegate:</span></span>  
  
```vb  
Delegate Sub SampleDelegate(ByVal str As String)  
```  
  
 <span data-ttu-id="3b20d-289">Para criar uma referência a um método que corresponde à assinatura especificada pelo delegado:</span><span class="sxs-lookup"><span data-stu-id="3b20d-289">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
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
  
 <span data-ttu-id="3b20d-290">Para obter mais informações, consulte:</span><span class="sxs-lookup"><span data-stu-id="3b20d-290">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3b20d-291">Delegados</span><span class="sxs-lookup"><span data-stu-id="3b20d-291">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
  
-   [<span data-ttu-id="3b20d-292">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="3b20d-292">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
-   [<span data-ttu-id="3b20d-293">Operador AddressOf</span><span class="sxs-lookup"><span data-stu-id="3b20d-293">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
  
## <a name="see-also"></a><span data-ttu-id="3b20d-294">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3b20d-294">See Also</span></span>  
 [<span data-ttu-id="3b20d-295">Guia de programação em Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3b20d-295">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
