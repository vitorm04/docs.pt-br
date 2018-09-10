---
title: Propriedades de interface (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: eea2bb524496a3db22146586df323437d9f84242
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396725"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="6fc01-102">Propriedades de interface (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6fc01-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="6fc01-103">As propriedades podem ser declaradas em uma [interface](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="6fc01-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="6fc01-104">Este é um exemplo de um acessador de propriedade de interface:</span><span class="sxs-lookup"><span data-stu-id="6fc01-104">The following is an example of an interface property accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]  
  
 <span data-ttu-id="6fc01-105">O acessador de uma propriedade de interface não tem um corpo.</span><span class="sxs-lookup"><span data-stu-id="6fc01-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="6fc01-106">Portanto, a finalidade dos acessadores é indicar se a propriedade é leitura/gravação, somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="6fc01-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc01-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fc01-107">Example</span></span>  
 <span data-ttu-id="6fc01-108">Neste exemplo, a interface `IEmployee` tem uma propriedade de leitura/gravação, `Name` e uma propriedade somente leitura, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="6fc01-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="6fc01-109">A classe `Employee` implementa a interface `IEmployee` e usa essas duas propriedades.</span><span class="sxs-lookup"><span data-stu-id="6fc01-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="6fc01-110">O programa lê o nome de um novo funcionário e o número atual de funcionários e exibe o nome do funcionário e o número do funcionário computado.</span><span class="sxs-lookup"><span data-stu-id="6fc01-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="6fc01-111">Seria possível usar o nome totalmente qualificado da propriedade, que referencia a interface na qual o membro é declarado.</span><span class="sxs-lookup"><span data-stu-id="6fc01-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="6fc01-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6fc01-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="6fc01-113">Isso é denominado [Implementação explícita da interface](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="6fc01-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="6fc01-114">Por exemplo, se a classe `Employee` estiver implementando duas interfaces `ICitizen` e `IEmployee` e as duas interfaces tiverem a propriedade `Name`, será necessária a implementação explícita de membro da interface.</span><span class="sxs-lookup"><span data-stu-id="6fc01-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="6fc01-115">Ou seja, a seguinte declaração de propriedade:</span><span class="sxs-lookup"><span data-stu-id="6fc01-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]  
  
 <span data-ttu-id="6fc01-116">implementa a propriedade `Name` na interface `IEmployee`, enquanto a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="6fc01-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]  
  
 <span data-ttu-id="6fc01-117">implementa a propriedade `Name` na interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="6fc01-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="6fc01-118">Saída de Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fc01-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="6fc01-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fc01-119">See Also</span></span>  
 [<span data-ttu-id="6fc01-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6fc01-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6fc01-121">Propriedades</span><span class="sxs-lookup"><span data-stu-id="6fc01-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="6fc01-122">Usando propriedades</span><span class="sxs-lookup"><span data-stu-id="6fc01-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="6fc01-123">Comparação entre propriedades e indexadores</span><span class="sxs-lookup"><span data-stu-id="6fc01-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
 [<span data-ttu-id="6fc01-124">Indexadores</span><span class="sxs-lookup"><span data-stu-id="6fc01-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="6fc01-125">Interfaces</span><span class="sxs-lookup"><span data-stu-id="6fc01-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
