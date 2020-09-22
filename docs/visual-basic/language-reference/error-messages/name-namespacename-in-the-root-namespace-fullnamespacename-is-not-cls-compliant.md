---
title: O nome <namespacename> no namespace raiz <fullnamespacename> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40039
- bc40039
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
ms.openlocfilehash: 4e29a27841021b0cf68af01f4535e60eeb38b9a8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871524"
---
# <a name="name-namespacename-in-the-root-namespace-fullnamespacename-is-not-cls-compliant"></a><span data-ttu-id="0ae14-102">O nome \<namespacename> no namespace raiz \<fullnamespacename> não é compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="0ae14-102">Name \<namespacename> in the root namespace \<fullnamespacename> is not CLS-compliant</span></span>

<span data-ttu-id="0ae14-103">Um assembly é marcado como `<CLSCompliant(True)>` , mas um elemento do nome do namespace raiz começa com um sublinhado ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="0ae14-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="0ae14-104">Um elemento de programação pode conter um ou mais sublinhados, mas para ser compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele não deve começar com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="0ae14-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="0ae14-105">Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="0ae14-105">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="0ae14-106">Quando você aplica o a <xref:System.CLSCompliantAttribute> um elemento de programação, você define o parâmetro do atributo `isCompliant` como `True` ou `False` para indicar conformidade ou não conformidade.</span><span class="sxs-lookup"><span data-stu-id="0ae14-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="0ae14-107">Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.</span><span class="sxs-lookup"><span data-stu-id="0ae14-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="0ae14-108">Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, será considerado como não compatível.</span><span class="sxs-lookup"><span data-stu-id="0ae14-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="0ae14-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="0ae14-109">By default, this message is a warning.</span></span> <span data-ttu-id="0ae14-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0ae14-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0ae14-111">**ID do erro:** BC40039</span><span class="sxs-lookup"><span data-stu-id="0ae14-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0ae14-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0ae14-112">To correct this error</span></span>  
  
- <span data-ttu-id="0ae14-113">Se você precisar de conformidade com CLS, altere o nome do namespace raiz para que nenhum de seus elementos comece com um sublinhado.</span><span class="sxs-lookup"><span data-stu-id="0ae14-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
- <span data-ttu-id="0ae14-114">Se você precisar que o nome do namespace permaneça inalterado, remova o <xref:System.CLSCompliantAttribute> do assembly ou marque-o como `<CLSCompliant(False)>` .</span><span class="sxs-lookup"><span data-stu-id="0ae14-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae14-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="0ae14-115">See also</span></span>

- [<span data-ttu-id="0ae14-116">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="0ae14-116">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="0ae14-117">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ae14-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="0ae14-118">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="0ae14-118">-rootnamespace</span></span>](../../reference/command-line-compiler/rootnamespace.md)
- [<span data-ttu-id="0ae14-119">Página de Aplicativo, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ae14-119">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="0ae14-120">Nomes de elementos declarados</span><span class="sxs-lookup"><span data-stu-id="0ae14-120">Declared Element Names</span></span>](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="0ae14-121">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ae14-121">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
