---
title: "partial (método) (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialmethod_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
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
ms.openlocfilehash: b6f8ecca01ebf681c906b73abefc94e9e45b8700
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="partial-method-c-reference"></a><span data-ttu-id="b82aa-102">partial (método) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b82aa-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="b82aa-103">Um método parcial tem sua assinatura definida em uma parte de um tipo parcial e sua implementação definida em outra parte do tipo.</span><span class="sxs-lookup"><span data-stu-id="b82aa-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="b82aa-104">Os métodos parciais permitem que os designers de classe forneçam ganchos de método, semelhantes a manipuladores de eventos, que os desenvolvedores podem decidir implementar ou não.</span><span class="sxs-lookup"><span data-stu-id="b82aa-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="b82aa-105">Se o desenvolvedor não fornecer uma implementação, o compilador removerá a assinatura no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b82aa-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="b82aa-106">As seguintes condições são aplicáveis a métodos parciais:</span><span class="sxs-lookup"><span data-stu-id="b82aa-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="b82aa-107">As assinaturas em ambas as partes do tipo parcial devem ser correspondentes.</span><span class="sxs-lookup"><span data-stu-id="b82aa-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="b82aa-108">O método deve retornar nulo.</span><span class="sxs-lookup"><span data-stu-id="b82aa-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="b82aa-109">Não é permitido nenhum modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="b82aa-109">No access modifiers are allowed.</span></span> <span data-ttu-id="b82aa-110">Métodos parciais são implicitamente privados.</span><span class="sxs-lookup"><span data-stu-id="b82aa-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="b82aa-111">O exemplo a seguir mostra um método parcial definido em duas partes de uma classe parcial:</span><span class="sxs-lookup"><span data-stu-id="b82aa-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 <span data-ttu-id="b82aa-112">[!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b82aa-112">[!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]</span></span>  
  
 <span data-ttu-id="b82aa-113">Para obter mais informações, consulte [Classes e métodos parciais](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b82aa-113">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82aa-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b82aa-114">See Also</span></span>  
 <span data-ttu-id="b82aa-115">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b82aa-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="b82aa-116">(partial (tipo)</span><span class="sxs-lookup"><span data-stu-id="b82aa-116">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)

