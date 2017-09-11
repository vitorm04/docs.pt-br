---
title: "Namespace ou tipo especificado no nível de projeto Imports &quot;&lt;qualifiedelementname&gt;&quot; não contém nenhum membro público ou não pode ser encontrado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
dev_langs:
- VB
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 301e2bd419f0b4723ff76c2bdd2187c4c412e174
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="827f0-102">Namespace ou tipo especificado no nível de projeto Imports '&lt;qualifiedelementname&gt;' não contém nenhum membro público ou não foi encontrado</span><span class="sxs-lookup"><span data-stu-id="827f0-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="827f0-103">Namespace ou tipo especificado no nível de projeto Imports '\<qualifiedelementname >' não contém nenhum membro público ou não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="827f0-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="827f0-104">Verifique se o namespace ou o tipo está definido e contém pelo menos um membro público.</span><span class="sxs-lookup"><span data-stu-id="827f0-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="827f0-105">Verifique se que o nome do alias não contém outros aliases.</span><span class="sxs-lookup"><span data-stu-id="827f0-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="827f0-106">Uma propriedade de importação de um projeto especifica um elemento contido que não pode ser encontrado ou não define nenhum `Public` membros.</span><span class="sxs-lookup"><span data-stu-id="827f0-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="827f0-107">A *que contém o elemento* pode ser um namespace, classe, estrutura, módulo, interface ou enumeração.</span><span class="sxs-lookup"><span data-stu-id="827f0-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="827f0-108">O elemento contido contém membros, como variáveis, procedimentos ou outros elementos contidos.</span><span class="sxs-lookup"><span data-stu-id="827f0-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="827f0-109">A finalidade da importação é permitir que seu código para acessar membros de namespace ou tipo sem ter que qualificá-los.</span><span class="sxs-lookup"><span data-stu-id="827f0-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="827f0-110">Seu projeto também precisará adicionar uma referência para o namespace ou tipo.</span><span class="sxs-lookup"><span data-stu-id="827f0-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="827f0-111">Para obter mais informações, consulte "Importing Containing Elements" [referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="827f0-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="827f0-112">Se o compilador não pode localizar o elemento contido, ele não pode resolver referências que o usam.</span><span class="sxs-lookup"><span data-stu-id="827f0-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="827f0-113">Se ele acha o elemento mas o elemento não expõe nenhum `Public` membros, então nenhuma referência pode ser bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="827f0-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="827f0-114">Em ambos os casos, faz sentido para o elemento de importação.</span><span class="sxs-lookup"><span data-stu-id="827f0-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="827f0-115">Você usa o **Project Designer** para especificar elementos a importar.</span><span class="sxs-lookup"><span data-stu-id="827f0-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="827f0-116">Use o **importado namespaces** seção o **referências** página.</span><span class="sxs-lookup"><span data-stu-id="827f0-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="827f0-117">Você pode obter o **Project Designer** clicando duas vezes o **meu projeto** ícone na **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="827f0-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="827f0-118">**ID do erro:** BC40057</span><span class="sxs-lookup"><span data-stu-id="827f0-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="827f0-119">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="827f0-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="827f0-120">Abra o **Project Designer** e alternar para o **referência** página.</span><span class="sxs-lookup"><span data-stu-id="827f0-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="827f0-121">No **importado namespaces** seção, verifique se que o elemento contêiner está acessível do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="827f0-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="827f0-122">Verifique se que o elemento contêiner expõe pelo menos um `Public` membro.</span><span class="sxs-lookup"><span data-stu-id="827f0-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827f0-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="827f0-123">See Also</span></span>  
 <span data-ttu-id="827f0-124">[Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="827f0-124">[References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="827f0-125"> [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="827f0-125"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="827f0-126"> [Público](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="827f0-126"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="827f0-127"> [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="827f0-127"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="827f0-128"> [Referências a Elementos Declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="827f0-128"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
