---
title: Como escrever um construtor de cópia – guia de programação C#
description: Saiba como escrever um construtor de cópia em C# que usa uma instância da classe e retorna uma nova instância com os valores da entrada.
ms.date: 07/20/2015
helpviewer_keywords:
- C# Language, copy constructor
- copy constructor [C#]
ms.assetid: fba899b5-fc41-428e-a745-3ebdbf37990a
ms.openlocfilehash: beb2fcfaa36303eeaabd5278cf5e7a128282270e
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864222"
---
# <a name="how-to-write-a-copy-constructor-c-programming-guide"></a><span data-ttu-id="b5f02-103">Como escrever um construtor de cópia (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="b5f02-103">How to write a copy constructor (C# Programming Guide)</span></span>
<span data-ttu-id="b5f02-104">O C# não fornece um construtor de cópia para objetos, mas é possível escrever um por conta própria.</span><span class="sxs-lookup"><span data-stu-id="b5f02-104">C# doesn't provide a copy constructor for objects, but you can write one yourself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5f02-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5f02-105">Example</span></span>  
 <span data-ttu-id="b5f02-106">No exemplo a seguir, a `Person`[class](../../language-reference/keywords/class.md) define um construtor de cópia que usa, como seu argumento, uma instância de `Person`.</span><span class="sxs-lookup"><span data-stu-id="b5f02-106">In the following example, the `Person`[class](../../language-reference/keywords/class.md) defines a copy constructor that takes, as its argument, an instance of `Person`.</span></span> <span data-ttu-id="b5f02-107">Os valores das propriedades do argumento são atribuídos às propriedades da nova instância de `Person`.</span><span class="sxs-lookup"><span data-stu-id="b5f02-107">The values of the properties of the argument are assigned to the properties of the new instance of `Person`.</span></span> <span data-ttu-id="b5f02-108">O código contém um construtor de cópia alternativa que envia as propriedades `Name` e `Age` da instância que você deseja copiar para o construtor de instância da classe.</span><span class="sxs-lookup"><span data-stu-id="b5f02-108">The code contains an alternative copy constructor that sends the `Name` and `Age` properties of the instance that you want to copy to the instance constructor of the class.</span></span>  
  
 [!code-csharp[csProgGuideObjects#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#16)]  
  
## <a name="see-also"></a><span data-ttu-id="b5f02-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="b5f02-109">See also</span></span>

- <xref:System.ICloneable>
- [<span data-ttu-id="b5f02-110">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b5f02-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b5f02-111">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="b5f02-111">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b5f02-112">Construtores</span><span class="sxs-lookup"><span data-stu-id="b5f02-112">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b5f02-113">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="b5f02-113">Finalizers</span></span>](./destructors.md)
