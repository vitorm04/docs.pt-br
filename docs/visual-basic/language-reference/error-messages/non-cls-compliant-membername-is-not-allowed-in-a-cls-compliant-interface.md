---
title: "Não compatível com CLS &lt;membername&gt; não é permitido em uma interface compatível com CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords: BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2811958df5bd0b023a2ce3b02abf85b5a23c58f6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="fb07d-102">Não compatível com CLS &lt;membername&gt; não é permitido em uma interface compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="fb07d-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="fb07d-103">Uma propriedade, procedimento ou evento em uma interface está marcado como `<CLSCompliant(True)>` quando a própria interface está marcada como `<CLSCompliant(False)>` ou não está marcado.</span><span class="sxs-lookup"><span data-stu-id="fb07d-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="fb07d-104">Para uma interface para ser compatível com o [independência da linguagem e componentes independentes da linguagem](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), todos os seus membros devem ser compatíveis.</span><span class="sxs-lookup"><span data-stu-id="fb07d-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="fb07d-105">Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="fb07d-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="fb07d-106">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="fb07d-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="fb07d-107">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="fb07d-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="fb07d-108">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="fb07d-108">By default, this message is a warning.</span></span> <span data-ttu-id="fb07d-109">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fb07d-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fb07d-110">**ID do erro:** BC40033</span><span class="sxs-lookup"><span data-stu-id="fb07d-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fb07d-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="fb07d-111">To correct this error</span></span>  
  
-   <span data-ttu-id="fb07d-112">Se você precisar de compatibilidade com CLS e tem controle sobre o código de origem da interface, marque a interface como `<CLSCompliant(True)>` se todos os seus membros são compatíveis.</span><span class="sxs-lookup"><span data-stu-id="fb07d-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="fb07d-113">Se você precisar de compatibilidade com CLS e não tem controle sobre o código de origem da interface, ou se ele não está qualificada para ser compatível, defina este membro dentro de uma interface diferente.</span><span class="sxs-lookup"><span data-stu-id="fb07d-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="fb07d-114">Se você precisar que esse membro permaneça em sua interface atual, remova o <xref:System.CLSCompliantAttribute> da sua definição ou marque-a como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="fb07d-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb07d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb07d-115">See Also</span></span>  
 [<span data-ttu-id="fb07d-116">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="fb07d-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="fb07d-117">\<PAVE sobre > escrevendo código compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="fb07d-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
