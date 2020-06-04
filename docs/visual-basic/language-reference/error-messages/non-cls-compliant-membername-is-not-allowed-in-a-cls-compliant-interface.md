---
title: <membername> não compatível com CLS não é permitido em uma interface compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: e572189b958612bf9527c82ce702df3ab929a23f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409394"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="26202-102">\<membername> não compatível com CLS não é permitido em uma interface compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="26202-102">Non-CLS-compliant \<membername> is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="26202-103">Uma propriedade, um procedimento ou um evento em uma interface é marcado como `<CLSCompliant(True)>` quando a própria interface está marcada como `<CLSCompliant(False)>` ou não está marcada.</span><span class="sxs-lookup"><span data-stu-id="26202-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="26202-104">Para que uma interface seja compatível com a [independência de idioma e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), todos os seus membros devem estar em conformidade.</span><span class="sxs-lookup"><span data-stu-id="26202-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="26202-105">Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade.</span><span class="sxs-lookup"><span data-stu-id="26202-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="26202-106">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="26202-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="26202-107">Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.</span><span class="sxs-lookup"><span data-stu-id="26202-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="26202-108">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="26202-108">By default, this message is a warning.</span></span> <span data-ttu-id="26202-109">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="26202-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="26202-110">**ID do erro:** BC40033</span><span class="sxs-lookup"><span data-stu-id="26202-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="26202-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="26202-111">To correct this error</span></span>  
  
- <span data-ttu-id="26202-112">Se você precisar de conformidade com CLS e tiver controle sobre o código-fonte da interface, marque a interface como `<CLSCompliant(True)>` se todos os seus membros estiverem em conformidade.</span><span class="sxs-lookup"><span data-stu-id="26202-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
- <span data-ttu-id="26202-113">Se você precisar de conformidade com CLS e não tiver controle sobre o código-fonte da interface, ou se ele não estiver qualificado para ser compatível, defina esse membro em uma interface diferente.</span><span class="sxs-lookup"><span data-stu-id="26202-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
- <span data-ttu-id="26202-114">Se você precisar que esse membro permaneça em sua interface atual, remova o <xref:System.CLSCompliantAttribute> de sua definição ou marque-o como `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="26202-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26202-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="26202-115">See also</span></span>

- [<span data-ttu-id="26202-116">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="26202-116">Interface Statement</span></span>](../statements/interface-statement.md)
