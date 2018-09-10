---
title: struct (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 7931da2e5f5c493b54eb1f33a1d6f57b38592f6e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530186"
---
# <a name="struct-c-reference"></a><span data-ttu-id="a5eab-102">struct (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a5eab-102">struct (C# Reference)</span></span>
<span data-ttu-id="a5eab-103">O tipo `struct` é um tipo de valor normalmente usado para encapsular pequenos grupos de variáveis relacionadas, tais como coordenadas de um retângulo ou as características de um item em um inventário.</span><span class="sxs-lookup"><span data-stu-id="a5eab-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="a5eab-104">O seguinte exemplo mostra uma declaração simples de struct:</span><span class="sxs-lookup"><span data-stu-id="a5eab-104">The following example shows a simple struct declaration:</span></span>  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="a5eab-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="a5eab-105">Remarks</span></span>  
 <span data-ttu-id="a5eab-106">Os structs também podem conter [construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constantes](../../../csharp/programming-guide/classes-and-structs/constants.md), [campos](../../../csharp/programming-guide/classes-and-structs/fields.md), [métodos](../../../csharp/programming-guide/classes-and-structs/methods.md), [propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexadores](../../../csharp/programming-guide/indexers/index.md), [operadores](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [eventos](../../../csharp/programming-guide/events/index.md) e [tipos aninhados](../../../csharp/programming-guide/classes-and-structs/nested-types.md), embora, se vários desses membros forem necessários, você deva considerar tonar seu tipo uma classe.</span><span class="sxs-lookup"><span data-stu-id="a5eab-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="a5eab-107">Para obter exemplos, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="a5eab-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="a5eab-108">Os structs podem implantar uma interface, mas não podem herdá-la de outra struct.</span><span class="sxs-lookup"><span data-stu-id="a5eab-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="a5eab-109">Por esse motivo, os membros de struct não podem ser declarados como `protected`.</span><span class="sxs-lookup"><span data-stu-id="a5eab-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="a5eab-110">Para obter mais informações, consulte [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="a5eab-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a5eab-111">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a5eab-111">Examples</span></span>  
 <span data-ttu-id="a5eab-112">Para obter exemplos e mais informações, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="a5eab-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a5eab-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="a5eab-113">C# Language Specification</span></span>  
 <span data-ttu-id="a5eab-114">Para obter exemplos, consulte [Usando structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="a5eab-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5eab-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5eab-115">See Also</span></span>

- [<span data-ttu-id="a5eab-116">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a5eab-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a5eab-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a5eab-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a5eab-118">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="a5eab-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a5eab-119">Tabela de valores padrão</span><span class="sxs-lookup"><span data-stu-id="a5eab-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
- [<span data-ttu-id="a5eab-120">Tabela de tipos internos</span><span class="sxs-lookup"><span data-stu-id="a5eab-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="a5eab-121">Tipos</span><span class="sxs-lookup"><span data-stu-id="a5eab-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="a5eab-122">Tipos de valor</span><span class="sxs-lookup"><span data-stu-id="a5eab-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
- [<span data-ttu-id="a5eab-123">class</span><span class="sxs-lookup"><span data-stu-id="a5eab-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
- [<span data-ttu-id="a5eab-124">interface</span><span class="sxs-lookup"><span data-stu-id="a5eab-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
- [<span data-ttu-id="a5eab-125">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="a5eab-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
