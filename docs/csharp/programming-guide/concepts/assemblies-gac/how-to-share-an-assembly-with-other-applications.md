---
title: Como compartilhar um assembly com outros aplicativos (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 85117cfdc9b12a93891e89727412a03acc83289b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="e2ca4-102">Como compartilhar um assembly com outros aplicativos (C#)</span><span class="sxs-lookup"><span data-stu-id="e2ca4-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="e2ca4-103">Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e2ca4-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="e2ca4-104">Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](../../../../framework/app-domains/gac.md) (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="e2ca4-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="e2ca4-105">Compartilhando um assembly</span><span class="sxs-lookup"><span data-stu-id="e2ca4-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="e2ca4-106">Crie o assembly.</span><span class="sxs-lookup"><span data-stu-id="e2ca4-106">Create your assembly.</span></span> <span data-ttu-id="e2ca4-107">Para obter mais informações, consulte [Criando assemblies](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="e2ca4-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="e2ca4-108">Atribua um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="e2ca4-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="e2ca4-109">Para obter mais informações, consulte [Como assinar um assembly com um nome forte](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="e2ca4-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="e2ca4-110">Atribua informações de versão ao assembly.</span><span class="sxs-lookup"><span data-stu-id="e2ca4-110">Assign version information to your assembly.</span></span> <span data-ttu-id="e2ca4-111">Para obter mais informações, consulte [Controle de versão do assembly](https://msdn.microsoft.com/library/51ket42z).</span><span class="sxs-lookup"><span data-stu-id="e2ca4-111">For more information, see [Assembly Versioning](https://msdn.microsoft.com/library/51ket42z).</span></span>  
  
4.  <span data-ttu-id="e2ca4-112">Adicione o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="e2ca4-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="e2ca4-113">Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="e2ca4-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="e2ca4-114">Acesse, de outros aplicativos, os tipos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="e2ca4-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="e2ca4-115">Para obter mais informações, consulte [Como referenciar um assembly de nome forte](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="e2ca4-115">For more information, see [How to: Reference a Strong-Named Assembly](http://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ca4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2ca4-116">See Also</span></span>  
 <span data-ttu-id="e2ca4-117">[Guia de Programação em C#](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e2ca4-117">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="e2ca4-118">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="e2ca4-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)

