---
title: O namespace ou o tipo especificado no nível de projeto Imports '<qualifiedelementname>' não contém nenhum membro público ou não pode ser localizado.
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 105fa8da838938d13022c210c1f65cdafd251003
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918301"
---
# <a name="namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="0abb6-102">Namespace ou tipo especificado no nível de projeto Imports '\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado</span><span class="sxs-lookup"><span data-stu-id="0abb6-102">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>
<span data-ttu-id="0abb6-103">Namespace ou tipo especificado no nível de projeto Imports '\<qualifiedelementname >' não contém nenhum membro público ou não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="0abb6-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="0abb6-104">Verifique se o namespace ou o tipo é definido e contém pelo menos um membro público.</span><span class="sxs-lookup"><span data-stu-id="0abb6-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="0abb6-105">Verifique se que o nome do alias não contém outros aliases.</span><span class="sxs-lookup"><span data-stu-id="0abb6-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="0abb6-106">Uma propriedade de importação de um projeto especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.</span><span class="sxs-lookup"><span data-stu-id="0abb6-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="0abb6-107">Um *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração.</span><span class="sxs-lookup"><span data-stu-id="0abb6-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="0abb6-108">O elemento contido contém membros, como variáveis, procedimentos ou outros elementos que contém.</span><span class="sxs-lookup"><span data-stu-id="0abb6-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="0abb6-109">A finalidade de importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="0abb6-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="0abb6-110">Seu projeto talvez seja necessário também adicionar uma referência para o namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="0abb6-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="0abb6-111">Para obter mais informações, consulte "Importação de elementos que contém" na [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="0abb6-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="0abb6-112">Se o compilador não pode localizar o elemento contido, ele não é possível resolver as referências que usá-lo.</span><span class="sxs-lookup"><span data-stu-id="0abb6-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="0abb6-113">Se ele localiza o elemento, mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0abb6-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="0abb6-114">Em ambos os casos não faz sentido para o elemento de importação.</span><span class="sxs-lookup"><span data-stu-id="0abb6-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="0abb6-115">Você usa o **Designer de projeto** para especificar elementos a importar.</span><span class="sxs-lookup"><span data-stu-id="0abb6-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="0abb6-116">Use o **namespaces importados** seção o **referências** página.</span><span class="sxs-lookup"><span data-stu-id="0abb6-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="0abb6-117">Você pode obter o **Designer de projeto** clicando duas vezes o **My Project** ícone na **Gerenciador de soluções**.</span><span class="sxs-lookup"><span data-stu-id="0abb6-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="0abb6-118">**ID do erro:** BC40057</span><span class="sxs-lookup"><span data-stu-id="0abb6-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0abb6-119">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0abb6-119">To correct this error</span></span>  
  
1. <span data-ttu-id="0abb6-120">Abra o **Designer de projeto** e alterne para o **referência** página.</span><span class="sxs-lookup"><span data-stu-id="0abb6-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2. <span data-ttu-id="0abb6-121">No **namespaces importados** seção, verifique se o elemento que o contém é acessível a partir de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="0abb6-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3. <span data-ttu-id="0abb6-122">Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="0abb6-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abb6-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0abb6-123">See also</span></span>

- [<span data-ttu-id="0abb6-124">Página Referências, Designer de Projeto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0abb6-124">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="0abb6-125">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="0abb6-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="0abb6-126">Público</span><span class="sxs-lookup"><span data-stu-id="0abb6-126">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="0abb6-127">Namespaces no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0abb6-127">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="0abb6-128">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="0abb6-128">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
