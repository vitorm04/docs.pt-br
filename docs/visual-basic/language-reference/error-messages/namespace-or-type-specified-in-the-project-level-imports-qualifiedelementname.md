---
title: O namespace ou o tipo especificado no nível de projeto Imports '<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado.
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: e0be18509d0d4b1b4f5eadfadce7a0785e9309f0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871511"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="696df-102">O namespace ou o tipo especificado no nível de projeto Imports '\<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado.</span><span class="sxs-lookup"><span data-stu-id="696df-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="696df-103">O namespace ou tipo especificado nas importações de nível de projeto ' \<qualifiedelementname> ' não contém nenhum membro público ou não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="696df-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="696df-104">Verifique se o namespace ou o tipo está definido e contém pelo menos um membro público.</span><span class="sxs-lookup"><span data-stu-id="696df-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="696df-105">Verifique se o nome do alias não contém outros aliases.</span><span class="sxs-lookup"><span data-stu-id="696df-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="696df-106">Uma propriedade de importação de um projeto especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="696df-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="696df-107">Um *elemento recipiente* pode ser um namespace, uma classe, uma estrutura, um módulo, uma interface ou uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="696df-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="696df-108">O elemento contentor contém membros, como variáveis, procedimentos ou outros elementos que os contêm.</span><span class="sxs-lookup"><span data-stu-id="696df-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="696df-109">A finalidade da importação é permitir que seu código acesse namespace ou membros de tipo sem precisar qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="696df-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="696df-110">Seu projeto também pode precisar adicionar uma referência ao namespace ou ao tipo.</span><span class="sxs-lookup"><span data-stu-id="696df-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="696df-111">Para obter mais informações, consulte "importando elementos continentes" em [referências a elementos declarados](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="696df-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="696df-112">Se o compilador não encontrar o elemento contido especificado, ele não poderá resolver referências que o utilizam.</span><span class="sxs-lookup"><span data-stu-id="696df-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="696df-113">Se encontrar o elemento, mas o elemento não expor nenhum `Public` membro, nenhuma referência poderá ser bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="696df-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="696df-114">Em ambos os casos, não há sentido para importar o elemento.</span><span class="sxs-lookup"><span data-stu-id="696df-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="696df-115">Você usa o **Designer de projeto** para especificar elementos a serem importados.</span><span class="sxs-lookup"><span data-stu-id="696df-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="696df-116">Use a seção **namespaces importados** da página **referências** .</span><span class="sxs-lookup"><span data-stu-id="696df-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="696df-117">Você pode acessar o **Designer de projeto** clicando duas vezes no ícone **meu projeto** em **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="696df-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="696df-118">**ID do erro:** BC40057</span><span class="sxs-lookup"><span data-stu-id="696df-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="696df-119">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="696df-119">To correct this error</span></span>  
  
1. <span data-ttu-id="696df-120">Abra o **Designer de projeto** e alterne para a página de **referência** .</span><span class="sxs-lookup"><span data-stu-id="696df-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2. <span data-ttu-id="696df-121">Na seção **namespaces importados** , verifique se o elemento que o contém pode ser acessado do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="696df-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3. <span data-ttu-id="696df-122">Verifique se o elemento que o contém expõe pelo menos um `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="696df-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696df-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="696df-123">See also</span></span>

- [<span data-ttu-id="696df-124">Página Referências, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="696df-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="696df-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="696df-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="696df-126">Pública</span><span class="sxs-lookup"><span data-stu-id="696df-126">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="696df-127">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="696df-127">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="696df-128">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="696df-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
