---
title: <proceduresignature1> não está em conformidade com CLS porque sobrecarrega <proceduresignature2> que difere dele somente pelos tipos de matriz e parâmetro de matriz ou pela classificação dos tipos de parâmetro da matriz
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250178"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="d0f57-102">\<proceduresignature1 > não tem conformidade com CLS porque ele sobrecarrega \<proceduresignature2 > que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz</span><span class="sxs-lookup"><span data-stu-id="d0f57-102">\<proceduresignature1> is not CLS-compliant because it overloads \<proceduresignature2> which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>

<span data-ttu-id="d0f57-103">Um procedimento ou propriedade é marcado como `<CLSCompliant(True)>` quando ele substitui outro procedimento ou propriedade e a única diferença entre suas listas de parâmetros é o nível de aninhamento de uma matriz denteada ou a classificação de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="d0f57-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>
  
 <span data-ttu-id="d0f57-104">Nas declarações a seguir, a segunda e terceira declarações geram esse erro:</span><span class="sxs-lookup"><span data-stu-id="d0f57-104">In the following declarations, the second and third declarations generate this error:</span></span>
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 <span data-ttu-id="d0f57-105">A segunda declaração altera o parâmetro unidimensional original `arrayParam` para uma matriz de matrizes.</span><span class="sxs-lookup"><span data-stu-id="d0f57-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="d0f57-106">A terceira declaração muda `arrayParam` para uma matriz bidimensional (Rank 2).</span><span class="sxs-lookup"><span data-stu-id="d0f57-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="d0f57-107">Embora Visual Basic permita sobrecargas para diferir apenas por uma dessas alterações, esse sobrecarregamento não é compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="d0f57-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="d0f57-108">Quando você aplica o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo como `True` ou `False` para indicar a conformidade ou a não conformidade.</span><span class="sxs-lookup"><span data-stu-id="d0f57-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="d0f57-109">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="d0f57-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="d0f57-110">Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele será considerado não compatível.</span><span class="sxs-lookup"><span data-stu-id="d0f57-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="d0f57-111">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="d0f57-111">By default, this message is a warning.</span></span> <span data-ttu-id="d0f57-112">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d0f57-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d0f57-113">**ID do erro:** BC40035</span><span class="sxs-lookup"><span data-stu-id="d0f57-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d0f57-114">Para corrigir esse erro</span><span class="sxs-lookup"><span data-stu-id="d0f57-114">To correct this error</span></span>  
  
- <span data-ttu-id="d0f57-115">Se você precisar de conformidade com CLS, defina suas sobrecargas para diferir umas das outras em mais formas do que apenas as alterações citadas nesta página de ajuda.</span><span class="sxs-lookup"><span data-stu-id="d0f57-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>
- <span data-ttu-id="d0f57-116">Se você precisar que as sobrecargas diferem apenas pelas alterações citadas nesta página de ajuda, remova o <xref:System.CLSCompliantAttribute> de suas definições ou marque-os como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="d0f57-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d0f57-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0f57-117">See also</span></span>

- [<span data-ttu-id="d0f57-118">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="d0f57-118">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d0f57-119">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="d0f57-119">Overloads</span></span>](../modifiers/overloads.md)
