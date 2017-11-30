---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 06770f05aabedcf13cc9af1970a2c511a30c73b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="0949a-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0949a-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="0949a-103">Especifica que um parâmetro de procedimento leva uma matriz opcional de elementos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="0949a-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="0949a-104">`ParamArray`pode ser usado apenas no último parâmetro de uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="0949a-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0949a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="0949a-105">Remarks</span></span>  
 <span data-ttu-id="0949a-106">`ParamArray`permite que você passe um número arbitrário de argumentos para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="0949a-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="0949a-107">Um `ParamArray` parâmetro sempre é declarado usando [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="0949a-107">A `ParamArray` parameter is always declared using [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
 <span data-ttu-id="0949a-108">Você pode fornecer um ou mais argumentos para um `ParamArray` parâmetro passando uma matriz dos dados apropriados tipo, uma lista separada por vírgulas de valores ou nada em todos os.</span><span class="sxs-lookup"><span data-stu-id="0949a-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="0949a-109">Para obter detalhes, consulte "Chamada de ParamArray" [matrizes de parâmetro](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="0949a-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0949a-110">Sempre que você lidar com uma matriz que pode ser indefinidamente grande, há um risco de ultrapassar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0949a-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="0949a-111">Se você aceitar uma matriz de parâmetros de código de chamada, você deve testar seu tamanho e execute as etapas apropriadas se ele é muito grande para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0949a-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="0949a-112">O `ParamArray` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="0949a-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="0949a-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="0949a-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="0949a-114">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="0949a-114">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="0949a-115">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="0949a-115">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="0949a-116">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="0949a-116">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0949a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0949a-117">See Also</span></span>  
 [<span data-ttu-id="0949a-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0949a-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="0949a-119">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0949a-119">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
