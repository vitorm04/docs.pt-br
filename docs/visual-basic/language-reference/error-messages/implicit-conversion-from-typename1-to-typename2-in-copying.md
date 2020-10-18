---
title: Conversão implícita de '<typename1>' em '<typename2>' ao copiar o valor do parâmetro 'ByRef' '<parametername>' para o argumento correspondente.
ms.date: 07/20/2015
f1_keywords:
- vbc41999
- bc41999
helpviewer_keywords:
- BC41999
ms.assetid: ae48c738-dff8-4c0f-8931-bbb70b2c8b03
ms.openlocfilehash: a95a4b792742efcc165f7c7a9592582d34618f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162798"
---
# <a name="bc41999-implicit-conversion-from-typename1-to-typename2-in-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument"></a><span data-ttu-id="84924-102">BC41999: conversão implícita de " \<typename1> " para " \<typename2> " ao copiar o valor do parâmetro "ByRef" " \<parametername> " de volta para o argumento correspondente.</span><span class="sxs-lookup"><span data-stu-id="84924-102">BC41999: Implicit conversion from '\<typename1>' to '\<typename2>' in copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument.</span></span>

<span data-ttu-id="84924-103">Um procedimento é chamado com um argumento [ByRef](../modifiers/byref.md) de um tipo diferente daquele do parâmetro correspondente.</span><span class="sxs-lookup"><span data-stu-id="84924-103">A procedure is called with a [ByRef](../modifiers/byref.md) argument of a different type than that of its corresponding parameter.</span></span>

 <span data-ttu-id="84924-104">Se você passar um argumento `ByRef` , o Visual Basic às vezes copiará o valor do argumento em uma variável local no procedimento em vez de passar uma referência.</span><span class="sxs-lookup"><span data-stu-id="84924-104">If you pass an argument `ByRef`, Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="84924-105">Nesse caso, quando o procedimento retorna, Visual Basic deve copiar o valor da variável local de volta para o argumento no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="84924-105">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>

 <span data-ttu-id="84924-106">Se um `ByRef` valor de argumento for copiado para o procedimento e o argumento e o parâmetro forem do mesmo tipo, nenhuma conversão será necessária.</span><span class="sxs-lookup"><span data-stu-id="84924-106">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="84924-107">Mas se os tipos forem diferentes, Visual Basic deverá converter em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="84924-107">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="84924-108">Como você não pode usar `CType` ou qualquer uma das outras palavras-chave de conversão em um argumento ou parâmetro de procedimento, tal conversão é sempre implícita.</span><span class="sxs-lookup"><span data-stu-id="84924-108">Because you cannot use `CType` or any of the other conversion keywords on a procedure argument or parameter, such a conversion is always implicit.</span></span>

 <span data-ttu-id="84924-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="84924-109">By default, this message is a warning.</span></span> <span data-ttu-id="84924-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="84924-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="84924-111">**ID do erro:** BC41999</span><span class="sxs-lookup"><span data-stu-id="84924-111">**Error ID:** BC41999</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="84924-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="84924-112">To correct this error</span></span>

- <span data-ttu-id="84924-113">Se possível, use um argumento de chamada do mesmo tipo que o parâmetro de procedimento, portanto Visual Basic não precisa fazer nenhuma conversão.</span><span class="sxs-lookup"><span data-stu-id="84924-113">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>

- <span data-ttu-id="84924-114">Se você precisar chamar o procedimento com um tipo de argumento diferente do tipo de parâmetro, mas não precisar retornar um valor para o argumento de chamada, defina o parâmetro como [ByVal](../modifiers/byval.md) em vez de `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="84924-114">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>

## <a name="see-also"></a><span data-ttu-id="84924-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="84924-115">See also</span></span>

- [<span data-ttu-id="84924-116">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="84924-116">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="84924-117">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="84924-117">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="84924-118">Passar argumentos por valor e por referência</span><span class="sxs-lookup"><span data-stu-id="84924-118">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="84924-119">Conversões implícitas e explícitas</span><span class="sxs-lookup"><span data-stu-id="84924-119">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
