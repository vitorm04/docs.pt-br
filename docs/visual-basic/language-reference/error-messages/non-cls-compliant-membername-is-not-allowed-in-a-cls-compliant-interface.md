---
title: <membername> não compatível com CLS não é permitido em uma interface compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: 68e1fb4f55d9f9b140f1b54cfde2bc5f60952dd2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592133"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="838f1-102">Não compatível com CLS \<membername > não é permitido em uma interface compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="838f1-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="838f1-103">Uma propriedade, procedimento ou evento em uma interface é marcado como `<CLSCompliant(True)>` quando a própria interface é marcada como `<CLSCompliant(False)>` ou não está marcado.</span><span class="sxs-lookup"><span data-stu-id="838f1-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="838f1-104">Para uma interface para estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), todos os seus membros devem estar em conformidade.</span><span class="sxs-lookup"><span data-stu-id="838f1-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="838f1-105">Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="838f1-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="838f1-106">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="838f1-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="838f1-107">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="838f1-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="838f1-108">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="838f1-108">By default, this message is a warning.</span></span> <span data-ttu-id="838f1-109">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="838f1-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="838f1-110">**ID do erro:** BC40033</span><span class="sxs-lookup"><span data-stu-id="838f1-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="838f1-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="838f1-111">To correct this error</span></span>  
  
- <span data-ttu-id="838f1-112">Se você exige conformidade com CLS e tem controle sobre o código-fonte de interface, marque a interface como `<CLSCompliant(True)>` se todos os seus membros estão em conformidade.</span><span class="sxs-lookup"><span data-stu-id="838f1-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="838f1-113">Se você exige conformidade com CLS e não tem controle sobre o código de origem da interface, ou se ele não se qualifica para estar em conformidade, defina este membro dentro de uma interface diferente.</span><span class="sxs-lookup"><span data-stu-id="838f1-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="838f1-114">Se você precisar que esse membro permaneça em sua interface atual, remova os <xref:System.CLSCompliantAttribute> de sua definição ou marque-a como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="838f1-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838f1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="838f1-115">See also</span></span>

- [<span data-ttu-id="838f1-116">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="838f1-116">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
