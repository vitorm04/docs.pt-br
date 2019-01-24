---
title: '&lt;mensagem&gt; esse erro também pode ser devido à mistura de uma referência de arquivo com uma referência de projeto ao assembly &#39; &lt;assemblyname&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
ms.openlocfilehash: d4fb2a8985a21ecea5056b83d2766e8dc468180d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528986"
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="9bd00-102">&lt;mensagem&gt; esse erro também pode ser devido à mistura de uma referência de arquivo com uma referência de projeto ao assembly &#39; &lt;assemblyname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="9bd00-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="9bd00-103">\<mensagem > Esse erro também pode ser devido à mistura de uma referência de arquivo com uma referência de projeto ao assembly '\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="9bd00-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="9bd00-104">Nesse caso, tente substituir a referência de arquivo para '\<assemblyfilename >' no projeto '\<projectname1 >' com uma referência de projeto a '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="9bd00-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="9bd00-105">O código em seu projeto acessa um membro de outro projeto, mas a configuração de sua solução não permite que o compilador do Visual Basic resolver a referência.</span><span class="sxs-lookup"><span data-stu-id="9bd00-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the Visual Basic compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="9bd00-106">Para acessar um tipo definido em outro assembly, o compilador do Visual Basic deve ter uma referência a esse assembly.</span><span class="sxs-lookup"><span data-stu-id="9bd00-106">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="9bd00-107">Isso deve ser uma referência única e não ambígua, que não faz com que referências circulares entre projetos.</span><span class="sxs-lookup"><span data-stu-id="9bd00-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="9bd00-108">**ID do erro:** BC30971</span><span class="sxs-lookup"><span data-stu-id="9bd00-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9bd00-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9bd00-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="9bd00-110">Determine qual projeto produz o melhor conjunto para o seu projeto para fazer referência.</span><span class="sxs-lookup"><span data-stu-id="9bd00-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="9bd00-111">Para essa decisão, você pode usar critérios, como a facilidade de acesso de arquivo e a frequência de atualizações.</span><span class="sxs-lookup"><span data-stu-id="9bd00-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="9bd00-112">Nas propriedades do projeto, adicione uma referência ao projeto que contém o assembly que define o tipo que você está usando.</span><span class="sxs-lookup"><span data-stu-id="9bd00-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd00-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd00-113">See also</span></span>
- [<span data-ttu-id="9bd00-114">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="9bd00-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="9bd00-115">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="9bd00-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

- [<span data-ttu-id="9bd00-116">Gerenciando propriedades de solução e de projeto</span><span class="sxs-lookup"><span data-stu-id="9bd00-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="9bd00-117">Solução de Problemas de Referências Quebradas</span><span class="sxs-lookup"><span data-stu-id="9bd00-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
