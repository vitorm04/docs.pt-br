---
title: "Referência necessária para o assembly &quot;&lt;assemblyidentity&gt;&quot;contendo o tipo&quot;&lt;typename&gt;&quot;, mas não foi possível encontrar uma referência adequada devido à ambiguidade entre os projetos&lt;projectname1&gt;&quot;e&quot;&lt;projectname2&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
dev_langs:
- VB
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: bb5375366fa525a0ca9c16944d026ca499062ed8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="6041e-102">Referência necessária para o assembly '&lt;assemblyidentity&gt;'contendo o tipo'&lt;typename&gt;', mas não foi possível encontrar uma referência adequada devido à ambiguidade entre os projetos&lt;projectname1&gt;'e'&lt;projectname2&gt;'</span><span class="sxs-lookup"><span data-stu-id="6041e-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="6041e-103">Uma expressão usa um tipo, como uma classe, estrutura, interface, enumeração ou delegado, que é definido fora do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="6041e-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="6041e-104">No entanto, você tem referências do projeto a mais de um assembly definindo o tipo.</span><span class="sxs-lookup"><span data-stu-id="6041e-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="6041e-105">Os projetos citados produzem assemblies com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="6041e-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="6041e-106">Portanto, o compilador não pode determinar qual assembly usar para o tipo que você está acessando.</span><span class="sxs-lookup"><span data-stu-id="6041e-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="6041e-107">Para acessar um tipo definido em outro assembly, o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador deve ter uma referência a esse assembly.</span><span class="sxs-lookup"><span data-stu-id="6041e-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="6041e-108">Isso deve ser uma referência única e não ambígua, que não cause referências circulares entre projetos.</span><span class="sxs-lookup"><span data-stu-id="6041e-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="6041e-109">**ID do erro:** BC30969</span><span class="sxs-lookup"><span data-stu-id="6041e-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6041e-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6041e-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="6041e-111">Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência.</span><span class="sxs-lookup"><span data-stu-id="6041e-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="6041e-112">Para essa decisão, você pode usar critérios, como a facilidade de acesso a arquivos e a frequência de atualizações.</span><span class="sxs-lookup"><span data-stu-id="6041e-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="6041e-113">Nas propriedades do projeto, adicione uma referência para o arquivo que contém o assembly que define o tipo que você está usando.</span><span class="sxs-lookup"><span data-stu-id="6041e-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6041e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6041e-114">See Also</span></span>  
 <span data-ttu-id="6041e-115">[Gerenciando referências em um projeto](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="6041e-115">[Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="6041e-116"> [Referências a elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="6041e-116"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="6041e-117"> [NIB: como adicionar ou remover referências usando a caixa de diálogo Adicionar Referência](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="6041e-117"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="6041e-118"> [PONTA como: modificar propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="6041e-118"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="6041e-119"> [Solução de Problemas de Referências Quebradas](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span><span class="sxs-lookup"><span data-stu-id="6041e-119"> [Troubleshooting Broken References](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span></span>
