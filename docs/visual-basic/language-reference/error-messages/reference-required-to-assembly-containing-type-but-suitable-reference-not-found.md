---
title: Referência obrigatória ao assembly '<assemblyidentity>' contendo o tipo '<typename>', mas não foi possível localizar uma referência adequada devido à ambiguidade entre os projetos '<projectname1>' e '<projectname2>'
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 4b9f74f0627268752b0ba3c3816fe9d4cc8a231b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404817"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="adf48-102">Referência obrigatória ao assembly '\<assemblyidentity>' contendo o tipo '\<typename>', mas não foi possível localizar uma referência adequada devido à ambiguidade entre os projetos '\<projectname1>' e '\<projectname2>'</span><span class="sxs-lookup"><span data-stu-id="adf48-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>
<span data-ttu-id="adf48-103">Uma expressão usa um tipo, como uma classe, estrutura, interface, enumeração ou delegado, que é definido fora do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="adf48-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="adf48-104">No entanto, você tem referências de projeto para mais de um assembly que define esse tipo.</span><span class="sxs-lookup"><span data-stu-id="adf48-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="adf48-105">Os projetos citados produzem assemblies com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="adf48-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="adf48-106">Portanto, o compilador não pode determinar qual assembly usar para o tipo que você está acessando.</span><span class="sxs-lookup"><span data-stu-id="adf48-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="adf48-107">Para acessar um tipo definido em outro assembly, o compilador Visual Basic deve ter uma referência a esse assembly.</span><span class="sxs-lookup"><span data-stu-id="adf48-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="adf48-108">Essa deve ser uma referência única e não ambígua que não cause referências circulares entre projetos.</span><span class="sxs-lookup"><span data-stu-id="adf48-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="adf48-109">**ID do erro:** BC30969</span><span class="sxs-lookup"><span data-stu-id="adf48-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="adf48-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="adf48-110">To correct this error</span></span>  
  
1. <span data-ttu-id="adf48-111">Determine qual projeto produz o melhor assembly para referência do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="adf48-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="adf48-112">Para essa decisão, você pode usar critérios como a facilidade de acesso a arquivos e a frequência de atualizações.</span><span class="sxs-lookup"><span data-stu-id="adf48-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="adf48-113">Nas propriedades do projeto, adicione uma referência ao arquivo que contém o assembly que define o tipo que você está usando.</span><span class="sxs-lookup"><span data-stu-id="adf48-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf48-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="adf48-114">See also</span></span>

- [<span data-ttu-id="adf48-115">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="adf48-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="adf48-116">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="adf48-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="adf48-117">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="adf48-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="adf48-118">Solução de Problemas de Referências Quebradas</span><span class="sxs-lookup"><span data-stu-id="adf48-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
