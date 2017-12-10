---
title: "Nome &lt;namespacename&gt; no namespace raiz &lt;fullnamespacename&gt; não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords: BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 36de8b6a27c47e9e7192aed10e6b561bb0c07acc
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="5c324-102">Nome &lt;namespacename&gt; no namespace raiz &lt;fullnamespacename&gt; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="5c324-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="5c324-103">Um assembly é marcado como `<CLSCompliant(True)>`, mas um elemento do nome do namespace raiz começa com um sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="5c324-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="5c324-104">Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com a [independência da linguagem e componentes independentes da linguagem](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="5c324-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="5c324-105">Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5c324-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="5c324-106">Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="5c324-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5c324-107">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="5c324-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5c324-108">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="5c324-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5c324-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="5c324-109">By default, this message is a warning.</span></span> <span data-ttu-id="5c324-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5c324-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5c324-111">**ID do erro:** BC40039</span><span class="sxs-lookup"><span data-stu-id="5c324-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c324-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5c324-112">To correct this error</span></span>  
  
-   <span data-ttu-id="5c324-113">Se você precisar de compatibilidade com CLS, altere o nome do namespace raiz para que nenhum de seus elementos começa com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="5c324-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="5c324-114">Se você precisar que o nome do namespace permanecem inalteradas, em seguida, remova o <xref:System.CLSCompliantAttribute> do assembly ou marque-a como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="5c324-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c324-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c324-115">See Also</span></span>  
 [<span data-ttu-id="5c324-116">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="5c324-116">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="5c324-117">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c324-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [<span data-ttu-id="5c324-118">/rootnamespace</span><span class="sxs-lookup"><span data-stu-id="5c324-118">/rootnamespace</span></span>](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)  
 [<span data-ttu-id="5c324-119">Página de Aplicativo, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c324-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="5c324-120">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="5c324-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="5c324-121">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c324-121">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="5c324-122">\<PAVE sobre > escrevendo código compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="5c324-122">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
