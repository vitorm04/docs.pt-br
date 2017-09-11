---
title: ParamArray (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
dev_langs:
- VB
helpviewer_keywords:
- ParamArray keyword
- ParamArray keyword, syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a4fcb538f5fc91ea82c70d5bb879b17072fc2dbb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="63029-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63029-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="63029-103">Especifica que um parâmetro de procedimento leva uma matriz opcional de elementos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="63029-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="63029-104">`ParamArray`pode ser usado apenas no último parâmetro de uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="63029-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63029-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="63029-105">Remarks</span></span>  
 <span data-ttu-id="63029-106">`ParamArray`permite que você passe um número arbitrário de argumentos para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="63029-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="63029-107">A `ParamArray` parâmetro sempre é declarado usando [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="63029-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="63029-108">Você pode fornecer um ou mais argumentos para um `ParamArray` , passando uma matriz de dados apropriados tipo de parâmetro, uma lista separada por vírgulas de valores ou nada todo.</span><span class="sxs-lookup"><span data-stu-id="63029-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="63029-109">Para obter detalhes, consulte "Chamada de ParamArray" [matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="63029-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63029-110">Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63029-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="63029-111">Se você aceitar uma matriz de parâmetros do código de chamada, você deve testar seu tamanho e tomar as medidas adequadas se ele for muito grande para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63029-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="63029-112">O `ParamArray` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="63029-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="63029-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="63029-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="63029-114">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="63029-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="63029-115">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="63029-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="63029-116">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="63029-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="63029-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63029-117">See Also</span></span>  
 <span data-ttu-id="63029-118">[Palavras-chave](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="63029-118">[Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="63029-119"> [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)</span><span class="sxs-lookup"><span data-stu-id="63029-119"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)</span></span>
