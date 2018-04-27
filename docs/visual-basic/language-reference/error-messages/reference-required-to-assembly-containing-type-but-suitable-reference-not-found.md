---
title: Referência necessária para o assembly &#39; &lt;assemblyidentity&gt; &#39; contendo o tipo &#39; &lt;typename&gt;&#39;, mas não foi possível encontrar uma referência adequada devido à ambiguidade entre projetos &#39; &lt;projectname1&gt; &#39; e &#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69b1184d47e427bd985c3b18135d4a0ac4d91410
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="6effb-102">Referência necessária para o assembly &#39; &lt;assemblyidentity&gt; &#39; contendo o tipo &#39; &lt;typename&gt;&#39;, mas não foi possível encontrar uma referência adequada devido à ambiguidade entre projetos &#39; &lt;projectname1&gt; &#39; e &#39; &lt;projectname2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="6effb-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="6effb-103">Uma expressão usa um tipo, como classe, estrutura, interface, enumeração ou representante, que está definido fora do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6effb-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="6effb-104">No entanto, você tem referências do projeto para definir o tipo de mais de um assembly.</span><span class="sxs-lookup"><span data-stu-id="6effb-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="6effb-105">Os projetos citados produzem assemblies com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="6effb-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="6effb-106">Portanto, o compilador não pode determinar qual assembly usar para o tipo que você está acessando.</span><span class="sxs-lookup"><span data-stu-id="6effb-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="6effb-107">Para acessar um tipo definido em outro assembly, o compilador do Visual Basic deve ter uma referência a esse assembly.</span><span class="sxs-lookup"><span data-stu-id="6effb-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="6effb-108">Isso deve ser uma referência única, não ambígua que não cause referências circulares entre projetos.</span><span class="sxs-lookup"><span data-stu-id="6effb-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="6effb-109">**ID do erro:** BC30969</span><span class="sxs-lookup"><span data-stu-id="6effb-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6effb-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6effb-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="6effb-111">Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência.</span><span class="sxs-lookup"><span data-stu-id="6effb-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="6effb-112">Para essa decisão, você pode usar critérios, como a facilidade de acesso de arquivo e a frequência de atualizações.</span><span class="sxs-lookup"><span data-stu-id="6effb-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="6effb-113">Nas propriedades do projeto, adicione uma referência para o arquivo que contém o assembly que define o tipo que você está usando.</span><span class="sxs-lookup"><span data-stu-id="6effb-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6effb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6effb-114">See Also</span></span>  
 [<span data-ttu-id="6effb-115">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="6effb-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="6effb-116">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="6effb-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="6effb-117">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="6effb-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="6effb-118">Solução de Problemas de Referências Quebradas</span><span class="sxs-lookup"><span data-stu-id="6effb-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
