---
title: O nome <membername> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 33b60b2212d25737330dc93d7ba2715e4d5865b7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873702"
---
# <a name="name-membername-is-not-cls-compliant"></a><span data-ttu-id="3f1ce-102">O nome \<membername> não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="3f1ce-102">Name \<membername> is not CLS-compliant</span></span>

<span data-ttu-id="3f1ce-103">Um assembly é marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="3f1ce-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="3f1ce-104">Um elemento de programação pode conter um ou mais sublinhados, mas para ser compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="3f1ce-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="3f1ce-105">Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="3f1ce-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="3f1ce-106">Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade.</span><span class="sxs-lookup"><span data-stu-id="3f1ce-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="3f1ce-107">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="3f1ce-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="3f1ce-108">Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.</span><span class="sxs-lookup"><span data-stu-id="3f1ce-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="3f1ce-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="3f1ce-109">By default, this message is a warning.</span></span> <span data-ttu-id="3f1ce-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3f1ce-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3f1ce-111">**ID do erro:** BC40031</span><span class="sxs-lookup"><span data-stu-id="3f1ce-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3f1ce-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3f1ce-112">To correct this error</span></span>  
  
- <span data-ttu-id="3f1ce-113">Se você tiver controle sobre o código-fonte, altere o nome do membro para que ele não comece com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="3f1ce-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
- <span data-ttu-id="3f1ce-114">Se você precisar que o nome do membro permaneça inalterado, remova o <xref:System.CLSCompliantAttribute> de sua definição ou marque-o como `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="3f1ce-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="3f1ce-115">Você ainda pode marcar o assembly como `<CLSCompliant(True)>` .</span><span class="sxs-lookup"><span data-stu-id="3f1ce-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f1ce-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="3f1ce-116">See also</span></span>

- [<span data-ttu-id="3f1ce-117">Nomes de elementos declarados</span><span class="sxs-lookup"><span data-stu-id="3f1ce-117">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="3f1ce-118">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f1ce-118">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
