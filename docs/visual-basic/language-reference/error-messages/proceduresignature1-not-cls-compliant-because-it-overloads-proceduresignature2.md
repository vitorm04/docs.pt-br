---
title: "&lt;proceduresignature1&gt; não é compatível com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords: BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d361759471a8edfa97437bd2503cfaa661fb9678
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="3ae81-102">&lt;proceduresignature1&gt; não é compatível com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz</span><span class="sxs-lookup"><span data-stu-id="3ae81-102">&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="3ae81-103">Um procedimento ou propriedade é marcada como `<CLSCompliant(True)>` quando substitui outro procedimento ou propriedade e a única diferença entre suas listas de parâmetro é o nível de aninhamento de uma matriz denteada ou a posição de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="3ae81-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="3ae81-104">Em declarações a seguir, as segunda e terceira declarações geram esse erro.</span><span class="sxs-lookup"><span data-stu-id="3ae81-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="3ae81-105">A segunda declaração altera o parâmetro unidimensional original `arrayParam` para uma matriz de matrizes.</span><span class="sxs-lookup"><span data-stu-id="3ae81-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="3ae81-106">A terceira declaração muda `arrayParam` para uma matriz bidimensional (posição 2).</span><span class="sxs-lookup"><span data-stu-id="3ae81-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="3ae81-107">Enquanto o Visual Basic permite sobrecargas diferir somente por uma dessas alterações, tais sobrecargas não são compatíveis com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="3ae81-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="3ae81-108">Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="3ae81-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="3ae81-109">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="3ae81-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="3ae81-110">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="3ae81-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="3ae81-111">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="3ae81-111">By default, this message is a warning.</span></span> <span data-ttu-id="3ae81-112">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3ae81-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3ae81-113">**ID do erro:** BC40035</span><span class="sxs-lookup"><span data-stu-id="3ae81-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3ae81-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3ae81-114">To correct this error</span></span>  
  
-   <span data-ttu-id="3ae81-115">Se você precisar de compatibilidade com CLS, defina suas sobrecargas para diferem entre si em mais maneiras do que apenas as alterações citadas nessa página de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="3ae81-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="3ae81-116">Se você precisar que as sobrecargas sejam diferentes somente pelas alterações citadas na Ajuda da página, remova o <xref:System.CLSCompliantAttribute> de suas definições ou marcá-los como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="3ae81-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae81-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3ae81-117">See Also</span></span>  
   
 [<span data-ttu-id="3ae81-118">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="3ae81-118">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [<span data-ttu-id="3ae81-119">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="3ae81-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)
