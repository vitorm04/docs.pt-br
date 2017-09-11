---
title: "Interfaces (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
caps.latest.revision: 45
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0552cea71f66ba8c299b1706cab6778c9e3367c9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="interfaces-c-programming-guide"></a><span data-ttu-id="1f763-102">Interfaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1f763-102">Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="1f763-103">Uma interface contém definições para um grupo de funcionalidades relacionadas que uma [classe](../../../csharp/language-reference/keywords/class.md) ou um [struct](../../../csharp/language-reference/keywords/struct.md) pode implementar.</span><span class="sxs-lookup"><span data-stu-id="1f763-103">An interface contains definitions for a group of related functionalities that a [class](../../../csharp/language-reference/keywords/class.md) or a [struct](../../../csharp/language-reference/keywords/struct.md) can implement.</span></span>  
  
 <span data-ttu-id="1f763-104">Usando interfaces, você pode, por exemplo, incluir o comportamento de várias fontes em uma classe.</span><span class="sxs-lookup"><span data-stu-id="1f763-104">By using interfaces, you can, for example, include behavior from multiple sources in a class.</span></span> <span data-ttu-id="1f763-105">Essa funcionalidade é importante em C# porque a linguagem não dá suporte a várias heranças de classes.</span><span class="sxs-lookup"><span data-stu-id="1f763-105">That capability is important in C# because the language doesn't support multiple inheritance of classes.</span></span> <span data-ttu-id="1f763-106">Além disso, use uma interface se você deseja simular a herança para structs, pois eles não podem herdar de outro struct ou classe.</span><span class="sxs-lookup"><span data-stu-id="1f763-106">In addition, you must use an interface if you want to simulate inheritance for structs, because they can't actually inherit from another struct or class.</span></span>  
  
 <span data-ttu-id="1f763-107">Você define uma interface usando a palavra-chave [interface](../../../csharp/language-reference/keywords/interface.md), como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1f763-107">You define an interface by using the [interface](../../../csharp/language-reference/keywords/interface.md) keyword, as the following example shows.</span></span>  
  
 <span data-ttu-id="1f763-108">[!code-cs[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1f763-108">[!code-cs[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]</span></span>  
  
 <span data-ttu-id="1f763-109">Qualquer classe ou struct que implemente a interface <xref:System.IEquatable%601> deve conter uma definição para um método <xref:System.IEquatable%601.Equals%2A> que corresponda à assinatura que a interface especifica.</span><span class="sxs-lookup"><span data-stu-id="1f763-109">Any class or struct that implements the <xref:System.IEquatable%601> interface must contain a definition for an <xref:System.IEquatable%601.Equals%2A> method that matches the signature that the interface specifies.</span></span> <span data-ttu-id="1f763-110">Como resultado, você pode contar com uma classe que implementa `IEquatable<T>` para conter um método `Equals` com o qual uma instância da classe pode determinar se é igual a outra instância da mesma classe.</span><span class="sxs-lookup"><span data-stu-id="1f763-110">As a result, you can count on a class that implements `IEquatable<T>` to contain an `Equals` method with which an instance of the class can determine whether it's equal to another instance of the same class.</span></span>  
  
 <span data-ttu-id="1f763-111">A definição de `IEquatable<T>` não fornece uma implementação para `Equals`.</span><span class="sxs-lookup"><span data-stu-id="1f763-111">The definition of `IEquatable<T>` doesn’t provide an implementation for `Equals`.</span></span> <span data-ttu-id="1f763-112">A interface define somente a assinatura.</span><span class="sxs-lookup"><span data-stu-id="1f763-112">The interface defines only the signature.</span></span> <span data-ttu-id="1f763-113">Dessa forma, uma interface em C# é semelhante a uma classe abstrata, na qual todos os métodos são abstratos.</span><span class="sxs-lookup"><span data-stu-id="1f763-113">In that way, an interface in C# is similar to an abstract class in which all the methods are abstract.</span></span> <span data-ttu-id="1f763-114">No entanto, uma classe ou struct pode implementar várias interfaces, mas uma classe pode herdar apenas uma única classe, abstrata ou não.</span><span class="sxs-lookup"><span data-stu-id="1f763-114">However, a class or struct can implement multiple interfaces, but a class can inherit only a single class, abstract or not.</span></span> <span data-ttu-id="1f763-115">Assim, ao usar interfaces, você pode incluir o comportamento de várias fontes em uma classe.</span><span class="sxs-lookup"><span data-stu-id="1f763-115">Therefore, by using interfaces, you can include behavior from multiple sources in a class.</span></span>  
  
 <span data-ttu-id="1f763-116">Para obter mais informações sobre classes abstratas, consulte [Classes e membros de classes abstratos e lacrados](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="1f763-116">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="1f763-117">As interfaces podem conter métodos, propriedades, eventos, indexadores ou qualquer combinação desses quatro tipos de membro.</span><span class="sxs-lookup"><span data-stu-id="1f763-117">Interfaces can contain methods, properties, events, indexers, or any combination of those four member types.</span></span> <span data-ttu-id="1f763-118">Para obter links para exemplos, consulte as [seções relacionadas](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="1f763-118">For links to examples, see [Related Sections](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections).</span></span> <span data-ttu-id="1f763-119">Uma interface não pode conter constantes, campos, operadores, construtores de instância, finalizadores ou tipos.</span><span class="sxs-lookup"><span data-stu-id="1f763-119">An interface can't contain constants, fields, operators, instance constructors, finalizers, or types.</span></span> <span data-ttu-id="1f763-120">Os membros da interface são automaticamente públicos e eles não podem incluir nenhum modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="1f763-120">Interface members are automatically public, and they can't include any access modifiers.</span></span> <span data-ttu-id="1f763-121">Os membros também não podem ser [estáticos](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="1f763-121">Members also can't be [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
 <span data-ttu-id="1f763-122">Para implementar um membro de interface, o membro correspondente da classe de implementação deve ser público, não estático e ter o mesmo nome e assinatura do membro de interface.</span><span class="sxs-lookup"><span data-stu-id="1f763-122">To implement an interface member, the corresponding member of the implementing class must be public, non-static, and have the same name and signature as the interface member.</span></span>  
  
 <span data-ttu-id="1f763-123">Quando uma classe ou struct implementa uma interface, a classe ou o struct deve fornecer uma implementação para todos os membros que a interface define.</span><span class="sxs-lookup"><span data-stu-id="1f763-123">When a class or struct implements an interface, the class or struct must provide an implementation for all of the members that the interface defines.</span></span> <span data-ttu-id="1f763-124">A interface não fornece nenhuma funcionalidade que uma classe ou um struct possa herdar da forma que ela pode herdar a funcionalidade da classe base.</span><span class="sxs-lookup"><span data-stu-id="1f763-124">The interface itself provides no functionality that a class or struct can inherit in the way that it can inherit base class functionality.</span></span> <span data-ttu-id="1f763-125">No entanto, se uma classe base implementa uma interface, qualquer classe que é derivada da classe base herda essa implementação.</span><span class="sxs-lookup"><span data-stu-id="1f763-125">However, if a base class implements an interface, any class that's derived from the base class inherits that implementation.</span></span>  
  
 <span data-ttu-id="1f763-126">O exemplo a seguir mostra uma implementação da interface IEquatable<T\>.</span><span class="sxs-lookup"><span data-stu-id="1f763-126">The following example shows an implementation of the IEquatable<T\> interface.</span></span> <span data-ttu-id="1f763-127">A classe de implementação, `Car`, deverá fornecer uma implementação do método <xref:System.IEquatable%601.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f763-127">The implementing class, `Car`, must provide an implementation of the <xref:System.IEquatable%601.Equals%2A> method.</span></span>  
  
 <span data-ttu-id="1f763-128">[!code-cs[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1f763-128">[!code-cs[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]</span></span>  
  
 <span data-ttu-id="1f763-129">As propriedades e os indexadores de uma classe podem definir acessadores extras para uma propriedade ou o indexador que é definido em uma interface.</span><span class="sxs-lookup"><span data-stu-id="1f763-129">Properties and indexers of a class can define extra accessors for a property or indexer that's defined in an interface.</span></span> <span data-ttu-id="1f763-130">Por exemplo, uma interface pode declarar uma propriedade que tem um acessador [get](../../../csharp/language-reference/keywords/get.md).</span><span class="sxs-lookup"><span data-stu-id="1f763-130">For example, an interface might declare a property that has a [get](../../../csharp/language-reference/keywords/get.md) accessor.</span></span> <span data-ttu-id="1f763-131">A classe que implementa a interface pode declarar a mesma propriedade tanto com um acessador `get` quanto com um [set](../../../csharp/language-reference/keywords/set.md).</span><span class="sxs-lookup"><span data-stu-id="1f763-131">The class that implements the interface can declare the same property with both a `get` and [set](../../../csharp/language-reference/keywords/set.md) accessor.</span></span> <span data-ttu-id="1f763-132">No entanto, se a propriedade ou o indexador usa a implementação explícita, os acessadores devem corresponder.</span><span class="sxs-lookup"><span data-stu-id="1f763-132">However, if the property or indexer uses explicit implementation, the accessors must match.</span></span> <span data-ttu-id="1f763-133">Para obter mais informações sobre a implementação explícita, consulte [Implementação de interface explícita](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) e [Propriedades da interface](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1f763-133">For more information about explicit implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md) and [Interface Properties](../../../csharp/programming-guide/classes-and-structs/interface-properties.md).</span></span>  
  
 <span data-ttu-id="1f763-134">As interfaces podem implementar outras interfaces.</span><span class="sxs-lookup"><span data-stu-id="1f763-134">Interfaces can implement other interfaces.</span></span> <span data-ttu-id="1f763-135">Uma classe pode incluir uma interface várias vezes por meio das classes base que ela herda ou por meio de interfaces que outras interfaces implementam.</span><span class="sxs-lookup"><span data-stu-id="1f763-135">A class might include an interface multiple times through base classes that it inherits or through interfaces that other interfaces implement.</span></span> <span data-ttu-id="1f763-136">No entanto, a classe poderá fornecer uma implementação de uma interface apenas uma vez e somente se a classe declarar a interface como parte da definição de classe (`class ClassName : InterfaceName`).</span><span class="sxs-lookup"><span data-stu-id="1f763-136">However, the class can provide an implementation of an interface only one time and only if the class declares the interface as part of the definition of the class (`class ClassName : InterfaceName`).</span></span> <span data-ttu-id="1f763-137">Se a interface é herdada porque é herdada de uma classe base que implementa a interface, a classe base fornece a implementação dos membros da interface.</span><span class="sxs-lookup"><span data-stu-id="1f763-137">If the interface is inherited because you inherited a base class that implements the interface, the base class provides the implementation of the members of the interface.</span></span> <span data-ttu-id="1f763-138">No entanto, a classe derivada pode reimplementar os membros de interface em vez de usar a implementação herdada.</span><span class="sxs-lookup"><span data-stu-id="1f763-138">However, the derived class can reimplement the interface members instead of using the inherited implementation.</span></span>  
  
 <span data-ttu-id="1f763-139">Uma classe base também pode implementar membros de interface usando membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="1f763-139">A base class can also implement interface members by using virtual members.</span></span> <span data-ttu-id="1f763-140">Nesse caso, uma classe derivada pode alterar o comportamento da interface substituindo os membros virtuais.</span><span class="sxs-lookup"><span data-stu-id="1f763-140">In that case, a derived class can change the interface behavior by overriding the virtual members.</span></span> <span data-ttu-id="1f763-141">Para obter mais informações sobre membros virtuais, consulte [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="1f763-141">For more information about virtual members, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="interfaces-summary"></a><span data-ttu-id="1f763-142">Resumo de Interfaces</span><span class="sxs-lookup"><span data-stu-id="1f763-142">Interfaces Summary</span></span>  
 <span data-ttu-id="1f763-143">Uma interface tem as propriedades a seguir:</span><span class="sxs-lookup"><span data-stu-id="1f763-143">An interface has the following properties:</span></span>  
  
-   <span data-ttu-id="1f763-144">Uma interface é como uma classe base abstrata.</span><span class="sxs-lookup"><span data-stu-id="1f763-144">An interface is like an abstract base class.</span></span> <span data-ttu-id="1f763-145">Qualquer classe ou struct que implementa a interface deve implementar todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="1f763-145">Any class or struct that implements the interface must implement all its members.</span></span>  
  
-   <span data-ttu-id="1f763-146">Uma interface não pode ser instanciada diretamente.</span><span class="sxs-lookup"><span data-stu-id="1f763-146">An interface can't be instantiated directly.</span></span> <span data-ttu-id="1f763-147">Seus membros são implementados por qualquer classe ou struct que implemente a interface.</span><span class="sxs-lookup"><span data-stu-id="1f763-147">Its members are implemented by any class or struct that implements the interface.</span></span>  
  
-   <span data-ttu-id="1f763-148">As interfaces podem conter propriedades, indexadores, métodos e eventos.</span><span class="sxs-lookup"><span data-stu-id="1f763-148">Interfaces can contain events, indexers, methods, and properties.</span></span>  
  
-   <span data-ttu-id="1f763-149">As interfaces não têm implementações de métodos.</span><span class="sxs-lookup"><span data-stu-id="1f763-149">Interfaces contain no implementation of methods.</span></span>  
  
-   <span data-ttu-id="1f763-150">Uma classe ou struct pode implementar várias interfaces.</span><span class="sxs-lookup"><span data-stu-id="1f763-150">A class or struct can implement multiple interfaces.</span></span> <span data-ttu-id="1f763-151">Uma classe pode herdar uma classe base e também implementar uma ou mais interfaces.</span><span class="sxs-lookup"><span data-stu-id="1f763-151">A class can inherit a base class and also implement one or more interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1f763-152">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1f763-152">In This Section</span></span>  
 [<span data-ttu-id="1f763-153">Implementação de interface explícita</span><span class="sxs-lookup"><span data-stu-id="1f763-153">Explicit Interface Implementation</span></span>](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 <span data-ttu-id="1f763-154">Explica como criar um membro da classe que é específico para uma interface.</span><span class="sxs-lookup"><span data-stu-id="1f763-154">Explains how to create a class member that’s specific to an interface.</span></span>  
  
 [<span data-ttu-id="1f763-155">Como implementar membros de interface explicitamente</span><span class="sxs-lookup"><span data-stu-id="1f763-155">How to: Explicitly Implement Interface Members</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 <span data-ttu-id="1f763-156">Fornece um exemplo de como implementar explicitamente membros de interfaces.</span><span class="sxs-lookup"><span data-stu-id="1f763-156">Provides an example of how to explicitly implement members of interfaces.</span></span>  
  
 [<span data-ttu-id="1f763-157">Como implementar membros de duas interfaces explicitamente</span><span class="sxs-lookup"><span data-stu-id="1f763-157">How to: Explicitly Implement Members of Two Interfaces</span></span>](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 <span data-ttu-id="1f763-158">Fornece um exemplo de como implementar explicitamente membros de interfaces com herança.</span><span class="sxs-lookup"><span data-stu-id="1f763-158">Provides an example of how to explicitly implement members of interfaces with inheritance.</span></span>  
  
##  <span data-ttu-id="1f763-159"><a name="BKMK_RelatedSections"></a> Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="1f763-159"><a name="BKMK_RelatedSections"></a> Related Sections</span></span>  
  
-   [<span data-ttu-id="1f763-160">Propriedades de interface</span><span class="sxs-lookup"><span data-stu-id="1f763-160">Interface Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [<span data-ttu-id="1f763-161">Indexadores em interfaces</span><span class="sxs-lookup"><span data-stu-id="1f763-161">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="1f763-162">Como implementar eventos de interface</span><span class="sxs-lookup"><span data-stu-id="1f763-162">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="1f763-163">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="1f763-163">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [<span data-ttu-id="1f763-164">Herança</span><span class="sxs-lookup"><span data-stu-id="1f763-164">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [<span data-ttu-id="1f763-165">Métodos</span><span class="sxs-lookup"><span data-stu-id="1f763-165">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="1f763-166">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="1f763-166">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [<span data-ttu-id="1f763-167">Classes e membros de classes abstract e sealed</span><span class="sxs-lookup"><span data-stu-id="1f763-167">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [<span data-ttu-id="1f763-168">Propriedades</span><span class="sxs-lookup"><span data-stu-id="1f763-168">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [<span data-ttu-id="1f763-169">Eventos</span><span class="sxs-lookup"><span data-stu-id="1f763-169">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
  
-   [<span data-ttu-id="1f763-170">Indexadores</span><span class="sxs-lookup"><span data-stu-id="1f763-170">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="1f763-171">Capítulo do Livro em Destaque</span><span class="sxs-lookup"><span data-stu-id="1f763-171">Featured Book Chapter</span></span>  
 <span data-ttu-id="1f763-172">[Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) em [Learning C# 3.0: Master the Fundamentals of C# 3.0 (Aprendendo C# 3.0: dominando os conceitos básicos do C# 3.0)](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="1f763-172">[Interfaces](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx) in [Learning C# 3.0: Master the Fundamentals of C# 3.0](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f763-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1f763-173">See Also</span></span>  
 <span data-ttu-id="1f763-174">[Guia de programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1f763-174">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="1f763-175">Herança</span><span class="sxs-lookup"><span data-stu-id="1f763-175">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

