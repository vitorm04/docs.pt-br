---
title: "Nome &lt;membername&gt; não é compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords: BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7f574c2ebd71dbe06c4a687728e7812a18c8a949
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="7ac5b-102">Nome &lt;membername&gt; não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="7ac5b-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="7ac5b-103">Um assembly é marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="7ac5b-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="7ac5b-104">Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com a [independência da linguagem e componentes independentes da linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS), ele não deve começar com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="7ac5b-105">Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="7ac5b-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="7ac5b-106">Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="7ac5b-107">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="7ac5b-108">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="7ac5b-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-109">By default, this message is a warning.</span></span> <span data-ttu-id="7ac5b-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7ac5b-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7ac5b-111">**ID do erro:** BC40031</span><span class="sxs-lookup"><span data-stu-id="7ac5b-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7ac5b-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7ac5b-112">To correct this error</span></span>  
  
-   <span data-ttu-id="7ac5b-113">Se você tem controle sobre o código-fonte, altere o nome de membro para que ele não começa com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="7ac5b-114">Se você precisar que o nome do membro permanecem inalteradas, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque-a como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="7ac5b-115">Você ainda poderá marcar o assembly como `<CLSCompliant(True)>`.</span><span class="sxs-lookup"><span data-stu-id="7ac5b-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ac5b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ac5b-116">See Also</span></span>  
 [<span data-ttu-id="7ac5b-117">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="7ac5b-117">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="7ac5b-118">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ac5b-118">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="7ac5b-119">\<PAVE sobre > escrevendo código compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="7ac5b-119">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
