---
title: Namespace ou tipo especificado em Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t contém nenhum membro público ou não foi encontrado
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 21c0794fb4ed6104204fba5d49e37394eff24865
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552132"
---
# <a name="namespace-or-type-specified-in-the-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="5b543-102">Namespace ou tipo especificado em Imports &#39; &lt;qualifiedelementname&gt; &#39; &#39;t contém nenhum membro público ou não foi encontrado</span><span class="sxs-lookup"><span data-stu-id="5b543-102">Namespace or type specified in the Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="5b543-103">Tipo ou Namespace especificado em Imports'\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="5b543-103">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="5b543-104">Verifique se o namespace ou o tipo é definido e contém pelo menos um membro público.</span><span class="sxs-lookup"><span data-stu-id="5b543-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="5b543-105">Verifique se que o nome do alias não contém outros aliases.</span><span class="sxs-lookup"><span data-stu-id="5b543-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="5b543-106">Uma `Imports` declaração especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.</span><span class="sxs-lookup"><span data-stu-id="5b543-106">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="5b543-107">Um *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração.</span><span class="sxs-lookup"><span data-stu-id="5b543-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="5b543-108">O elemento contido contém membros, como variáveis, procedimentos ou outros elementos que contém.</span><span class="sxs-lookup"><span data-stu-id="5b543-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="5b543-109">A finalidade de importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="5b543-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="5b543-110">Seu projeto talvez seja necessário também adicionar uma referência para o namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="5b543-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="5b543-111">Para obter mais informações, consulte "Importação de elementos que contém" na [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="5b543-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="5b543-112">Se o compilador não pode localizar o elemento contido, ele não é possível resolver as referências que usá-lo.</span><span class="sxs-lookup"><span data-stu-id="5b543-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="5b543-113">Se ele localiza o elemento, mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5b543-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="5b543-114">Em ambos os casos não faz sentido para o elemento de importação.</span><span class="sxs-lookup"><span data-stu-id="5b543-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="5b543-115">Tenha em mente que se você importar um elemento de recipiente e atribuir um alias de importação para ele, em seguida, é possível usar esse alias de importação para importar de outro elemento.</span><span class="sxs-lookup"><span data-stu-id="5b543-115">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="5b543-116">O código a seguir gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="5b543-116">The following code generates a compiler error.</span></span>  
  
 <span data-ttu-id="5b543-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span><span class="sxs-lookup"><span data-stu-id="5b543-117">`Imports`   `winfrm`   `= System.Windows.Forms`</span></span>  
  
 <span data-ttu-id="5b543-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span><span class="sxs-lookup"><span data-stu-id="5b543-118">`' The following statement is`   `INVALID`   `because it reuses an import alias.`</span></span>  
  
 <span data-ttu-id="5b543-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span><span class="sxs-lookup"><span data-stu-id="5b543-119">`Imports behav =`   `winfrm`  `.Design.Behavior`</span></span>  
  
 <span data-ttu-id="5b543-120">**ID do erro:** BC40056</span><span class="sxs-lookup"><span data-stu-id="5b543-120">**Error ID:** BC40056</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5b543-121">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5b543-121">To correct this error</span></span>  
  
1.  <span data-ttu-id="5b543-122">Verifique se o elemento que o contém é acessível a partir de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5b543-122">Verify that the containing element is accessible from your project.</span></span>  
  
2.  <span data-ttu-id="5b543-123">Verifique se que a especificação do elemento contido não inclui qualquer alias de importação da importação de outro.</span><span class="sxs-lookup"><span data-stu-id="5b543-123">Verify that the specification of the containing element does not include any import alias from another import.</span></span>  
  
3.  <span data-ttu-id="5b543-124">Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="5b543-124">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b543-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b543-125">See also</span></span>
- [<span data-ttu-id="5b543-126">Instrução Imports (Tipo e Namespace .NET)</span><span class="sxs-lookup"><span data-stu-id="5b543-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="5b543-127">Instrução Namespace</span><span class="sxs-lookup"><span data-stu-id="5b543-127">Namespace Statement</span></span>](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="5b543-128">Público</span><span class="sxs-lookup"><span data-stu-id="5b543-128">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="5b543-129">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b543-129">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="5b543-130">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="5b543-130">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
