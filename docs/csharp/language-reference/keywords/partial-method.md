---
description: Método partial – Referência de C#
title: Método partial – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: d6c433fd30f6ec51355bdefee90d815783487c1b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134374"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="07bfe-103">Método parcial (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="07bfe-103">partial method (C# Reference)</span></span>

<span data-ttu-id="07bfe-104">Um método parcial tem sua assinatura definida em uma parte de um tipo parcial e sua implementação definida em outra parte do tipo.</span><span class="sxs-lookup"><span data-stu-id="07bfe-104">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="07bfe-105">Os métodos parciais permitem que os designers de classe forneçam ganchos de método, semelhantes a manipuladores de eventos, que os desenvolvedores podem decidir implementar ou não.</span><span class="sxs-lookup"><span data-stu-id="07bfe-105">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="07bfe-106">Se o desenvolvedor não fornecer uma implementação, o compilador removerá a assinatura no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="07bfe-106">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="07bfe-107">As seguintes condições são aplicáveis a métodos parciais:</span><span class="sxs-lookup"><span data-stu-id="07bfe-107">The following conditions apply to partial methods:</span></span>

- <span data-ttu-id="07bfe-108">As assinaturas em ambas as partes do tipo parcial devem ser correspondentes.</span><span class="sxs-lookup"><span data-stu-id="07bfe-108">Signatures in both parts of the partial type must match.</span></span>

- <span data-ttu-id="07bfe-109">O método deve retornar nulo.</span><span class="sxs-lookup"><span data-stu-id="07bfe-109">The method must return void.</span></span>

- <span data-ttu-id="07bfe-110">Não é permitido nenhum modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="07bfe-110">No access modifiers are allowed.</span></span> <span data-ttu-id="07bfe-111">Métodos parciais são implicitamente privados.</span><span class="sxs-lookup"><span data-stu-id="07bfe-111">Partial methods are implicitly private.</span></span>

<span data-ttu-id="07bfe-112">O exemplo a seguir mostra um método parcial definido em duas partes de uma classe parcial:</span><span class="sxs-lookup"><span data-stu-id="07bfe-112">The following example shows a partial method defined in two parts of a partial class:</span></span>

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

<span data-ttu-id="07bfe-113">Para obter mais informações, consulte [Classes parciais e métodos](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="07bfe-113">For more information, see [Partial Classes and Methods](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07bfe-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="07bfe-114">See also</span></span>

- [<span data-ttu-id="07bfe-115">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="07bfe-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07bfe-116">tipo parcial</span><span class="sxs-lookup"><span data-stu-id="07bfe-116">partial type</span></span>](partial-type.md)
