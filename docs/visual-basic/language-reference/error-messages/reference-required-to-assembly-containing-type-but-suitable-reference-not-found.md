---
title: Referência obrigatória ao assembly '<assemblyidentity>' contendo o tipo '<typename>', mas não foi possível localizar uma referência adequada devido à ambiguidade entre os projetos '<projectname1>' e '<projectname2>'
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: ffc6b3c180c86abe272d56d0ecf3042d8181da59
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870897"
---
# <a name="reference-required-to-assembly-assemblyidentity-containing-type-typename-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-projectname1-and-projectname2"></a><span data-ttu-id="96407-102">Referência obrigatória ao assembly '\<assemblyidentity>' contendo o tipo '\<typename>', mas não foi possível localizar uma referência adequada devido à ambiguidade entre os projetos '\<projectname1>' e '\<projectname2>'</span><span class="sxs-lookup"><span data-stu-id="96407-102">Reference required to assembly '\<assemblyidentity>' containing type '\<typename>', but a suitable reference could not be found due to ambiguity between projects '\<projectname1>' and '\<projectname2>'</span></span>

<span data-ttu-id="96407-103">Uma expressão usa um tipo, como uma classe, estrutura, interface, enumeração ou delegado, que é definido fora do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="96407-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="96407-104">No entanto, você tem referências de projeto para mais de um assembly que define esse tipo.</span><span class="sxs-lookup"><span data-stu-id="96407-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="96407-105">Os projetos citados produzem assemblies com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="96407-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="96407-106">Portanto, o compilador não pode determinar qual assembly usar para o tipo que você está acessando.</span><span class="sxs-lookup"><span data-stu-id="96407-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="96407-107">Para acessar um tipo definido em outro assembly, o compilador Visual Basic deve ter uma referência a esse assembly.</span><span class="sxs-lookup"><span data-stu-id="96407-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="96407-108">Essa deve ser uma referência única e não ambígua que não cause referências circulares entre projetos.</span><span class="sxs-lookup"><span data-stu-id="96407-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="96407-109">**ID do erro:** BC30969</span><span class="sxs-lookup"><span data-stu-id="96407-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96407-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="96407-110">To correct this error</span></span>  
  
1. <span data-ttu-id="96407-111">Determine qual projeto produz o melhor assembly para referência do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="96407-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="96407-112">Para essa decisão, você pode usar critérios como a facilidade de acesso a arquivos e a frequência de atualizações.</span><span class="sxs-lookup"><span data-stu-id="96407-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2. <span data-ttu-id="96407-113">Nas propriedades do projeto, adicione uma referência ao arquivo que contém o assembly que define o tipo que você está usando.</span><span class="sxs-lookup"><span data-stu-id="96407-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96407-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="96407-114">See also</span></span>

- [<span data-ttu-id="96407-115">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="96407-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="96407-116">Referências a elementos declarados</span><span class="sxs-lookup"><span data-stu-id="96407-116">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="96407-117">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="96407-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="96407-118">Solução de Problemas de Referências Quebradas</span><span class="sxs-lookup"><span data-stu-id="96407-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
