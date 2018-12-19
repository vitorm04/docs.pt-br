---
title: 'Como: escrever um construtor de cópia – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: daf0683060d7df5dc5e644b4b84aac3dcdea939f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240678"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="3ab70-102">Como: escrever um construtor de cópia (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3ab70-102">How to: Write a Copy Constructor (C# Programming Guide)</span></span>
<span data-ttu-id="3ab70-103">O C# não fornece um construtor de cópia para objetos, mas é possível escrever um por conta própria.</span><span class="sxs-lookup"><span data-stu-id="3ab70-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ab70-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3ab70-104">Example</span></span>  
 <span data-ttu-id="3ab70-105">No exemplo a seguir, a `Person`[class](../../../csharp/language-reference/keywords/class.md) define um construtor de cópia que usa, como seu argumento, uma instância de `Person`.</span><span class="sxs-lookup"><span data-stu-id="3ab70-105">In the following example, the `Person`[class](../../../csharp/language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="3ab70-106">Os valores das propriedades do argumento são atribuídos às propriedades da nova instância de `Person`.</span><span class="sxs-lookup"><span data-stu-id="3ab70-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="3ab70-107">O código contém um construtor de cópia alternativa que envia as propriedades `Name` e `Age` da instância que você deseja copiar para o construtor de instância da classe.</span><span class="sxs-lookup"><span data-stu-id="3ab70-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-write-a-copy-constructor_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3ab70-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ab70-108">See Also</span></span>

- <xref:System.ICloneable>  
- [<span data-ttu-id="3ab70-109">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3ab70-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3ab70-110">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="3ab70-110">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="3ab70-111">Construtores</span><span class="sxs-lookup"><span data-stu-id="3ab70-111">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="3ab70-112">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="3ab70-112">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
