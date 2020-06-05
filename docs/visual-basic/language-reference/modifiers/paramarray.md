---
title: ParamArray
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: e3c24818ea87884a0dd9b42c604e13e16ca6d3d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84391814"
---
# <a name="paramarray-visual-basic"></a><span data-ttu-id="aa45d-102">ParamArray (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa45d-102">ParamArray (Visual Basic)</span></span>
<span data-ttu-id="aa45d-103">Especifica que um parâmetro de procedimento usa uma matriz opcional de elementos do tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="aa45d-103">Specifies that a procedure parameter takes an optional array of elements of the specified type.</span></span> <span data-ttu-id="aa45d-104">`ParamArray`pode ser usado somente no último parâmetro de uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="aa45d-104">`ParamArray` can be used only on the last parameter of a parameter list.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa45d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa45d-105">Remarks</span></span>  
 <span data-ttu-id="aa45d-106">`ParamArray`permite que você passe um número arbitrário de argumentos para o procedimento.</span><span class="sxs-lookup"><span data-stu-id="aa45d-106">`ParamArray` allows you to pass an arbitrary number of arguments to the procedure.</span></span> <span data-ttu-id="aa45d-107">Um `ParamArray` parâmetro é sempre declarado usando [ByVal](byval.md).</span><span class="sxs-lookup"><span data-stu-id="aa45d-107">A `ParamArray` parameter is always declared using [ByVal](byval.md).</span></span>  
  
 <span data-ttu-id="aa45d-108">Você pode fornecer um ou mais argumentos a um `ParamArray` parâmetro passando uma matriz do tipo de dados apropriado, uma lista de valores separados por vírgula ou nada.</span><span class="sxs-lookup"><span data-stu-id="aa45d-108">You can supply one or more arguments to a `ParamArray` parameter by passing an array of the appropriate data type, a comma-separated list of values, or nothing at all.</span></span> <span data-ttu-id="aa45d-109">Para obter detalhes, consulte "chamando um ParamArray" em [matrizes de parâmetros](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="aa45d-109">For details, see "Calling a ParamArray" in [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aa45d-110">Sempre que você lida com uma matriz que pode ser indefinidamente grande, há um risco de sobreexecutar alguma capacidade interna de seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa45d-110">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="aa45d-111">Se você aceitar uma matriz de parâmetros do código de chamada, deverá testar seu comprimento e tomar as medidas apropriadas se for muito grande para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="aa45d-111">If you accept a parameter array from the calling code, you should test its length and take appropriate steps if it is too large for your application.</span></span>  
  
 <span data-ttu-id="aa45d-112">O `ParamArray` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="aa45d-112">The `ParamArray` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="aa45d-113">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="aa45d-113">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="aa45d-114">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="aa45d-114">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="aa45d-115">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="aa45d-115">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="aa45d-116">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="aa45d-116">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="aa45d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa45d-117">See also</span></span>

- [<span data-ttu-id="aa45d-118">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="aa45d-118">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="aa45d-119">Matrizes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="aa45d-119">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
