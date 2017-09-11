---
title: "Introdução aos genéricos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: 32
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
ms.openlocfilehash: d4fddd29135bfc15acedb8b89d577dc99a21e18a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="5cdbf-102">Introdução aos genéricos (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="5cdbf-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="5cdbf-103">As classes e métodos genéricos combinam a capacidade de reutilização, a segurança de tipos e a eficiência de uma maneira que suas contrapartes não genéricas não conseguem.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="5cdbf-104">Os genéricos são usados com mais frequência com coleções e com os métodos que operam nelas.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="5cdbf-105">A versão 2.0 da biblioteca de classes do .NET Framework fornece um novo namespace, <xref:System.Collections.Generic>, que contém várias classes de coleção novas com base em genéricos.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="5cdbf-106">É recomendável que todos os aplicativos que se destinam ao [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 e posterior usem as novas classes de coleção genéricas em vez das contrapartes não genéricas mais antigas, como a <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-106">It is recommended that all applications that target the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="5cdbf-107">Para obter mais informações, consulte [Genéricos na biblioteca de Classes .NET Framework](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span><span class="sxs-lookup"><span data-stu-id="5cdbf-107">For more information, see [Generics in the .NET Framework Class Library](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).</span></span>  
  
 <span data-ttu-id="5cdbf-108">É claro que você também pode criar tipos e métodos genéricos personalizados para fornecer suas próprias soluções e padrões de design generalizados que sejam fortemente tipados e eficientes.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="5cdbf-109">O exemplo de código a seguir mostra uma classe de lista vinculada genérica simples para fins de demonstração.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="5cdbf-110">(Na maioria dos casos, você deve usar a classe <xref:System.Collections.Generic.List%601>, fornecida pela biblioteca de classes .NET Framework, em vez de criar a sua própria classe). O parâmetro de tipo `T` é usado em vários locais em que um tipo concreto normalmente seria usado para indicar o tipo do item armazenado na lista.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="5cdbf-111">Ele é usado das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="5cdbf-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="5cdbf-112">Como o tipo de um parâmetro de método no método `AddHead`.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="5cdbf-113">Como o tipo de retorno do método público `GetNext` e a propriedade `Data` na classe `Node` aninhada.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-113">As the return type of the public method `GetNext` and the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="5cdbf-114">Como o tipo de dados do membro particular na classe aninhada.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-114">As the type of the private member data in the nested class.</span></span>  
  
 <span data-ttu-id="5cdbf-115">Observe que T está disponível para a classe `Node` aninhada.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="5cdbf-116">Quando `GenericList<T>` é instanciada com um tipo concreto, por exemplo como um `GenericList<int>`, cada ocorrência de `T` será substituída por `int`.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 <span data-ttu-id="5cdbf-117">[!code-cs[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5cdbf-117">[!code-cs[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]</span></span>  
  
 <span data-ttu-id="5cdbf-118">O exemplo de código a seguir mostra como o código cliente usa a classe `GenericList<T>` genérica para criar uma lista de inteiros.</span><span class="sxs-lookup"><span data-stu-id="5cdbf-118">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="5cdbf-119">Ao simplesmente alterar o argumento de tipo, o código a seguir poderia facilmente ser modificado para criar listas de cadeias de caracteres ou qualquer outro tipo personalizado:</span><span class="sxs-lookup"><span data-stu-id="5cdbf-119">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 <span data-ttu-id="5cdbf-120">[!code-cs[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5cdbf-120">[!code-cs[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cdbf-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cdbf-121">See Also</span></span>  
 <span data-ttu-id="5cdbf-122"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="5cdbf-122"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="5cdbf-123">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5cdbf-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="5cdbf-124">Genéricos</span><span class="sxs-lookup"><span data-stu-id="5cdbf-124">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

