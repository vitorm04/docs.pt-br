---
title: Como escrever um construtor de cópias - C# Guia de Programação
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: aa6feb1b07f491a90a78684e254910d387b9bccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714847"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="e1a58-102">Como escrever um construtor de cópias (C# Guia de Programação)</span><span class="sxs-lookup"><span data-stu-id="e1a58-102">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="e1a58-103">O C# não fornece um construtor de cópia para objetos, mas é possível escrever um por conta própria.</span><span class="sxs-lookup"><span data-stu-id="e1a58-103">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1a58-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1a58-104">Example</span></span>  
 <span data-ttu-id="e1a58-105">No exemplo a seguir, a `Person`[class](../../language-reference/keywords/class.md) define um construtor de cópia que usa, como seu argumento, uma instância de `Person`.</span><span class="sxs-lookup"><span data-stu-id="e1a58-105">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="e1a58-106">Os valores das propriedades do argumento são atribuídos às propriedades da nova instância de `Person`.</span><span class="sxs-lookup"><span data-stu-id="e1a58-106">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="e1a58-107">O código contém um construtor de cópia alternativa que envia as propriedades `Name` e `Age` da instância que você deseja copiar para o construtor de instância da classe.</span><span class="sxs-lookup"><span data-stu-id="e1a58-107">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="e1a58-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1a58-108">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="e1a58-109">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="e1a58-109">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e1a58-110">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="e1a58-110">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e1a58-111">Construtores</span><span class="sxs-lookup"><span data-stu-id="e1a58-111">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e1a58-112">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="e1a58-112">Finalizers</span></span>](./destructors.md)
