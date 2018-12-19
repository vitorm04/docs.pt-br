---
title: Indexadores em interfaces – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ff636691ea2f4dacd13fbd2a336f0023ed65750b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235651"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="0b704-102">Indexadores em interfaces (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="0b704-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="0b704-103">Os indexadores podem ser declarados em uma [interface](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="0b704-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="0b704-104">Acessadores de indexadores de interface diferem dos acessadores de indexadores de [classe](../../../csharp/language-reference/keywords/class.md) das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="0b704-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="0b704-105">Os acessadores de interface não usam modificadores.</span><span class="sxs-lookup"><span data-stu-id="0b704-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="0b704-106">Um acessador de interface não tem um corpo.</span><span class="sxs-lookup"><span data-stu-id="0b704-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="0b704-107">Portanto, a finalidade do acessador é indicar se o indexador é leitura/gravação, somente leitura ou somente gravação.</span><span class="sxs-lookup"><span data-stu-id="0b704-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="0b704-108">Este é um exemplo de um acessador de indexador de interface:</span><span class="sxs-lookup"><span data-stu-id="0b704-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="0b704-109">A assinatura de um indexador deve ser diferente das assinaturas de todos os outros indexadores declarados na mesma interface.</span><span class="sxs-lookup"><span data-stu-id="0b704-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b704-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0b704-110">Example</span></span>  
 <span data-ttu-id="0b704-111">O exemplo a seguir mostra como implementar indexadores de interface.</span><span class="sxs-lookup"><span data-stu-id="0b704-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="0b704-112">No exemplo anterior, é possível usar a implementação de membro de interface explícita usando o nome totalmente qualificado do membro de interface.</span><span class="sxs-lookup"><span data-stu-id="0b704-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="0b704-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="0b704-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="0b704-114">No entanto, o nome totalmente qualificado só será necessário para evitar ambiguidade quando a classe estiver implementando mais de uma interface com a mesma assinatura do indexador.</span><span class="sxs-lookup"><span data-stu-id="0b704-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="0b704-115">Por exemplo, se uma classe `Employee` estiver implementando dois interfaces, `ICitizen` e `IEmployee`, e as duas interfaces tiverem a mesma assinatura de indexador, a implementação de membro de interface explícita é necessária.</span><span class="sxs-lookup"><span data-stu-id="0b704-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="0b704-116">Ou seja, a seguinte declaração de indexador:</span><span class="sxs-lookup"><span data-stu-id="0b704-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="0b704-117">implementa o indexador na interface `IEmployee`, enquanto a seguinte declaração:</span><span class="sxs-lookup"><span data-stu-id="0b704-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="0b704-118">implementa o indexador na interface `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="0b704-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b704-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b704-119">See Also</span></span>

- [<span data-ttu-id="0b704-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0b704-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0b704-121">Indexadores</span><span class="sxs-lookup"><span data-stu-id="0b704-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="0b704-122">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0b704-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="0b704-123">Interfaces</span><span class="sxs-lookup"><span data-stu-id="0b704-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
