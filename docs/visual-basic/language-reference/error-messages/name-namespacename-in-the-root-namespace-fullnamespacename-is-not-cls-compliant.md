---
title: Nome da &lt;namespacename&gt; no namespace raiz &lt;fullnamespacename&gt; não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 8d35268891711ca7f2a7f5ec47be425e342dccd7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642523"
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="42414-102">Nome da &lt;namespacename&gt; no namespace raiz &lt;fullnamespacename&gt; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="42414-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="42414-103">Um assembly é marcado como `<CLSCompliant(True)>`, mas um elemento do nome do namespace raiz começa com um sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="42414-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="42414-104">Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="42414-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="42414-105">Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="42414-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="42414-106">Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="42414-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="42414-107">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="42414-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="42414-108">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="42414-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="42414-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="42414-109">By default, this message is a warning.</span></span> <span data-ttu-id="42414-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="42414-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="42414-111">**ID do erro:** BC40039</span><span class="sxs-lookup"><span data-stu-id="42414-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="42414-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="42414-112">To correct this error</span></span>  
  
-   <span data-ttu-id="42414-113">Se você precisar de conformidade com CLS, altere o nome do namespace raiz para que nenhum de seus elementos começa com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="42414-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="42414-114">Se você precisar que o nome do namespace permanecem inalterados, em seguida, remova os <xref:System.CLSCompliantAttribute> do assembly ou marcá-la como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="42414-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42414-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42414-115">See also</span></span>
- [<span data-ttu-id="42414-116">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="42414-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="42414-117">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42414-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="42414-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="42414-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="42414-119">Página de Aplicativo, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42414-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="42414-120">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="42414-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="42414-121">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42414-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)

