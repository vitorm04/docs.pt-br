---
title: O valor do tipo '<typename1>' não pode ser convertido em '<typename2>' (várias referências ao arquivo)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: e394459e7d25d38e27e78f10dd547cb9ebd6230d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261341"
---
# <a name="value-of-type-typename1-cannot-be-converted-to-typename2-multiple-file-references"></a><span data-ttu-id="fa55a-102">Valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >' (várias referências de arquivo)</span><span class="sxs-lookup"><span data-stu-id="fa55a-102">Value of type '\<typename1>' cannot be converted to '\<typename2>' (Multiple file references)</span></span>
<span data-ttu-id="fa55a-103">Valor do tipo '\<typename1 >' não pode ser convertido em '\<typename2 >'.</span><span class="sxs-lookup"><span data-stu-id="fa55a-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="fa55a-104">Incompatibilidade de tipo pode ser devido a combinação de uma referência de arquivo para '\<filepath1 >' no projeto '\<projectname1 >' com uma referência de arquivo para '\<filepath2 >' no projeto '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="fa55a-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="fa55a-105">Se os dois assemblies forem idênticos, tente substituir essas referências para que ambas as referências são do mesmo local.</span><span class="sxs-lookup"><span data-stu-id="fa55a-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="fa55a-106">Em uma situação em que um projeto faz mais de uma referência de arquivo para um assembly, o compilador não pode garantir que um tipo pode ser convertido para outro.</span><span class="sxs-lookup"><span data-stu-id="fa55a-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="fa55a-107">Cada referência de arquivo Especifica um caminho de arquivo e um nome para o arquivo de saída de um projeto (geralmente um arquivo DLL).</span><span class="sxs-lookup"><span data-stu-id="fa55a-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="fa55a-108">O compilador não pode garantir que os arquivos de saída provenientes da mesma fonte ou que eles representam a mesma versão do mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="fa55a-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="fa55a-109">Portanto, ele não pode garantir que os tipos em referências diferentes são do mesmo tipo, ou que um deles pode ser convertido para outro.</span><span class="sxs-lookup"><span data-stu-id="fa55a-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="fa55a-110">Se você souber que os assemblies referenciados têm a mesma identidade de assembly, você pode usar uma referência de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="fa55a-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="fa55a-111">O *identidade de assembly* inclui nome, versão, se houver de chave pública e cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="fa55a-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="fa55a-112">Essas informações identificam exclusivamente o assembly.</span><span class="sxs-lookup"><span data-stu-id="fa55a-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="fa55a-113">**ID do erro:** BC30961</span><span class="sxs-lookup"><span data-stu-id="fa55a-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa55a-114">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="fa55a-114">To correct this error</span></span>  
  
-   <span data-ttu-id="fa55a-115">Se os assemblies referenciados tiverem a mesma identidade de assembly, em seguida, remover ou substituir uma das referências de arquivo para que haja apenas uma referência de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="fa55a-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="fa55a-116">Se os assemblies referenciados não têm a mesma identidade de assembly, altere seu código para que ele não tenta converter um tipo em um a um tipo em outro.</span><span class="sxs-lookup"><span data-stu-id="fa55a-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa55a-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa55a-117">See also</span></span>
- [<span data-ttu-id="fa55a-118">Conversões de tipo no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa55a-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="fa55a-119">Gerenciando referências em um projeto</span><span class="sxs-lookup"><span data-stu-id="fa55a-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)

