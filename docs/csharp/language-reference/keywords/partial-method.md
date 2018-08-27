---
title: partial (método) (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 69e16dd8b0fe0055124aca90fea65a36d9e413f3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933679"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="95085-102">partial (método) (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="95085-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="95085-103">Um método parcial tem sua assinatura definida em uma parte de um tipo parcial e sua implementação definida em outra parte do tipo.</span><span class="sxs-lookup"><span data-stu-id="95085-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="95085-104">Os métodos parciais permitem que os designers de classe forneçam ganchos de método, semelhantes a manipuladores de eventos, que os desenvolvedores podem decidir implementar ou não.</span><span class="sxs-lookup"><span data-stu-id="95085-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="95085-105">Se o desenvolvedor não fornecer uma implementação, o compilador removerá a assinatura no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="95085-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="95085-106">As seguintes condições são aplicáveis a métodos parciais:</span><span class="sxs-lookup"><span data-stu-id="95085-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="95085-107">As assinaturas em ambas as partes do tipo parcial devem ser correspondentes.</span><span class="sxs-lookup"><span data-stu-id="95085-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="95085-108">O método deve retornar nulo.</span><span class="sxs-lookup"><span data-stu-id="95085-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="95085-109">Não é permitido nenhum modificador de acesso.</span><span class="sxs-lookup"><span data-stu-id="95085-109">No access modifiers are allowed.</span></span> <span data-ttu-id="95085-110">Métodos parciais são implicitamente privados.</span><span class="sxs-lookup"><span data-stu-id="95085-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="95085-111">O exemplo a seguir mostra um método parcial definido em duas partes de uma classe parcial:</span><span class="sxs-lookup"><span data-stu-id="95085-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="95085-112">Para obter mais informações, consulte [Classes e métodos parciais](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="95085-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95085-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95085-113">See Also</span></span>

- [<span data-ttu-id="95085-114">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="95085-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="95085-115">(partial (tipo)</span><span class="sxs-lookup"><span data-stu-id="95085-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
