---
title: O nome <membername> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 06b20b4f61741f2174654d749df55c3c4348c547
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824618"
---
# <a name="name-membername-is-not-cls-compliant"></a><span data-ttu-id="33d02-102">Nome \<membername > não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="33d02-102">Name \<membername> is not CLS-compliant</span></span>
<span data-ttu-id="33d02-103">Um assembly é marcado como `<CLSCompliant(True)>` , mas expõe um membro com um nome que começa com um sublinhado (`_`).</span><span class="sxs-lookup"><span data-stu-id="33d02-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="33d02-104">Um elemento de programação pode conter um ou mais sublinhados, mas to estar em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="33d02-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="33d02-105">Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="33d02-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="33d02-106">Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="33d02-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="33d02-107">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="33d02-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="33d02-108">Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.</span><span class="sxs-lookup"><span data-stu-id="33d02-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="33d02-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="33d02-109">By default, this message is a warning.</span></span> <span data-ttu-id="33d02-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="33d02-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="33d02-111">**ID do erro:** BC40031</span><span class="sxs-lookup"><span data-stu-id="33d02-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="33d02-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="33d02-112">To correct this error</span></span>  
  
-   <span data-ttu-id="33d02-113">Se você tem controle sobre o código-fonte, altere o nome do membro para que ele não começa com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="33d02-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="33d02-114">Se você precisar que o nome do membro permanecem inalterados, remova os <xref:System.CLSCompliantAttribute> de sua definição ou marque-a como `<CLSCompliant(False)>`.</span><span class="sxs-lookup"><span data-stu-id="33d02-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="33d02-115">Você ainda poderá marcar o assembly como `<CLSCompliant(True)>`.</span><span class="sxs-lookup"><span data-stu-id="33d02-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d02-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33d02-116">See also</span></span>

- [<span data-ttu-id="33d02-117">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="33d02-117">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="33d02-118">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33d02-118">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
