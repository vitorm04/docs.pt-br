---
title: Conversão implícita de &#39; &lt;typename1&gt; &#39; para &#39; &lt;typename2&gt; &#39; na cópia do valor de &#39;ByRef&#39; parâmetro &#39; &lt; nome do parâmetro&gt; &#39; volta para o argumento correspondente.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: b1f772598b18f8edfe0198f62d78854d30f993ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589994"
---
# <a name="implicit-conversion-from-39lttypename1gt39-to-39lttypename2gt39-in-copying-the-value-of-39byref39-parameter-39ltparameternamegt39-back-to-the-matching-argument"></a><span data-ttu-id="b057b-102">Conversão implícita de &#39; &lt;typename1&gt; &#39; para &#39; &lt;typename2&gt; &#39; na cópia do valor de &#39;ByRef&#39; parâmetro &#39; &lt; nome do parâmetro&gt; &#39; volta para o argumento correspondente.</span><span class="sxs-lookup"><span data-stu-id="b057b-102">Implicit conversion from &#39;&lt;typename1&gt;&#39; to &#39;&lt;typename2&gt;&#39; in copying the value of &#39;ByRef&#39; parameter &#39;&lt;parametername&gt;&#39; back to the matching argument.</span></span>
<span data-ttu-id="b057b-103">Um procedimento é chamado com um [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argumento de um tipo diferente do seu parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="b057b-103">A procedure is called with a [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>  
  
 <span data-ttu-id="b057b-104">Se você passar um argumento `ByRef`, Visual Basic, às vezes, copia o valor do argumento para uma variável local no procedimento em vez de passar uma referência.</span><span class="sxs-lookup"><span data-stu-id="b057b-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="b057b-105">Nesse caso, quando o procedimento retorna, Visual Basic deve, em seguida, copie o valor da variável local volta para o argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="b057b-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>  
  
 <span data-ttu-id="b057b-106">Se um `ByRef` o valor do argumento é copiado para o procedimento e o argumento e parâmetro são do mesmo tipo, nenhuma conversão é necessária.</span><span class="sxs-lookup"><span data-stu-id="b057b-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="b057b-107">Mas se os tipos forem diferentes, o Visual Basic deve converter em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="b057b-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="b057b-108">Porque você não pode usar `CType` ou qualquer um dos outros conversão palavras-chave em um argumento de procedimento ou parâmetro, tal conversão sempre está implícito.</span><span class="sxs-lookup"><span data-stu-id="b057b-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>  
  
 <span data-ttu-id="b057b-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="b057b-109">By default, this message is a warning.</span></span> <span data-ttu-id="b057b-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="b057b-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="b057b-111">**ID do erro:** BC41999</span><span class="sxs-lookup"><span data-stu-id="b057b-111">**Error ID:** BC41999</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b057b-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b057b-112">To correct this error</span></span>  
  
-   <span data-ttu-id="b057b-113">Se possível, use um argumento chamando do mesmo tipo que o parâmetro do procedimento, para que o Visual Basic não precisa fazer nenhuma conversão.</span><span class="sxs-lookup"><span data-stu-id="b057b-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>  
  
-   <span data-ttu-id="b057b-114">Se você precisar chamar o procedimento com um argumento de tipo diferente do tipo de parâmetro, mas não precisa retornar um valor para o argumento de chamada, defina o parâmetro para ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) em vez de `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="b057b-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) instead of `ByRef`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b057b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b057b-115">See Also</span></span>  
 [<span data-ttu-id="b057b-116">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="b057b-116">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="b057b-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="b057b-117">Procedure Parameters and Arguments</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b057b-118">Passando Argumentos por Valor e por Referência</span><span class="sxs-lookup"><span data-stu-id="b057b-118">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="b057b-119">Conversões Implícitas e Explícitas</span><span class="sxs-lookup"><span data-stu-id="b057b-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
