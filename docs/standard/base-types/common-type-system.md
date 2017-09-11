---
title: Sistema de tipo comum detalhado
description: Sistema de tipo comum detalhado
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: b5482a1d-7bdc-40fe-aa45-10df930ceb5b
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 6be672acc84a76106e25b82574acad16beb4a8ac
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="common-type-system-in-depth"></a><span data-ttu-id="32c30-104">Sistema de tipo comum detalhado</span><span class="sxs-lookup"><span data-stu-id="32c30-104">Common type system in depth</span></span>

<span data-ttu-id="32c30-105">Este tópico contém as seções a seguir que exploram o Common Type System detalhadamente:</span><span class="sxs-lookup"><span data-stu-id="32c30-105">This topic contains the following sections that explore the common type system in depth:</span></span>

* [<span data-ttu-id="32c30-106">Tipos no .NET</span><span class="sxs-lookup"><span data-stu-id="32c30-106">Types in .NET</span></span>](#types-in-net)

* [<span data-ttu-id="32c30-107">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="32c30-107">Type definitions</span></span>](#type-definitions)

* [<span data-ttu-id="32c30-108">Membros de tipos</span><span class="sxs-lookup"><span data-stu-id="32c30-108">Type members</span></span>](#type-members)

* [<span data-ttu-id="32c30-109">Características de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="32c30-109">Characteristics of type members</span></span>](#characteristics-of-type-members)


## <a name="types-in-net"></a><span data-ttu-id="32c30-110">Tipos no .NET</span><span class="sxs-lookup"><span data-stu-id="32c30-110">Types in .NET</span></span>

<span data-ttu-id="32c30-111">Todos os tipos no .NET são tipos de valor ou tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="32c30-111">All types in .NET are either value types or reference types.</span></span> 

<span data-ttu-id="32c30-112">Tipos de valor são tipos de dados cujos objetos são representados pelo valor real do objeto.</span><span class="sxs-lookup"><span data-stu-id="32c30-112">Value types are data types whose objects are represented by the object's actual value.</span></span> <span data-ttu-id="32c30-113">Se uma instância de um tipo de valor é atribuída a uma variável, essa variável recebe uma nova cópia do valor.</span><span class="sxs-lookup"><span data-stu-id="32c30-113">If an instance of a value type is assigned to a variable, that variable is given a fresh copy of the value.</span></span>

<span data-ttu-id="32c30-114">Tipos de referência são tipos de dados cujos objetos são representados por uma referência (semelhante a um ponteiro) para o valor real do objeto.</span><span class="sxs-lookup"><span data-stu-id="32c30-114">Reference types are data types whose objects are represented by a reference (similar to a pointer) to the object's actual value.</span></span> <span data-ttu-id="32c30-115">Se um tipo de referência é atribuído a uma variável, essa variável referencia (aponta para) o valor original.</span><span class="sxs-lookup"><span data-stu-id="32c30-115">If a reference type is assigned to a variable, that variable references (points to) the original value.</span></span> <span data-ttu-id="32c30-116">Nenhuma cópia é feita.</span><span class="sxs-lookup"><span data-stu-id="32c30-116">No copy is made.</span></span> 

<span data-ttu-id="32c30-117">O Common Type System no .NET dá suporte às seguintes cinco categorias de tipos:</span><span class="sxs-lookup"><span data-stu-id="32c30-117">The common type system in .NET supports the following five categories of types:</span></span>

* [<span data-ttu-id="32c30-118">Classes</span><span class="sxs-lookup"><span data-stu-id="32c30-118">Classes</span></span>](#classes)

* [<span data-ttu-id="32c30-119">Estruturas</span><span class="sxs-lookup"><span data-stu-id="32c30-119">Structures</span></span>](#structures)

* [<span data-ttu-id="32c30-120">Enumerações</span><span class="sxs-lookup"><span data-stu-id="32c30-120">Enumerations</span></span>](#enumerations)

* [<span data-ttu-id="32c30-121">Interfaces</span><span class="sxs-lookup"><span data-stu-id="32c30-121">Interfaces</span></span>](#interfaces)

* [<span data-ttu-id="32c30-122">Delegados</span><span class="sxs-lookup"><span data-stu-id="32c30-122">Delegates</span></span>](#delegates)

### <a name="classes"></a><span data-ttu-id="32c30-123">Classes</span><span class="sxs-lookup"><span data-stu-id="32c30-123">Classes</span></span>

<span data-ttu-id="32c30-124">Uma classe é um tipo de referência que pode ser derivado diretamente de outra classe e que é derivada implicitamente de [System.Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="32c30-124">A class is a reference type that can be derived directly from another class and that is derived implicitly from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="32c30-125">A classe define as operações que um objeto (que é uma instância da classe) pode executar (métodos, eventos ou propriedades) e os dados que o objeto contém (campos).</span><span class="sxs-lookup"><span data-stu-id="32c30-125">The class defines the operations that an object (which is an instance of the class) can perform (methods, events, or properties) and the data that the object contains (fields).</span></span> <span data-ttu-id="32c30-126">Embora uma classe geralmente inclua a definição e a implementação (diferente de interfaces, por exemplo, que contêm somente a definição sem implementação), ela pode ter um ou mais membros que não têm implementação.</span><span class="sxs-lookup"><span data-stu-id="32c30-126">Although a class generally includes both definition and implementation (unlike interfaces, for example, which contain only definition without implementation), it can have one or more members that have no implementation.</span></span>

<span data-ttu-id="32c30-127">A tabela a seguir descreve algumas das características que uma classe pode ter.</span><span class="sxs-lookup"><span data-stu-id="32c30-127">The following table describes some of the characteristics that a class may have.</span></span> <span data-ttu-id="32c30-128">Cada linguagem que dá suporte ao tempo de execução fornece uma maneira para indicar que uma classe ou um membro da classe tem uma ou mais dessas características.</span><span class="sxs-lookup"><span data-stu-id="32c30-128">Each language that supports the runtime provides a way to indicate that a class or class member has one or more of these characteristics.</span></span> <span data-ttu-id="32c30-129">No entanto, as linguagens de programação individuais que segmentam o .NET não podem disponibilizar todas essas características.</span><span class="sxs-lookup"><span data-stu-id="32c30-129">However, individual programming languages that target .NET may not make all these characteristics available.</span></span>

<span data-ttu-id="32c30-130">Característica</span><span class="sxs-lookup"><span data-stu-id="32c30-130">Characteristic</span></span> | <span data-ttu-id="32c30-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="32c30-131">Description</span></span>
-------------- | -----------
<span data-ttu-id="32c30-132">sealed</span><span class="sxs-lookup"><span data-stu-id="32c30-132">sealed</span></span> | <span data-ttu-id="32c30-133">Especifica que outra classe não pode ser derivada desse tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-133">Specifies that another class cannot be derived from this type.</span></span>
<span data-ttu-id="32c30-134">implementa</span><span class="sxs-lookup"><span data-stu-id="32c30-134">implements</span></span> | <span data-ttu-id="32c30-135">Indica que a classe usa uma ou mais interfaces, fornecendo implementações de membros da interface.</span><span class="sxs-lookup"><span data-stu-id="32c30-135">Indicates that the class uses one or more interfaces by providing implementations of interface members.</span></span>
<span data-ttu-id="32c30-136">abstract</span><span class="sxs-lookup"><span data-stu-id="32c30-136">abstract</span></span> | <span data-ttu-id="32c30-137">Indica que a classe não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="32c30-137">Indicates that the class cannot be instantiated.</span></span> <span data-ttu-id="32c30-138">Para usá-la, você deve derivar outra classe a partir dela.</span><span class="sxs-lookup"><span data-stu-id="32c30-138">To use it, you must derive another class from it.</span></span>
<span data-ttu-id="32c30-139">herda</span><span class="sxs-lookup"><span data-stu-id="32c30-139">inherits</span></span> | <span data-ttu-id="32c30-140">Indica que as instâncias da classe podem ser usadas em qualquer lugar em que a classe base for especificada.</span><span class="sxs-lookup"><span data-stu-id="32c30-140">Indicates that instances of the class can be used anywhere the base class is specified.</span></span> <span data-ttu-id="32c30-141">Uma classe derivada que herda de uma classe base pode usar a implementação de todos os membros públicos fornecidos pela classe base ou a classe derivada pode substituir a implementação dos membros públicos com sua própria implementação.</span><span class="sxs-lookup"><span data-stu-id="32c30-141">A derived class that inherits from a base class can use the implementation of any public members provided by the base class, or the derived class can override the implementation of the public members with its own implementation.</span></span>
<span data-ttu-id="32c30-142">exportado ou não exportado</span><span class="sxs-lookup"><span data-stu-id="32c30-142">exported or not exported</span></span> | <span data-ttu-id="32c30-143">Indica se uma classe está visível fora do assembly em que ela está definida.</span><span class="sxs-lookup"><span data-stu-id="32c30-143">Indicates whether a class is visible outside the assembly in which it is defined.</span></span> <span data-ttu-id="32c30-144">Essa característica só se aplica a classes de nível superior e não a classes aninhadas.</span><span class="sxs-lookup"><span data-stu-id="32c30-144">This characteristic applies only to top-level classes and not to nested classes.</span></span>

> [!NOTE]
> <span data-ttu-id="32c30-145">Uma classe também pode ser aninhada em uma classe ou estrutura pai.</span><span class="sxs-lookup"><span data-stu-id="32c30-145">A class can also be nested in a parent class or structure.</span></span> <span data-ttu-id="32c30-146">Classes aninhadas também têm características de membro.</span><span class="sxs-lookup"><span data-stu-id="32c30-146">Nested classes also have member characteristics.</span></span> <span data-ttu-id="32c30-147">Para obter mais informações, consulte [Tipos aninhados](#nested-types).</span><span class="sxs-lookup"><span data-stu-id="32c30-147">For more information, see [Nested types](#nested-types).</span></span>

<span data-ttu-id="32c30-148">Membros da classe que não tenham implementação são membros abstratos.</span><span class="sxs-lookup"><span data-stu-id="32c30-148">Class members that have no implementation are abstract members.</span></span> <span data-ttu-id="32c30-149">Uma classe que tenha um ou mais membros abstratos é ela própria abstrata. Não é possível criar novas instâncias dessa classe.</span><span class="sxs-lookup"><span data-stu-id="32c30-149">A class that has one or more abstract members is itself abstract; new instances of it cannot be created.</span></span> <span data-ttu-id="32c30-150">Algumas linguagens que segmentam o tempo de execução permitem marcar uma classe como abstrata mesmo que nenhum de seus membros seja abstrato.</span><span class="sxs-lookup"><span data-stu-id="32c30-150">Some languages that target the runtime let you mark a class as abstract even if none of its members are abstract.</span></span> <span data-ttu-id="32c30-151">É possível usar uma classe abstrata quando você deseja encapsular um conjunto básico de funcionalidades que as classes derivadas podem herdar ou substituir quando apropriado.</span><span class="sxs-lookup"><span data-stu-id="32c30-151">You can use an abstract class when you want to encapsulate a basic set of functionality that derived classes can inherit or override when appropriate.</span></span> <span data-ttu-id="32c30-152">Classes que não são abstratas são chamadas de classes concretas.</span><span class="sxs-lookup"><span data-stu-id="32c30-152">Classes that are not abstract are referred to as concrete classes.</span></span>

<span data-ttu-id="32c30-153">Uma classe pode implementar qualquer número de interfaces, mas pode herdar apenas uma classe base além de [System.Object](xref:System.Object), de que todas as classes herdam implicitamente.</span><span class="sxs-lookup"><span data-stu-id="32c30-153">A class can implement any number of interfaces, but it can inherit from only one base class in addition to [System.Object](xref:System.Object), from which all classes inherit implicitly.</span></span> <span data-ttu-id="32c30-154">Todas as classes devem ter pelo menos um construtor, que inicializa novas instâncias da classe.</span><span class="sxs-lookup"><span data-stu-id="32c30-154">All classes must have at least one constructor, which initializes new instances of the class.</span></span> <span data-ttu-id="32c30-155">Se você não definir explicitamente um construtor, a maioria dos compiladores fornecerá automaticamente um construtor padrão (sem parâmetros).</span><span class="sxs-lookup"><span data-stu-id="32c30-155">If you do not explicitly define a constructor, most compilers will automatically provide a default (parameterless) constructor.</span></span>

### <a name="structures"></a><span data-ttu-id="32c30-156">Estruturas</span><span class="sxs-lookup"><span data-stu-id="32c30-156">Structures</span></span>

<span data-ttu-id="32c30-157">Uma estrutura é um tipo de valor que é derivado implicitamente de [System.ValueType](xref:System.ValueType) que, por sua vez, é derivado de [System.Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="32c30-157">A structure is a value type that derives implicitly from [System.ValueType](xref:System.ValueType), which in turn is derived from [System.Object](xref:System.Object).</span></span> <span data-ttu-id="32c30-158">Uma estrutura é muito útil para representar valores cujos requisitos de memória são pequenos e passar valores como parâmetros por valor para os métodos que tenham parâmetros fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="32c30-158">A structure is very useful for representing values whose memory requirements are small, and for passing values as by-value parameters to methods that have strongly typed parameters.</span></span> <span data-ttu-id="32c30-159">No .NET, todos os tipos de dados primitivos ([Booliano](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) e [UInt64](xref:System.UInt64)) são definidos como estruturas.</span><span class="sxs-lookup"><span data-stu-id="32c30-159">In .NET, all primitive data types ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64)) are defined as structures.</span></span>

<span data-ttu-id="32c30-160">Assim como as classes, as estruturas definem os dados (os campos da estrutura) e as operações que podem ser executadas nesses dados (os métodos da estrutura).</span><span class="sxs-lookup"><span data-stu-id="32c30-160">Like classes, structures define both data (the fields of the structure) and the operations that can be performed on that data (the methods of the structure).</span></span> <span data-ttu-id="32c30-161">Isso significa que você pode chamar métodos em estruturas, incluindo os métodos virtuais definidos nas classes [System.Object](xref:System.Object) e [System.ValueType](xref:System.ValueType) e todos os métodos definidos no próprio tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="32c30-161">This means that you can call methods on structures, including the virtual methods defined on the [System.Object](xref:System.Object) and [System.ValueType](xref:System.ValueType) classes, and any methods defined on the value type itself.</span></span> <span data-ttu-id="32c30-162">Em outras palavras, as estruturas podem ter campos, propriedades e eventos, bem como métodos estáticos e não estáticos.</span><span class="sxs-lookup"><span data-stu-id="32c30-162">In other words, structures can have fields, properties, and events, as well as static and nonstatic methods.</span></span> <span data-ttu-id="32c30-163">É possível criar instâncias de estruturas, passá-las como parâmetros, armazená-las como variáveis locais ou armazená-las em um campo de outro tipo de valor ou tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="32c30-163">You can create instances of structures, pass them as parameters, store them as local variables, or store them in a field of another value type or reference type.</span></span> <span data-ttu-id="32c30-164">As estruturas também podem implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="32c30-164">Structures can also implement interfaces.</span></span>

<span data-ttu-id="32c30-165">Tipos de valor também são diferentes das classes em vários pontos.</span><span class="sxs-lookup"><span data-stu-id="32c30-165">Value types also differ from classes in several respects.</span></span> <span data-ttu-id="32c30-166">Primeiro, embora herdem implicitamente de [System.ValueType](xref:System.ValueType), eles não podem herdar diretamente de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-166">First, although they implicitly inherit from [System.ValueType](xref:System.ValueType), they cannot directly inherit from any type.</span></span> <span data-ttu-id="32c30-167">Da mesma forma, todos os tipos de valor são lacrados, o que significa que nenhum outro tipo pode ser derivado deles.</span><span class="sxs-lookup"><span data-stu-id="32c30-167">Similarly, all value types are sealed, which means that no other type can be derived from them.</span></span> <span data-ttu-id="32c30-168">Eles também não exigem construtores.</span><span class="sxs-lookup"><span data-stu-id="32c30-168">They also do not require constructors.</span></span>

<span data-ttu-id="32c30-169">Para cada tipo de valor, o Common Language Runtime fornece um tipo disponível demarcado correspondente, que é uma classe com o mesmo estado e comportamento que o tipo de valor.</span><span class="sxs-lookup"><span data-stu-id="32c30-169">For each value type, the common language runtime supplies a corresponding boxed type, which is a class that has the same state and behavior as the value type.</span></span> <span data-ttu-id="32c30-170">Uma instância de um tipo de valor é demarcada quando é passada para um método que aceita um parâmetro de tipo [System.Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="32c30-170">An instance of a value type is boxed when it is passed to a method that accepts a parameter of type [System.Object](xref:System.Object).</span></span> <span data-ttu-id="32c30-171">Ele é não demarcado (ou seja, convertido de uma instância de uma classe de volta para uma instância de um tipo de valor) quando o controle retorna de uma chamada de método que aceita um tipo de valor como um parâmetro por referência.</span><span class="sxs-lookup"><span data-stu-id="32c30-171">It is unboxed (that is, converted from an instance of a class back to an instance of a value type) when control returns from a method call that accepts a value type as a by-reference parameter.</span></span> <span data-ttu-id="32c30-172">Algumas linguagens exigem que você use sintaxe especial quando o tipo demarcado é necessário. Outras usam automaticamente o tipo demarcado quando necessário.</span><span class="sxs-lookup"><span data-stu-id="32c30-172">Some languages require that you use special syntax when the boxed type is required; others automatically use the boxed type when it is needed.</span></span> <span data-ttu-id="32c30-173">Ao definir um tipo de valor, você está definindo o tipo demarcado e não demarcado.</span><span class="sxs-lookup"><span data-stu-id="32c30-173">When you define a value type, you are defining both the boxed and the unboxed type.</span></span>

### <a name="enumerations"></a><span data-ttu-id="32c30-174">Enumerações</span><span class="sxs-lookup"><span data-stu-id="32c30-174">Enumerations</span></span>

<span data-ttu-id="32c30-175">Uma enumeração (enum) é um tipo de valor que é herdado diretamente de [System.Enum](xref:System.Enum) e que fornece nomes alternativos para valores de um tipo primitivo subjacente.</span><span class="sxs-lookup"><span data-stu-id="32c30-175">An enumeration (enum) is a value type that inherits directly from [System.Enum](xref:System.Enum) and that supplies alternate names for the values of an underlying primitive type.</span></span> <span data-ttu-id="32c30-176">Um tipo de enumeração tem um nome, um tipo subjacente que deve ser um dos tipos inteiros com ou sem sinal internos (como [Byte](xref:System.Byte), [Int32](xref:System.Int32) ou [UInt64](xref:System.UInt64)) e um conjunto de campos.</span><span class="sxs-lookup"><span data-stu-id="32c30-176">An enumeration type has a name, an underlying type that must be one of the built-in signed or unsigned integer types (such as [Byte](xref:System.Byte), [Int32](xref:System.Int32), or [UInt64](xref:System.UInt64)), and a set of fields.</span></span> <span data-ttu-id="32c30-177">Os campos são campos literais estáticos, cada um deles representa uma constante.</span><span class="sxs-lookup"><span data-stu-id="32c30-177">The fields are static literal fields, each of which represents a constant.</span></span> <span data-ttu-id="32c30-178">O mesmo valor pode ser atribuído a vários campos.</span><span class="sxs-lookup"><span data-stu-id="32c30-178">The same value can be assigned to multiple fields.</span></span> <span data-ttu-id="32c30-179">Quando isso ocorre, você deve marcar um dos valores como o valor de enumeração primário para reflexão e conversão da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="32c30-179">When this occurs, you must mark one of the values as the primary enumeration value for reflection and string conversion.</span></span>

<span data-ttu-id="32c30-180">Você pode atribuir um valor de tipo subjacente a uma enumeração e vice-versa (nenhuma conversão é exigida pelo tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="32c30-180">You can assign a value of the underlying type to an enumeration and vice versa (no cast is required by the runtime).</span></span> <span data-ttu-id="32c30-181">É possível criar uma instância de uma enumeração e chamar os métodos de [System.Enum](xref:System.Enum), assim como qualquer método definido no tipo subjacente da enumeração.</span><span class="sxs-lookup"><span data-stu-id="32c30-181">You can create an instance of an enumeration and call the methods of [System.Enum](xref:System.Enum), as well as any methods defined on the enumeration's underlying type.</span></span> <span data-ttu-id="32c30-182">No entanto, algumas linguagens talvez não deixem passar uma enumeração como um parâmetro quando uma instância do tipo subjacente é necessária (ou vice-versa).</span><span class="sxs-lookup"><span data-stu-id="32c30-182">However, some languages might not let you pass an enumeration as a parameter when an instance of the underlying type is required (or vice versa).</span></span>

<span data-ttu-id="32c30-183">As seguintes restrições adicionais se aplicam a enumerações:</span><span class="sxs-lookup"><span data-stu-id="32c30-183">The following additional restrictions apply to enumerations:</span></span> 

* <span data-ttu-id="32c30-184">Elas não podem definir seus próprios métodos.</span><span class="sxs-lookup"><span data-stu-id="32c30-184">They cannot define their own methods.</span></span>

* <span data-ttu-id="32c30-185">Elas não podem implementar interfaces.</span><span class="sxs-lookup"><span data-stu-id="32c30-185">They cannot implement interfaces.</span></span>

* <span data-ttu-id="32c30-186">Elas não podem definir propriedades ou eventos.</span><span class="sxs-lookup"><span data-stu-id="32c30-186">They cannot define properties or events.</span></span>

* <span data-ttu-id="32c30-187">Elas não podem ser genéricas, a menos que sejam genéricas apenas por estarem aninhadas dentro de um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="32c30-187">They cannot be generic, unless they are generic only because they are nested within a generic type.</span></span> <span data-ttu-id="32c30-188">Ou seja, uma enumeração não pode ter parâmetros de tipo próprios.</span><span class="sxs-lookup"><span data-stu-id="32c30-188">That is, an enumeration cannot have type parameters of its own.</span></span> 

> [!NOTE]
> <span data-ttu-id="32c30-189">Tipos aninhados (incluindo enumerações) criados com o C# incluem os parâmetros de tipo de todos os tipos genéricos e, portanto, serão genéricos mesmo se não tiverem parâmetros de tipo próprios.</span><span class="sxs-lookup"><span data-stu-id="32c30-189">Nested types (including enumerations) created with C# include the type parameters of all enclosing generic types, and are therefore generic even if they do not have type parameters of their own.</span></span> <span data-ttu-id="32c30-190">Para obter mais informações, consulte o tópico de referência [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])).</span><span class="sxs-lookup"><span data-stu-id="32c30-190">For more information, see the [Type.MakeGenericType](xref:System.Type.MakeGenericType(System.Type[])) reference topic.</span></span> 

<span data-ttu-id="32c30-191">O atributo [FlagsAttribute](xref:System.FlagsAttribute) denota um tipo especial de enumeração chamado campo de bits.</span><span class="sxs-lookup"><span data-stu-id="32c30-191">The [FlagsAttribute](xref:System.FlagsAttribute) attribute denotes a special kind of enumeration called a bit field.</span></span> <span data-ttu-id="32c30-192">O próprio tempo de execução não faz distinção entre enumerações tradicionais e campos de bits, mas a linguagem pode fazer isso.</span><span class="sxs-lookup"><span data-stu-id="32c30-192">The runtime itself does not distinguish between traditional enumerations and bit fields, but your language might do so.</span></span> <span data-ttu-id="32c30-193">Quando é feita essa distinção, operadores bit a bit podem ser usados em campos de bits, mas não em enumerações, para gerar valores sem nome.</span><span class="sxs-lookup"><span data-stu-id="32c30-193">When this distinction is made, bitwise operators can be used on bit fields, but not on enumerations, to generate unnamed values.</span></span> <span data-ttu-id="32c30-194">Enumerações geralmente são usadas para listas de elementos exclusivos, como dias da semana, país ou nomes de região etc.</span><span class="sxs-lookup"><span data-stu-id="32c30-194">Enumerations are generally used for lists of unique elements, such as days of the week, country or region names, and so on.</span></span> <span data-ttu-id="32c30-195">Os campos de bits são geralmente usados para listas de qualidades ou quantidades que possam ocorrer em combinação, como `Red And Big And Fast`.</span><span class="sxs-lookup"><span data-stu-id="32c30-195">Bit fields are generally used for lists of qualities or quantities that might occur in combination, such as `Red And Big And Fast`.</span></span>

<span data-ttu-id="32c30-196">O exemplo a seguir mostra como usar campos de bit e enumerações tradicionais.</span><span class="sxs-lookup"><span data-stu-id="32c30-196">The following example shows how to use both bit fields and traditional enumerations.</span></span>

```csharp
using System;
using System.Collections.Generic;

// A traditional enumeration of some root vegetables.
public enum SomeRootVegetables
{
    HorseRadish,
    Radish,
    Turnip
}

// A bit field or flag enumeration of harvesting seasons.
[Flags]
public enum Seasons
{
    None = 0,
    Summer = 1,
    Autumn = 2,
    Winter = 4,
    Spring = 8,
    All = Summer | Autumn | Winter | Spring
}

public class Example
{
   public static void Main()
   {
       // Hash table of when vegetables are available.
       Dictionary<SomeRootVegetables, Seasons> AvailableIn = new Dictionary<SomeRootVegetables, Seasons>();

       AvailableIn[SomeRootVegetables.HorseRadish] = Seasons.All;
       AvailableIn[SomeRootVegetables.Radish] = Seasons.Spring;
       AvailableIn[SomeRootVegetables.Turnip] = Seasons.Spring | 
            Seasons.Autumn;

       // Array of the seasons, using the enumeration.
       Seasons[] theSeasons = new Seasons[] { Seasons.Summer, Seasons.Autumn, 
            Seasons.Winter, Seasons.Spring };

       // Print information of what vegetables are available each season.
       foreach (Seasons season in theSeasons)
       {
          Console.Write(String.Format(
              "The following root vegetables are harvested in {0}:\n", 
              season.ToString("G")));
          foreach (KeyValuePair<SomeRootVegetables, Seasons> item in AvailableIn)
          {
             // A bitwise comparison.
             if (((Seasons)item.Value & season) > 0)
                 Console.Write(String.Format("  {0:G}\n", 
                      (SomeRootVegetables)item.Key));
          }
       }
   }
}
// The example displays the following output:
//    The following root vegetables are harvested in Summer:
//      HorseRadish
//    The following root vegetables are harvested in Autumn:
//      Turnip
//      HorseRadish
//    The following root vegetables are harvested in Winter:
//      HorseRadish
//    The following root vegetables are harvested in Spring:
//      Turnip
//      Radish
//      HorseRadish
```

```vb
Imports System.Collections.Generic

' A traditional enumeration of some root vegetables.
Public Enum SomeRootVegetables
   HorseRadish
   Radish
   Turnip
End Enum 

' A bit field or flag enumeration of harvesting seasons.
<Flags()> Public Enum Seasons
   None = 0
   Summer = 1
   Autumn = 2
   Winter = 4
   Spring = 8
   All = Summer Or Autumn Or Winter Or Spring
End Enum 

' Entry point.
Public Class Example
   Public Shared Sub Main()
      ' Hash table of when vegetables are available.
      Dim AvailableIn As New Dictionary(Of SomeRootVegetables, Seasons)()

      AvailableIn(SomeRootVegetables.HorseRadish) = Seasons.All
      AvailableIn(SomeRootVegetables.Radish) = Seasons.Spring
      AvailableIn(SomeRootVegetables.Turnip) = Seasons.Spring Or _
                                               Seasons.Autumn

      ' Array of the seasons, using the enumeration.
      Dim theSeasons() As Seasons = {Seasons.Summer, Seasons.Autumn, _
                                     Seasons.Winter, Seasons.Spring}

      ' Print information of what vegetables are available each season.
      For Each season As Seasons In theSeasons
         Console.WriteLine(String.Format( _
              "The following root vegetables are harvested in {0}:", _
              season.ToString("G")))
         For Each item As KeyValuePair(Of SomeRootVegetables, Seasons) In AvailableIn
            ' A bitwise comparison.
            If(CType(item.Value, Seasons) And season) > 0 Then
               Console.WriteLine("  " + _
                     CType(item.Key, SomeRootVegetables).ToString("G"))
            End If
         Next
      Next
   End Sub 
End Class 
' The example displays the following output:
'    The following root vegetables are harvested in Summer:
'      HorseRadish
'    The following root vegetables are harvested in Autumn:
'      Turnip
'      HorseRadish
'    The following root vegetables are harvested in Winter:
'      HorseRadish
'    The following root vegetables are harvested in Spring:
'      Turnip
'      Radish
'      HorseRadish
```

### <a name="interfaces"></a><span data-ttu-id="32c30-197">Interfaces</span><span class="sxs-lookup"><span data-stu-id="32c30-197">Interfaces</span></span>

<span data-ttu-id="32c30-198">Uma interface define um contrato que especifica um relacionamento "possível" ou um relacionamento de "propriedade".</span><span class="sxs-lookup"><span data-stu-id="32c30-198">An interface defines a contract that specifies a "can do" relationship or a "has a" relationship.</span></span> <span data-ttu-id="32c30-199">Interfaces são geralmente usadas para implementar a funcionalidade, como comparação e classificação (interfaces [IComparable](xref:System.IComparable) e [IComparable&lt;T&gt;](xref:System.IComparable%601)), testes de igualdade (a interface [IEquatable&lt;T&gt;](xref:System.IEquatable%601)), ou a enumeração de itens em uma coleção (as interfaces [IEnumerable](xref:System.Collections.IEnumerable) e [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601)).</span><span class="sxs-lookup"><span data-stu-id="32c30-199">Interfaces are often used to implement functionality, such as comparing and sorting (the [IComparable](xref:System.IComparable) and [IComparable&lt;T&gt;](xref:System.IComparable%601) interfaces), testing for equality (the [IEquatable&lt;T&gt;](xref:System.IEquatable%601) interface), or enumerating items in a collection (the [IEnumerable](xref:System.Collections.IEnumerable) and [IEnumerable&lt;T&gt;](xref:System.Collections.Generic.IEnumerable%601) interfaces).</span></span> <span data-ttu-id="32c30-200">Interfaces podem ter propriedades, métodos, eventos e todos os que são membros abstratos; ou seja, embora a interface defina os membros e suas assinaturas, ela deixa para o tipo que implementa a interface para definir a funcionalidade de cada membro da interface.</span><span class="sxs-lookup"><span data-stu-id="32c30-200">Interfaces can have properties, methods, and events, all of which are abstract members; that is, although the interface defines the members and their signatures, it leaves it to the type that implements the interface to define the functionality of each interface member.</span></span> <span data-ttu-id="32c30-201">Isso significa que qualquer classe ou estrutura que implementa uma interface deve fornecer definições para os membros abstratos declarados na interface.</span><span class="sxs-lookup"><span data-stu-id="32c30-201">This means that any class or structure that implements an interface must supply definitions for the abstract members declared in the interface.</span></span> <span data-ttu-id="32c30-202">Uma interface pode exigir qualquer classe de implementação ou estrutura para também implementar uma ou mais outras interfaces.</span><span class="sxs-lookup"><span data-stu-id="32c30-202">An interface can require any implementing class or structure to also implement one or more other interfaces.</span></span>

<span data-ttu-id="32c30-203">As restrições a seguir se aplicam a interfaces:</span><span class="sxs-lookup"><span data-stu-id="32c30-203">The following restrictions apply to interfaces:</span></span> 

* <span data-ttu-id="32c30-204">Uma interface pode ser declarada com qualquer acessibilidade, mas membros da interface devem ter acessibilidade pública.</span><span class="sxs-lookup"><span data-stu-id="32c30-204">An interface can be declared with any accessibility, but interface members must all have public accessibility.</span></span>

* <span data-ttu-id="32c30-205">Interfaces não podem definir construtores.</span><span class="sxs-lookup"><span data-stu-id="32c30-205">Interfaces cannot define constructors.</span></span>

* <span data-ttu-id="32c30-206">Interfaces não podem definir campos.</span><span class="sxs-lookup"><span data-stu-id="32c30-206">Interfaces cannot define fields.</span></span>

* <span data-ttu-id="32c30-207">Interfaces podem definir apenas membros de instância.</span><span class="sxs-lookup"><span data-stu-id="32c30-207">Interfaces can define only instance members.</span></span> <span data-ttu-id="32c30-208">Elas não podem definir membros estáticos.</span><span class="sxs-lookup"><span data-stu-id="32c30-208">They cannot define static members.</span></span>

<span data-ttu-id="32c30-209">Cada linguagem deve fornecer regras para mapear uma implementação para a interface que exija o membro, porque mais de uma interface pode declarar um membro com a mesma assinatura e esses membros podem ter implementações separadas.</span><span class="sxs-lookup"><span data-stu-id="32c30-209">Each language must provide rules for mapping an implementation to the interface that requires the member, because more than one interface can declare a member with the same signature, and these members can have separate implementations.</span></span>

### <a name="delegates"></a><span data-ttu-id="32c30-210">Delegados</span><span class="sxs-lookup"><span data-stu-id="32c30-210">Delegates</span></span>

<span data-ttu-id="32c30-211">Os delegados são tipos de referência que têm um propósito semelhante aos de ponteiros de função no C++.</span><span class="sxs-lookup"><span data-stu-id="32c30-211">Delegates are reference types that serve a purpose similar to that of function pointers in C++.</span></span> <span data-ttu-id="32c30-212">Eles são usados para manipuladores de eventos e funções de retorno de chamada no .NET.</span><span class="sxs-lookup"><span data-stu-id="32c30-212">They are used for event handlers and callback functions in .NET.</span></span> <span data-ttu-id="32c30-213">Diferentemente de ponteiros de função, delegados são seguros, verificáveis e fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="32c30-213">Unlike function pointers, delegates are secure, verifiable, and type safe.</span></span> <span data-ttu-id="32c30-214">Um tipo de delegado pode representar qualquer método de instância ou método estático que tenha uma assinatura compatível.</span><span class="sxs-lookup"><span data-stu-id="32c30-214">A delegate type can represent any instance method or static method that has a compatible signature.</span></span> 

<span data-ttu-id="32c30-215">Um parâmetro de um delegado será compatível com o parâmetro correspondente de um método se o tipo do parâmetro de delegado for mais restritivo do que o tipo do parâmetro de método, porque isso garante que um argumento passado para o delegado possa ser passado com segurança para o método.</span><span class="sxs-lookup"><span data-stu-id="32c30-215">A parameter of a delegate is compatible with the corresponding parameter of a method if the type of the delegate parameter is more restrictive than the type of the method parameter, because this guarantees that an argument passed to the delegate can be passed safely to the method.</span></span>

<span data-ttu-id="32c30-216">Da mesma forma, o tipo de retorno de um delegado será compatível com o tipo de retorno de um método se o tipo de retorno do método for mais restritivo do que o tipo de retorno do delegado, porque isso garante que o valor retornado do método possa ser convertido com segurança para o tipo retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="32c30-216">Similarly, the return type of a delegate is compatible with the return type of a method if the return type of the method is more restrictive than the return type of the delegate, because this guarantees that the return value of the method can be cast safely to the return type of the delegate.</span></span>

<span data-ttu-id="32c30-217">Por exemplo, um delegado que tenha um parâmetro de tipo [IEnumerable](xref:System.Collections.IEnumerable) e um tipo de retorno de [Object](xref:System.Object) pode representar um método que tenha um parâmetro de tipo [Object](xref:System.Object) e um valor retornado de tipo [IEnumerable](xref:System.Collections.IEnumerable).</span><span class="sxs-lookup"><span data-stu-id="32c30-217">For example, a delegate that has a parameter of type [IEnumerable](xref:System.Collections.IEnumerable) and a return type of [Object](xref:System.Object) can represent a method that has a parameter of type [Object](xref:System.Object) and a return value of type [IEnumerable](xref:System.Collections.IEnumerable).</span></span> 

 <span data-ttu-id="32c30-218">Diz-se que um delegado está associado ao método que representa.</span><span class="sxs-lookup"><span data-stu-id="32c30-218">A delegate is said to be bound to the method it represents.</span></span> <span data-ttu-id="32c30-219">Além de estar associado ao método, um delegado pode ser associado a um objeto.</span><span class="sxs-lookup"><span data-stu-id="32c30-219">In addition to being bound to the method, a delegate can be bound to an object.</span></span> <span data-ttu-id="32c30-220">O objeto representa o primeiro parâmetro do método e é passado para o método sempre que o delegado é invocado.</span><span class="sxs-lookup"><span data-stu-id="32c30-220">The object represents the first parameter of the method, and is passed to the method every time the delegate is invoked.</span></span> <span data-ttu-id="32c30-221">Se o método for um método de instância, o objeto associado será passado como parâmetro `this` implícito (`Me` no Visual Basic). Se o método for estático, o objeto será passado como o primeiro parâmetro formal do método e a assinatura do delegado deverá corresponder aos parâmetros restantes.</span><span class="sxs-lookup"><span data-stu-id="32c30-221">If the method is an instance method, the bound object is passed as the implicit `this` parameter (`Me` in Visual Basic); if the method is static, the object is passed as the first formal parameter of the method, and the delegate signature must match the remaining parameters.</span></span> 
 
 <span data-ttu-id="32c30-222">Todos os delegados herdam de [System.MulticastDelegate](xref:System.MulticastDelegate), que herda de [System.Delegate](xref:System.Delegate).</span><span class="sxs-lookup"><span data-stu-id="32c30-222">All delegates inherit from [System.MulticastDelegate](xref:System.MulticastDelegate), which inherits from [System.Delegate](xref:System.Delegate).</span></span> <span data-ttu-id="32c30-223">As linguagens C# e Visual Basic não permitem a herança desses tipos.</span><span class="sxs-lookup"><span data-stu-id="32c30-223">The C# and Visual Basic languages don't allow inheritance from these types.</span></span> <span data-ttu-id="32c30-224">Em vez disso, elas fornecem palavras-chave para declarar delegados.</span><span class="sxs-lookup"><span data-stu-id="32c30-224">Instead, they provide keywords for declaring delegates.</span></span>
 
 <span data-ttu-id="32c30-225">Como delegados herdam de [MulticastDelegate](xref:System.MulticastDelegate), um delegado tem uma lista dos métodos que o delegado representa e que são executados quando o delegado é invocado.</span><span class="sxs-lookup"><span data-stu-id="32c30-225">Because delegates inherit from [MulticastDelegate](xref:System.MulticastDelegate), a delegate has an invocation list, which is a list of methods that the delegate represents and that are executed when the delegate is invoked.</span></span> <span data-ttu-id="32c30-226">Todos os métodos na lista recebem os argumentos fornecidos quando o delegado é invocado.</span><span class="sxs-lookup"><span data-stu-id="32c30-226">All methods in the list receive the arguments supplied when the delegate is invoked.</span></span>

> [!NOTE]
> <span data-ttu-id="32c30-227">O valor retornado não é definido para um delegado que tenha mais de um método na lista de invocação, mesmo que o delegado tenha um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="32c30-227">The return value is not defined for a delegate that has more than one method in its invocation list, even if the delegate has a return type.</span></span>

<span data-ttu-id="32c30-228">Em muitos casos, como acontece com métodos de retorno de chamada, um delegado representa apenas um método e as únicas ações que você precisa realizar são criar e invocar o delegado.</span><span class="sxs-lookup"><span data-stu-id="32c30-228">In many cases, such as with callback methods, a delegate represents only one method, and the only actions you have to take are creating the delegate and invoking it.</span></span> 

<span data-ttu-id="32c30-229">Para delegados que representam vários métodos, o .NET fornece métodos das classes de delegado [Delegate](xref:System.Delegate) e [MulticastDelegate](xref:System.MulticastDelegate) para dar suporte a operações como adicionar um método à lista de invocação de um delegado (o método [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate))), remover um método (o método [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate))) e obter a lista de invocação (o método [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList)).</span><span class="sxs-lookup"><span data-stu-id="32c30-229">For delegates that represent multiple methods, .NET provides methods of the [Delegate](xref:System.Delegate) and [MulticastDelegate](xref:System.MulticastDelegate) delegate classes to support operations such as adding a method to a delegate's invocation list (the [Delegate.Combine](xref:System.Delegate.Combine(System.Delegate,System.Delegate)) method), removing a method (the [Delegate.Remove](xref:System.Delegate.Remove(System.Delegate,System.Delegate)) method), and getting the invocation list (the [Delegate.GetInvocationList](xref:System.Delegate.GetInvocationList) method).</span></span>

> [!NOTE]
> <span data-ttu-id="32c30-230">Não é necessário usar esses métodos para delegados de manipuladores de eventos em C# ou Visual Basic, porque essas linguagens fornecem sintaxe para adicionar e remover manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="32c30-230">It is not necessary to use these methods for event-handler delegates in C# or Visual Basic, because these languages provide syntax for adding and removing event handlers.</span></span>

## <a name="type-definitions"></a><span data-ttu-id="32c30-231">Definições de tipo</span><span class="sxs-lookup"><span data-stu-id="32c30-231">Type definitions</span></span>

<span data-ttu-id="32c30-232">Uma definição de tipo inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="32c30-232">A type definition includes the following:</span></span> 

* <span data-ttu-id="32c30-233">Qualquer atributo definido no tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-233">Any attributes defined on the type.</span></span>

* <span data-ttu-id="32c30-234">A acessibilidade do tipo (visibilidade).</span><span class="sxs-lookup"><span data-stu-id="32c30-234">The type's accessibility (visibility).</span></span>

* <span data-ttu-id="32c30-235">O nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-235">The type's name.</span></span>

* <span data-ttu-id="32c30-236">O tipo de base do tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-236">The type's base type.</span></span>

* <span data-ttu-id="32c30-237">Qualquer interface implementada pelo tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-237">Any interfaces implemented by the type.</span></span>

* <span data-ttu-id="32c30-238">Definições para cada um dos membros do tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-238">Definitions for each of the type's members.</span></span>

### <a name="attributes"></a><span data-ttu-id="32c30-239">Atributos</span><span class="sxs-lookup"><span data-stu-id="32c30-239">Attributes</span></span>

<span data-ttu-id="32c30-240">Atributos fornecem metadados adicionais definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="32c30-240">Attributes provide additional user-defined metadata.</span></span> <span data-ttu-id="32c30-241">Com frequência, eles são usados para armazenar informações adicionais sobre um tipo em seu assembly ou para modificar o comportamento de um membro de tipo no ambiente do tempo de design ou do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="32c30-241">Most commonly, they are used to store additional information about a type in its assembly, or to modify the behavior of a type member in either the design-time or run-time environment.</span></span> 

<span data-ttu-id="32c30-242">Os atributos são as próprias classes herdadas de [System.Attribute](xref:System.Attribute).</span><span class="sxs-lookup"><span data-stu-id="32c30-242">Attributes are themselves classes that inherit from [System.Attribute](xref:System.Attribute).</span></span> <span data-ttu-id="32c30-243">Linguagens que dão suporte ao uso de atributos têm sua própria sintaxe para aplicar atributos a um elemento de linguagem.</span><span class="sxs-lookup"><span data-stu-id="32c30-243">Languages that support the use of attributes each have their own syntax for applying attributes to a language element.</span></span> <span data-ttu-id="32c30-244">Os atributos podem ser aplicados a praticamente qualquer elemento de linguagem. Os elementos específicos para os quais um atributo pode ser aplicado são definidos pelo [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) aplicado à classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="32c30-244">Attributes can be applied to almost any language element; the specific elements to which an attribute can be applied are defined by the [AttributeUsageAttribute](xref:System.AttributeUsageAttribute) that is applied to that attribute class.</span></span>

### <a name="type-accessibility"></a><span data-ttu-id="32c30-245">Acessibilidade de tipo</span><span class="sxs-lookup"><span data-stu-id="32c30-245">Type accessibility</span></span>

<span data-ttu-id="32c30-246">Todos os tipos têm um modificador que rege sua acessibilidade de outros tipos.</span><span class="sxs-lookup"><span data-stu-id="32c30-246">All types have a modifier that governs their accessibility from other types.</span></span> <span data-ttu-id="32c30-247">A tabela a seguir descreve as acessibilidades de tipo que o tempo de execução dá suporte.</span><span class="sxs-lookup"><span data-stu-id="32c30-247">The following table describes the type accessibilities supported by the runtime.</span></span>

<span data-ttu-id="32c30-248">Acessibilidade</span><span class="sxs-lookup"><span data-stu-id="32c30-248">Accessibility</span></span> | <span data-ttu-id="32c30-249">Descrição</span><span class="sxs-lookup"><span data-stu-id="32c30-249">Description</span></span>
------------- | -----------
<span data-ttu-id="32c30-250">public</span><span class="sxs-lookup"><span data-stu-id="32c30-250">public</span></span> | <span data-ttu-id="32c30-251">O tipo é acessível por todos os assemblies.</span><span class="sxs-lookup"><span data-stu-id="32c30-251">The type is accessible by all assemblies.</span></span>
<span data-ttu-id="32c30-252">assembly</span><span class="sxs-lookup"><span data-stu-id="32c30-252">assembly</span></span> | <span data-ttu-id="32c30-253">O tipo é acessível somente dentro do assembly.</span><span class="sxs-lookup"><span data-stu-id="32c30-253">The type is accessible only from within its assembly.</span></span>

<span data-ttu-id="32c30-254">A acessibilidade de um tipo aninhado depende do domínio de acessibilidade, que é determinado pela acessibilidade declarada do membro e pelo domínio da acessibilidade do tipo imediatamente contido.</span><span class="sxs-lookup"><span data-stu-id="32c30-254">The accessibility of a nested type depends on its accessibility domain, which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="32c30-255">Entretanto, o domínio de acessibilidade de um tipo aninhado não pode exceder o do tipo contido.</span><span class="sxs-lookup"><span data-stu-id="32c30-255">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>

<span data-ttu-id="32c30-256">O domínio de acessibilidade de um membro aninhado `M` declarado em um tipo `T` em um programa `P` é definido da seguinte forma (observe que `M` pode ser um tipo):</span><span class="sxs-lookup"><span data-stu-id="32c30-256">The accessibility domain of a nested member `M` declared in a type `T`within a program `P` is defined as follows (noting that `M` might itself be a type):</span></span> 

* <span data-ttu-id="32c30-257">Se a acessibilidade declarada de `M` for `public`, o domínio de acessibilidade de `M` será o domínio de acessibilidade de `T`.</span><span class="sxs-lookup"><span data-stu-id="32c30-257">If the declared accessibility of `M` is `public`, the accessibility domain of `M` is the accessibility domain of `T`.</span></span>

* <span data-ttu-id="32c30-258">Se a acessibilidade declarada de `M` for `protected internal`, o domínio de acessibilidade de `M` será a interseção do domínio de acessibilidade de `T` com o texto de programa de `P` e o texto de programa de qualquer tipo derivado de `T` declarado fora de `P`.</span><span class="sxs-lookup"><span data-stu-id="32c30-258">If the declared accessibility of `M` is `protected internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `P` and the program text of any type derived from `T` declared outside `P`.</span></span>

* <span data-ttu-id="32c30-259">Se a acessibilidade declarada de `M` for `protected`, o domínio de acessibilidade de `M` será a interseção do domínio de acessibilidade de `T` com o texto do programa de `T` e qualquer tipo derivado de `T`.</span><span class="sxs-lookup"><span data-stu-id="32c30-259">If the declared accessibility of `M` is `protected`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of `T` and any type derived from `T`.</span></span>

* <span data-ttu-id="32c30-260">Se a acessibilidade declarada de `M` for `internal`, o domínio de acessibilidade de `M` será a interseção do domínio de acessibilidade de `T` com o texto de programa de `P`.</span><span class="sxs-lookup"><span data-stu-id="32c30-260">If the declared accessibility of `M` is `internal`, the accessibility domain of `M` is the intersection of the accessibility domain of `T` with the program text of`P`.</span></span>

* <span data-ttu-id="32c30-261">Se a acessibilidade declarada de `M` for `private`, o domínio de acessibilidade de `M` será o texto de programa de `T`.</span><span class="sxs-lookup"><span data-stu-id="32c30-261">If the declared accessibility of `M` is `private`, the accessibility domain of `M` is the program text of `T`.</span></span>

### <a name="type-names"></a><span data-ttu-id="32c30-262">Nomes de tipo</span><span class="sxs-lookup"><span data-stu-id="32c30-262">Type names</span></span>

<span data-ttu-id="32c30-263">O Common Type System impõe apenas duas restrições de nomes:</span><span class="sxs-lookup"><span data-stu-id="32c30-263">The common type system imposes only two restrictions on names:</span></span> 

* <span data-ttu-id="32c30-264">Todos os nomes são codificados como cadeias de caracteres Unicode (16 bits).</span><span class="sxs-lookup"><span data-stu-id="32c30-264">All names are encoded as strings of Unicode (16-bit) characters.</span></span>

* <span data-ttu-id="32c30-265">Não são permitidos nomes que tenham um valor (16 bits) inserido de 0x0000.</span><span class="sxs-lookup"><span data-stu-id="32c30-265">Names are not permitted to have an embedded (16-bit) value of 0x0000.</span></span>

<span data-ttu-id="32c30-266">No entanto, a maioria das linguagens impõe restrições adicionais em nomes de tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-266">However, most languages impose additional restrictions on type names.</span></span> <span data-ttu-id="32c30-267">Todas as comparações são feitas em uma base byte por byte e, assim, diferenciam maiúsculas de minúsculas e são independentes de localidade.</span><span class="sxs-lookup"><span data-stu-id="32c30-267">All comparisons are done on a byte-by-byte basis, and are therefore case-sensitive and locale-independent.</span></span>

<span data-ttu-id="32c30-268">Embora um tipo possa referenciar tipos de outros módulos e assemblies, um tipo deve ser totalmente definido em um módulo do .NET.</span><span class="sxs-lookup"><span data-stu-id="32c30-268">Although a type might reference types from other modules and assemblies, a type must be fully defined within one .NET module.</span></span> <span data-ttu-id="32c30-269">(Dependendo do suporte do compilador, no entanto, ele pode ser dividido em vários arquivos de código-fonte.) Nomes de tipo precisam ser exclusivos somente dentro de um namespace.</span><span class="sxs-lookup"><span data-stu-id="32c30-269">(Depending on compiler support, however, it can be divided into multiple source code files.) Type names need be unique only within a namespace.</span></span> <span data-ttu-id="32c30-270">Para identificar totalmente um tipo, o nome de tipo deve ser qualificado pelo namespace que contém a implementação do tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-270">To fully identify a type, the type name must be qualified by the namespace that contains the implementation of the type.</span></span>

### <a name="base-types-and-interfaces"></a><span data-ttu-id="32c30-271">Tipos de base e interfaces</span><span class="sxs-lookup"><span data-stu-id="32c30-271">Base types and interfaces</span></span>

<span data-ttu-id="32c30-272">Um tipo pode herdar valores e comportamentos de outro tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-272">A type can inherit values and behaviors from another type.</span></span> <span data-ttu-id="32c30-273">O Common Type System não permite que tipos sejam herdados de mais de um tipo de base.</span><span class="sxs-lookup"><span data-stu-id="32c30-273">The common type system does not allow types to inherit from more than one base type.</span></span>

<span data-ttu-id="32c30-274">Um tipo pode implementar um número qualquer de interfaces.</span><span class="sxs-lookup"><span data-stu-id="32c30-274">A type can implement any number of interfaces.</span></span> <span data-ttu-id="32c30-275">Para implementar uma interface, um tipo deve implementar todos os membros virtuais dessa interface.</span><span class="sxs-lookup"><span data-stu-id="32c30-275">To implement an interface, a type must implement all the virtual members of that interface.</span></span> <span data-ttu-id="32c30-276">Um método virtual pode ser implementado por um tipo derivado e pode ser invocado estática ou dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="32c30-276">A virtual method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span>

## <a name="type-members"></a><span data-ttu-id="32c30-277">Membros de tipos</span><span class="sxs-lookup"><span data-stu-id="32c30-277">Type members</span></span>

<span data-ttu-id="32c30-278">O tempo de execução permite que você defina os membros do tipo, o que especifica o comportamento e o estado de um tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-278">The runtime enables you to define members of your type, which specifies the behavior and state of a type.</span></span> <span data-ttu-id="32c30-279">Os membros de tipo incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="32c30-279">Type members include the following:</span></span>

* [<span data-ttu-id="32c30-280">Campos</span><span class="sxs-lookup"><span data-stu-id="32c30-280">Fields</span></span>](#fields)

* [<span data-ttu-id="32c30-281">Propriedades</span><span class="sxs-lookup"><span data-stu-id="32c30-281">Properties</span></span>](#properties)

* [<span data-ttu-id="32c30-282">Métodos</span><span class="sxs-lookup"><span data-stu-id="32c30-282">Methods</span></span>](#methods)

* [<span data-ttu-id="32c30-283">Construtores</span><span class="sxs-lookup"><span data-stu-id="32c30-283">Constructors</span></span>](#constructors)

* [<span data-ttu-id="32c30-284">Eventos</span><span class="sxs-lookup"><span data-stu-id="32c30-284">Events</span></span>](#events)

* [<span data-ttu-id="32c30-285">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="32c30-285">Nested types</span></span>](#nested-types)

### <a name="fields"></a><span data-ttu-id="32c30-286">Campos</span><span class="sxs-lookup"><span data-stu-id="32c30-286">Fields</span></span>

<span data-ttu-id="32c30-287">Um campo descreve e contém parte do estado do tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-287">A field describes and contains part of the type's state.</span></span> <span data-ttu-id="32c30-288">Campos podem ser de qualquer tipo com suporte pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="32c30-288">Fields can be of any type supported by the runtime.</span></span> <span data-ttu-id="32c30-289">Geralmente, os campos são `private` ou `protected`, de forma que são acessíveis somente de dentro da classe ou de uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="32c30-289">Most commonly, fields are either `private` or `protected`, so that they are accessible only from within the class or from a derived class.</span></span> <span data-ttu-id="32c30-290">Se o valor de um campo puder ser modificado fora de seu tipo, um acessador do conjunto de propriedades normalmente será usado.</span><span class="sxs-lookup"><span data-stu-id="32c30-290">If the value of a field can be modified from outside its type, a property set accessor is typically used.</span></span> <span data-ttu-id="32c30-291">Os campos expostos publicamente geralmente são somente leitura e podem ser de dois tipos:</span><span class="sxs-lookup"><span data-stu-id="32c30-291">Publicly exposed fields are usually read-only and can be of two types:</span></span> 

* <span data-ttu-id="32c30-292">Constantes, cujo valor é atribuído no tempo de design.</span><span class="sxs-lookup"><span data-stu-id="32c30-292">Constants, whose value is assigned at design time.</span></span> <span data-ttu-id="32c30-293">Esses são membros estáticos de uma classe, embora eles não sejam definidos usando a palavra-chave `static` (`Shared` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="32c30-293">These are static members of a class, although they are not defined using the `static` (`Shared` in Visual Basic) keyword.</span></span>

* <span data-ttu-id="32c30-294">Variáveis somente leitura, cujos valores podem ser atribuídos no construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="32c30-294">Read-only variables, whose values can be assigned in the class constructor.</span></span>

<span data-ttu-id="32c30-295">O exemplo a seguir ilustra esses dois usos de campos somente leitura.</span><span class="sxs-lookup"><span data-stu-id="32c30-295">The following example illustrates these two usages of read-only fields.</span></span>

```csharp
using System;

public class Constants
{
   public const double Pi = 3.1416;
   public readonly DateTime BirthDate;

   public Constants(DateTime birthDate)
   {
      this.BirthDate = birthDate;
   }
}

public class Example
{
   public static void Main()
   {
      Constants con = new Constants(new DateTime(1974, 8, 18));
      Console.Write(Constants.Pi + "\n");
      Console.Write(con.BirthDate.ToString("d") + "\n");
   }
}
// The example displays the following output if run on a system whose current
// culture is en-US:
//    3.1417
//    8/18/1974
```

```vb
Public Class Constants
   Public Const Pi As Double = 3.1416
   Public ReadOnly BirthDate As Date

   Public Sub New(birthDate As Date)
      Me.BirthDate = birthDate
   End Sub
End Class

Public Module Example
   Public Sub Main()
      Dim con As New Constants(#8/18/1974#)
      Console.WriteLine(Constants.Pi.ToString())
      Console.WriteLine(con.BirthDate.ToString("d"))
   End Sub
End Module
' The example displays the following output if run on a system whose current
' culture is en-US:
'    3.1417
'    8/18/1974
```

### <a name="properties"></a><span data-ttu-id="32c30-296">Propriedades</span><span class="sxs-lookup"><span data-stu-id="32c30-296">Properties</span></span>

<span data-ttu-id="32c30-297">Uma propriedade nomeia um valor ou um estado do tipo e define métodos para obter ou definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="32c30-297">A property names a value or state of the type and defines methods for getting or setting the property's value.</span></span> <span data-ttu-id="32c30-298">Propriedades podem ser tipos primitivos, coleções de tipos primitivos, tipos definidos pelo usuário ou coleções de tipos definidos pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="32c30-298">Properties can be primitive types, collections of primitive types, user-defined types, or collections of user-defined types.</span></span> <span data-ttu-id="32c30-299">Propriedades são, frequentemente, usadas para manter a interface pública de um tipo independente da representação real do tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-299">Properties are often used to keep the public interface of a type independent from the type's actual representation.</span></span> <span data-ttu-id="32c30-300">Isso permite que as propriedades reflitam os valores que não estão armazenados diretamente na classe (por exemplo, quando uma propriedade retorna um valor computado) ou para realizar uma validação antes de os valores serem atribuídos a campos privados.</span><span class="sxs-lookup"><span data-stu-id="32c30-300">This enables properties to reflect values that are not directly stored in the class (for example, when a property returns a computed value) or to perform validation before values are assigned to private fields.</span></span> <span data-ttu-id="32c30-301">O exemplo a seguir ilustra o padrão mais recente.</span><span class="sxs-lookup"><span data-stu-id="32c30-301">The following example illustrates the latter pattern.</span></span>

```csharp
using System;

public class Person
{
   private int m_Age;

   public int Age
   { 
      get { return m_Age; }
      set {
         if (value < 0 || value > 125)
         {
            throw new ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.");
         }
         else
         {
            m_Age = value;
         }         
      }
   }
}
```

```vb
Public Class Person
   Private m_Age As Integer

   Public Property Age As Integer
      Get
         Return m_Age
      End Get
      Set
         If value < 0 Or value > 125 Then
            Throw New ArgumentOutOfRangeException("The value of the Age property must be between 0 and 125.")
         Else
            m_Age = value
         End If
      End Set
   End Property
End Class
```

<span data-ttu-id="32c30-302">Além de incluir a própria propriedade, a MSIL (Microsoft Intermediate Language) para um tipo que contém uma propriedade legível inclui um método `get`*_propertyname* e a MSIL para um tipo que contém uma propriedade gravável inclui um método `set`*_propertyname*.</span><span class="sxs-lookup"><span data-stu-id="32c30-302">In addition to including the property itself, the Microsoft intermediate language (MSIL) for a type that contains a readable property includes a `get`*_propertyname* method, and the MSIL for a type that contains a writable property includes a `set`*_propertyname* method.</span></span>

### <a name="methods"></a><span data-ttu-id="32c30-303">Métodos</span><span class="sxs-lookup"><span data-stu-id="32c30-303">Methods</span></span>

<span data-ttu-id="32c30-304">Um método descreve as operações disponíveis no tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-304">A method describes operations that are available on the type.</span></span> <span data-ttu-id="32c30-305">A assinatura do método especifica os tipos permitidos de todos seus parâmetros e o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="32c30-305">A method's signature specifies the allowable types of all its parameters and of its return value.</span></span>

<span data-ttu-id="32c30-306">Embora a maioria dos métodos defina o número exato de parâmetros necessários para chamadas de método, alguns métodos dão suporte a um número variável de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="32c30-306">Although most methods define the precise number of parameters required for method calls, some methods support a variable number of parameters.</span></span> <span data-ttu-id="32c30-307">O parâmetro final declarado desses métodos é marcado com o atributo [ParamArrayAttribute](xref:System.ParamArrayAttribute).</span><span class="sxs-lookup"><span data-stu-id="32c30-307">The final declared parameter of these methods is marked with the [ParamArrayAttribute](xref:System.ParamArrayAttribute) attribute.</span></span> <span data-ttu-id="32c30-308">Compiladores de linguagem normalmente fornecem uma palavra-chave, como `params` no C# e `ParamArray` no Visual Basic, que tornam o uso explícito de [ParamArrayAttribute](xref:System.ParamArrayAttribute) desnecessário.</span><span class="sxs-lookup"><span data-stu-id="32c30-308">Language compilers typically provide a keyword, such as `params` in C# and `ParamArray` in Visual Basic, that makes explicit use of [ParamArrayAttribute](xref:System.ParamArrayAttribute) unnecessary.</span></span>

### <a name="constructors"></a><span data-ttu-id="32c30-309">Construtores</span><span class="sxs-lookup"><span data-stu-id="32c30-309">Constructors</span></span>

<span data-ttu-id="32c30-310">Um construtor é um tipo especial de método que cria novas instâncias de uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="32c30-310">A constructor is a special kind of method that creates new instances of a class or structure.</span></span> <span data-ttu-id="32c30-311">Assim como qualquer outro método, um construtor pode incluir parâmetros. No entanto, os construtores não têm nenhum valor retornado (ou seja, eles retornam `void`).</span><span class="sxs-lookup"><span data-stu-id="32c30-311">Like any other method, a constructor can include parameters; however, constructors have no return value (that is, they return `void`).</span></span> 

<span data-ttu-id="32c30-312">Se o código-fonte para uma classe não definir explicitamente um construtor, o compilador incluirá um construtor padrão (sem parâmetros).</span><span class="sxs-lookup"><span data-stu-id="32c30-312">If the source code for a class does not explicitly define a constructor, the compiler includes a default (parameterless) constructor.</span></span> <span data-ttu-id="32c30-313">No entanto, se o código-fonte de uma classe definir apenas construtores com parâmetros, o compilador do C# não gerará um construtor sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="32c30-313">However, if the source code for a class defines only parameterized constructors, the C# compiler doesn't generate a parameterless constructor.</span></span>

<span data-ttu-id="32c30-314">Se o código-fonte de uma estrutura definir construtores, eles deverão ser parametrizados. Uma estrutura não pode definir um construtor padrão (sem parâmetros) e os compiladores não geram construtores sem parâmetros para estruturas ou outros tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="32c30-314">If the source code for a structure defines constructors, they must be parameterized; a structure cannot define a default (parameterless) constructor, and compilers do not generate parameterless constructors for structures or other value types.</span></span> <span data-ttu-id="32c30-315">Todos os tipos de valor têm um construtor padrão implícito.</span><span class="sxs-lookup"><span data-stu-id="32c30-315">All value types do have an implicit default constructor.</span></span> <span data-ttu-id="32c30-316">Esse construtor é implementado pelo Common Language Runtime e inicializa todos os campos da estrutura com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="32c30-316">This constructor is implemented by the common language runtime and initializes all fields of the structure to their default values.</span></span> 

### <a name="events"></a><span data-ttu-id="32c30-317">Eventos</span><span class="sxs-lookup"><span data-stu-id="32c30-317">Events</span></span>

<span data-ttu-id="32c30-318">Um evento define um incidente que pode ser respondido e define métodos para assinar, cancelar a assinatura e acionar o evento.</span><span class="sxs-lookup"><span data-stu-id="32c30-318">An event defines an incident that can be responded to, and defines methods for subscribing to, unsubscribing from, and raising the event.</span></span> <span data-ttu-id="32c30-319">Eventos são frequentemente usados para informar outros tipos de alterações de estado.</span><span class="sxs-lookup"><span data-stu-id="32c30-319">Events are often used to inform other types of state changes.</span></span>

### <a name="nested-types"></a><span data-ttu-id="32c30-320">Tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="32c30-320">Nested types</span></span>

<span data-ttu-id="32c30-321">Um tipo aninhado é um tipo membro de outros tipos.</span><span class="sxs-lookup"><span data-stu-id="32c30-321">A nested type is a type that is a member of some other type.</span></span> <span data-ttu-id="32c30-322">Os tipos aninhados devem ser unidos ao tipo de contenção e não devem ser utilizados como tipos de uso geral.</span><span class="sxs-lookup"><span data-stu-id="32c30-322">Nested types should be tightly coupled to their containing type and must not be useful as a general-purpose type.</span></span> <span data-ttu-id="32c30-323">Os tipos aninhados são úteis quando o tipo declarativo usa e cria instâncias do tipo aninhado e o uso do tipo aninhado não é exposto em membros públicos.</span><span class="sxs-lookup"><span data-stu-id="32c30-323">Nested types are useful when the declaring type uses and creates instances of the nested type, and use of the nested type is not exposed in public members.</span></span>

<span data-ttu-id="32c30-324">Os tipos aninhados são confusos para alguns desenvolvedores e não devem ficar publicamente visíveis, a menos que haja um motivo forte para a visibilidade.</span><span class="sxs-lookup"><span data-stu-id="32c30-324">Nested types are confusing to some developers and should not be publicly visible unless there is a compelling reason for visibility.</span></span> <span data-ttu-id="32c30-325">Em uma biblioteca bem projetada, os desenvolvedores raramente precisam usar tipos aninhados para instanciar objetos ou declarar variáveis.</span><span class="sxs-lookup"><span data-stu-id="32c30-325">In a well-designed library, developers should rarely have to use nested types to instantiate objects or declare variables.</span></span>

## <a name="characteristics-of-type-members"></a><span data-ttu-id="32c30-326">Características de membros de tipo</span><span class="sxs-lookup"><span data-stu-id="32c30-326">Characteristics of type members</span></span>

<span data-ttu-id="32c30-327">O Common Type System permite que os membros de tipo tenham várias características. No entanto, as linguagens não necessariamente dão suporte a todas elas.</span><span class="sxs-lookup"><span data-stu-id="32c30-327">The common type system allows type members to have a variety of characteristics; however, languages are not required to support all these characteristics.</span></span> <span data-ttu-id="32c30-328">A tabela a seguir descreve as características de um membro.</span><span class="sxs-lookup"><span data-stu-id="32c30-328">The following table describes member characteristics.</span></span>

<span data-ttu-id="32c30-329">Característica</span><span class="sxs-lookup"><span data-stu-id="32c30-329">Characteristic</span></span> | <span data-ttu-id="32c30-330">Pode ser aplicado a</span><span class="sxs-lookup"><span data-stu-id="32c30-330">Can apply to</span></span> | <span data-ttu-id="32c30-331">Descrição</span><span class="sxs-lookup"><span data-stu-id="32c30-331">Description</span></span>
-------------- | ------------ | -----------
<span data-ttu-id="32c30-332">abstract</span><span class="sxs-lookup"><span data-stu-id="32c30-332">abstract</span></span> | <span data-ttu-id="32c30-333">Métodos, propriedades e eventos</span><span class="sxs-lookup"><span data-stu-id="32c30-333">Methods, properties, and events</span></span> | <span data-ttu-id="32c30-334">O tipo não fornece a implementação do método.</span><span class="sxs-lookup"><span data-stu-id="32c30-334">The type does not supply the method's implementation.</span></span> <span data-ttu-id="32c30-335">Tipos que herdam ou implementam métodos abstratos devem fornecer uma implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="32c30-335">Types that inherit or implement abstract methods must supply an implementation for the method.</span></span> <span data-ttu-id="32c30-336">A única exceção é quando o tipo derivado é um tipo abstrato.</span><span class="sxs-lookup"><span data-stu-id="32c30-336">The only exception is when the derived type is itself an abstract type.</span></span> <span data-ttu-id="32c30-337">Todos os métodos abstratos são virtuais.</span><span class="sxs-lookup"><span data-stu-id="32c30-337">All abstract methods are virtual.</span></span>
<span data-ttu-id="32c30-338">private</span><span class="sxs-lookup"><span data-stu-id="32c30-338">private</span></span> | <span data-ttu-id="32c30-339">Todos</span><span class="sxs-lookup"><span data-stu-id="32c30-339">All</span></span> | <span data-ttu-id="32c30-340">Acessível somente dentro do mesmo tipo que o membro ou de um tipo aninhado.</span><span class="sxs-lookup"><span data-stu-id="32c30-340">Accessible only from within the same type as the member, or within a nested type.</span></span>
<span data-ttu-id="32c30-341">família</span><span class="sxs-lookup"><span data-stu-id="32c30-341">family</span></span> | <span data-ttu-id="32c30-342">Todos</span><span class="sxs-lookup"><span data-stu-id="32c30-342">All</span></span> | <span data-ttu-id="32c30-343">Acessível dentro do mesmo tipo que o membro e de tipos derivados herdados dele.</span><span class="sxs-lookup"><span data-stu-id="32c30-343">Accessible from within the same type as the member, and from derived types that inherit from it.</span></span>
<span data-ttu-id="32c30-344">assembly</span><span class="sxs-lookup"><span data-stu-id="32c30-344">assemby</span></span> | <span data-ttu-id="32c30-345">Todos</span><span class="sxs-lookup"><span data-stu-id="32c30-345">All</span></span> | <span data-ttu-id="32c30-346">Acessível somente no assembly no qual o tipo é definido.</span><span class="sxs-lookup"><span data-stu-id="32c30-346">Accessible only in the assembly in which the type is defined.</span></span>
<span data-ttu-id="32c30-347">família e assembly</span><span class="sxs-lookup"><span data-stu-id="32c30-347">family and assembly</span></span> | <span data-ttu-id="32c30-348">Todos</span><span class="sxs-lookup"><span data-stu-id="32c30-348">All</span></span> | <span data-ttu-id="32c30-349">Acessíveis somente em tipos qualificados para acesso de família e assembly.</span><span class="sxs-lookup"><span data-stu-id="32c30-349">Accessible only from types that qualify for both family and assembly access.</span></span>
<span data-ttu-id="32c30-350">família ou assembly</span><span class="sxs-lookup"><span data-stu-id="32c30-350">family or assemby</span></span> | <span data-ttu-id="32c30-351">Todos</span><span class="sxs-lookup"><span data-stu-id="32c30-351">All</span></span> | <span data-ttu-id="32c30-352">Acessíveis somente dentro de tipos qualificados para acesso de família ou assembly.</span><span class="sxs-lookup"><span data-stu-id="32c30-352">Accessible only from types that qualify for either family or assembly access.</span></span>
<span data-ttu-id="32c30-353">public</span><span class="sxs-lookup"><span data-stu-id="32c30-353">public</span></span> | <span data-ttu-id="32c30-354">Todos</span><span class="sxs-lookup"><span data-stu-id="32c30-354">All</span></span> | <span data-ttu-id="32c30-355">Acessíveis dentro de qualquer tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-355">Accessible from any type.</span></span>
<span data-ttu-id="32c30-356">final</span><span class="sxs-lookup"><span data-stu-id="32c30-356">final</span></span> | <span data-ttu-id="32c30-357">Métodos, propriedades e eventos</span><span class="sxs-lookup"><span data-stu-id="32c30-357">Methods, properties, and events</span></span> | <span data-ttu-id="32c30-358">Um método virtual não pode ser substituído em um tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="32c30-358">The virtual method cannot be overridden in a derived type.</span></span>
<span data-ttu-id="32c30-359">initialize-only</span><span class="sxs-lookup"><span data-stu-id="32c30-359">initialize-only</span></span> | <span data-ttu-id="32c30-360">Campos</span><span class="sxs-lookup"><span data-stu-id="32c30-360">Fields</span></span> | <span data-ttu-id="32c30-361">O valor pode apenas ser inicializado e não pode ser gravado após a inicialização.</span><span class="sxs-lookup"><span data-stu-id="32c30-361">The value can only be initialized, and cannot be written after initialization.</span></span>
<span data-ttu-id="32c30-362">instância</span><span class="sxs-lookup"><span data-stu-id="32c30-362">instance</span></span> | <span data-ttu-id="32c30-363">Campos, métodos, propriedades e eventos</span><span class="sxs-lookup"><span data-stu-id="32c30-363">Fields, methods, properties, and events</span></span> | <span data-ttu-id="32c30-364">Se um membro não estiver marcado como `static` (C#), `Shared` (Visual Basic), `virtual` (C#) ou `Overridable` (Visual Basic), ele será um membro de instância (não há palavra-chave de instância).</span><span class="sxs-lookup"><span data-stu-id="32c30-364">If a member is not marked as `static` (C#), `Shared` (Visual Basic), `virtual` (C#), or `Overridable` (Visual Basic),  it is an instance member (there is no instance keyword).</span></span> <span data-ttu-id="32c30-365">Haverá tantas cópias desses membros na memória quanto objetos que as usam.</span><span class="sxs-lookup"><span data-stu-id="32c30-365">There will be as many copies of such members in memory as there are objects that use it.</span></span>
<span data-ttu-id="32c30-366">literal</span><span class="sxs-lookup"><span data-stu-id="32c30-366">literal</span></span> | <span data-ttu-id="32c30-367">Campos</span><span class="sxs-lookup"><span data-stu-id="32c30-367">Fields</span></span> | <span data-ttu-id="32c30-368">O valor atribuído ao campo é um valor fixo, conhecido no tempo de compilação, de um tipo de valor interno.</span><span class="sxs-lookup"><span data-stu-id="32c30-368">The value assigned to the field is a fixed value, known at compile time, of a built-in value type.</span></span> <span data-ttu-id="32c30-369">Às vezes, campos literais são conhecidos como constantes.</span><span class="sxs-lookup"><span data-stu-id="32c30-369">Literal fields are sometimes referred to as constants.</span></span>
<span data-ttu-id="32c30-370">newslot ou override</span><span class="sxs-lookup"><span data-stu-id="32c30-370">newslot or override</span></span> | <span data-ttu-id="32c30-371">Todos</span><span class="sxs-lookup"><span data-stu-id="32c30-371">All</span></span> | <span data-ttu-id="32c30-372">Define como o membro interage com os membros herdados que têm a mesma assinatura: `newslot` oculta membros herdados que têm a mesma assinatura; `override` substitui a definição de um método virtual herdado.</span><span class="sxs-lookup"><span data-stu-id="32c30-372">Defines how the member interacts with inherited members that have the same signature: `newslot` hides inherited members that have the same signature; `override` replaces the definition of an inherited virtual method.</span></span> <span data-ttu-id="32c30-373">O padrão é newslot.</span><span class="sxs-lookup"><span data-stu-id="32c30-373">The default is newslot.</span></span>
<span data-ttu-id="32c30-374">static</span><span class="sxs-lookup"><span data-stu-id="32c30-374">static</span></span> | <span data-ttu-id="32c30-375">Campos, métodos, propriedades e eventos</span><span class="sxs-lookup"><span data-stu-id="32c30-375">Fields, methods, properties, and events</span></span> | <span data-ttu-id="32c30-376">O membro pertence ao tipo no qual está definido e não a uma instância particular do tipo; o membro existirá mesmo se uma instância do tipo não tiver sido criada e será compartilhado entre todas as instâncias do tipo.</span><span class="sxs-lookup"><span data-stu-id="32c30-376">The member belongs to the type it is defined on, not to a particular instance of the type; the member exists even if an instance of the type is not created, and it is shared among all instances of the type.</span></span>
<span data-ttu-id="32c30-377">virtual</span><span class="sxs-lookup"><span data-stu-id="32c30-377">virtual</span></span> | <span data-ttu-id="32c30-378">Métodos, propriedades e eventos</span><span class="sxs-lookup"><span data-stu-id="32c30-378">Methods, properties, and events</span></span> | <span data-ttu-id="32c30-379">O método pode ser implementado por um tipo derivado e pode ser invocado estática ou dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="32c30-379">The method can be implemented by a derived type and can be invoked either statically or dynamically.</span></span> <span data-ttu-id="32c30-380">Se a invocação dinâmica for usada, o tipo da instância que faz a chamada no tempo de execução (em vez do tipo conhecido no tempo de compilação) determinará qual implementação do método será chamada.</span><span class="sxs-lookup"><span data-stu-id="32c30-380">If dynamic invocation is used, the type of the instance that makes the call at run time (rather than the type known at compile time) determines which implementation of the method is called.</span></span> <span data-ttu-id="32c30-381">Para invocar um método virtual estaticamente, a variável precisará ser convertida em um tipo que usa a versão desejada do método.</span><span class="sxs-lookup"><span data-stu-id="32c30-381">To invoke a virtual method statically, the variable might have to be cast to a type that uses the desired version of the method.</span></span>

### <a name="overloading"></a><span data-ttu-id="32c30-382">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="32c30-382">Overloading</span></span>

<span data-ttu-id="32c30-383">Cada membro de tipo tem uma assinatura exclusiva.</span><span class="sxs-lookup"><span data-stu-id="32c30-383">Each type member has a unique signature.</span></span> <span data-ttu-id="32c30-384">Assinaturas de método consistem no nome de método e em uma lista de parâmetros (a ordem e os tipos dos argumentos do método).</span><span class="sxs-lookup"><span data-stu-id="32c30-384">Method signatures consist of the method name and a parameter list (the order and types of the method's arguments).</span></span> <span data-ttu-id="32c30-385">Os vários métodos com o mesmo nome podem ser definidos em um tipo desde que suas assinaturas sejam diferentes.</span><span class="sxs-lookup"><span data-stu-id="32c30-385">Multiple methods with the same name can be defined within a type as long as their signatures differ.</span></span> <span data-ttu-id="32c30-386">Quando dois ou mais métodos com o mesmo nome forem definidos, diz-se que o método está sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="32c30-386">When two or more methods with the same name are defined, the method is said to be overloaded.</span></span> <span data-ttu-id="32c30-387">Por exemplo, em [System.Char](xref:System.Char), o método `IsDigit` está sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="32c30-387">For example, in [System.Char](xref:System.Char), the `IsDigit` method is overloaded.</span></span> <span data-ttu-id="32c30-388">Um método utiliza um [Char](xref:System.Char).</span><span class="sxs-lookup"><span data-stu-id="32c30-388">One method takes a [Char](xref:System.Char).</span></span> <span data-ttu-id="32c30-389">O outro método utiliza uma [Cadeia de Caracteres](xref:System.String) e um [Int32](xref:System.Int32).</span><span class="sxs-lookup"><span data-stu-id="32c30-389">The other method takes a [String](xref:System.String) and an [Int32](xref:System.Int32).</span></span> 

> [!NOTE]
> <span data-ttu-id="32c30-390">O tipo de retorno não é considerado parte da assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="32c30-390">The return type is not considered part of a method's signature.</span></span> <span data-ttu-id="32c30-391">Ou seja, os métodos não poderão ser sobrecarregados se diferirem somente pelo tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="32c30-391">That is, methods cannot be overloaded if they differ only by return type.</span></span>

### <a name="inheriting-overriding-and-hiding-members"></a><span data-ttu-id="32c30-392">Herança, substituição e membros ocultos</span><span class="sxs-lookup"><span data-stu-id="32c30-392">Inheriting, overriding, and hiding members</span></span>

<span data-ttu-id="32c30-393">Um tipo derivado herda todos os membros de seu tipo de base; ou seja, esses membros são definidos e disponibilizados para o tipo derivado.</span><span class="sxs-lookup"><span data-stu-id="32c30-393">A derived type inherits all members of its base type; that is, these members are defined on, and available to, the derived type.</span></span> <span data-ttu-id="32c30-394">O comportamento, ou qualidades, de membros herdados pode ser modificado de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="32c30-394">The behavior or qualities of inherited members can be modified in two ways:</span></span> 

* <span data-ttu-id="32c30-395">Um tipo derivado pode ocultar um membro herdado definindo um novo membro com a mesma assinatura.</span><span class="sxs-lookup"><span data-stu-id="32c30-395">A derived type can hide an inherited member by defining a new member with the same signature.</span></span> <span data-ttu-id="32c30-396">Isso pode ser feito para fazer um membro privado anteriormente público ou para definir o novo comportamento de um método herdado marcado como `final`.</span><span class="sxs-lookup"><span data-stu-id="32c30-396">This might be done to make a previously public member private or to define new behavior for an inherited method that is marked as `final`.</span></span>

* <span data-ttu-id="32c30-397">Um tipo derivado pode substituir um método virtual herdado.</span><span class="sxs-lookup"><span data-stu-id="32c30-397">A derived type can override an inherited virtual method.</span></span> <span data-ttu-id="32c30-398">O método de substituição fornece uma nova definição do método que será invocado com base no tipo do valor no tempo de execução em vez do tipo de variável conhecido no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="32c30-398">The overriding method provides a new definition of the method that will be invoked based on the type of the value at run time rather than the type of the variable known at compile time.</span></span> <span data-ttu-id="32c30-399">Um método poderá substituir um método virtual somente se o método virtual não estiver marcado como `final` e o novo método for tão acessível quanto o método virtual.</span><span class="sxs-lookup"><span data-stu-id="32c30-399">A method can override a virtual method only if the virtual method is not marked as `final` and the new method is at least as accessible as the virtual method.</span></span>

## <a name="see-also"></a><span data-ttu-id="32c30-400">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32c30-400">See also</span></span>

[<span data-ttu-id="32c30-401">Conversão de tipos no .NET Framework</span><span class="sxs-lookup"><span data-stu-id="32c30-401">Type conversion in the .NET Framework</span></span>](type-conversion.md)
