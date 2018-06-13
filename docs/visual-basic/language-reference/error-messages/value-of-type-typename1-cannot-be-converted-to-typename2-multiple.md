---
title: O valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt; &#39; (várias referências de arquivo)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603685"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="b5285-102">O valor do tipo &#39; &lt;typename1&gt; &#39; não pode ser convertido em &#39; &lt;typename2&gt; &#39; (várias referências de arquivo)</span><span class="sxs-lookup"><span data-stu-id="b5285-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="b5285-103">O valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="b5285-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="b5285-104">Incompatibilidade de tipo pode ser devido à combinação de uma referência de arquivo para '\<filepath1 >' no projeto '\<projectname1 >' com uma referência de arquivo para '\<filepath2 >' no projeto '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="b5285-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="b5285-105">Se os dois assemblies forem idênticos, tente substituir essas referências para que ambas sejam do mesmo local.</span><span class="sxs-lookup"><span data-stu-id="b5285-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="b5285-106">Em uma situação na qual um projeto faz mais de uma referência de arquivo para um assembly, o compilador não pode garantir que um tipo possa ser convertido para outro.</span><span class="sxs-lookup"><span data-stu-id="b5285-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="b5285-107">Cada referência de arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de um projeto (geralmente um arquivo DLL).</span><span class="sxs-lookup"><span data-stu-id="b5285-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="b5285-108">O compilador não pode garantir que os arquivos de saída vêm da mesma origem, ou que eles representam a mesma versão do mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="b5285-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="b5285-109">Portanto, ele não pode garantir que os tipos em referências diferentes são do mesmo tipo ou que um deles pode ser convertido para o outro.</span><span class="sxs-lookup"><span data-stu-id="b5285-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="b5285-110">Se você souber que os assemblies referenciados têm a mesma identidade de assembly, você pode usar uma referência de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="b5285-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="b5285-111">O *identidade de assembly* inclui nome, versão, chave pública, se houver e cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="b5285-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="b5285-112">Essas informações identificam exclusivamente o assembly.</span><span class="sxs-lookup"><span data-stu-id="b5285-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="b5285-113">**ID do erro:** BC30961</span><span class="sxs-lookup"><span data-stu-id="b5285-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5285-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b5285-114">To correct this error</span></span>  
  
-   <span data-ttu-id="b5285-115">Se os assemblies referenciados têm a mesma identidade de assembly, em seguida, remova ou substitua uma das referências de arquivo para que haja apenas uma referência de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="b5285-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="b5285-116">Se os assemblies referenciados não têm a mesma identidade de assembly, altere seu código para que ele não tentará converter um tipo em um tipo em outro.</span><span class="sxs-lookup"><span data-stu-id="b5285-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5285-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5285-117">See Also</span></span>  
 [<span data-ttu-id="b5285-118">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5285-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="b5285-119">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="b5285-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
