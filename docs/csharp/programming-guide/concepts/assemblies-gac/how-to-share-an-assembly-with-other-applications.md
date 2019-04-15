---
title: 'Como: Compartilhar um assembly com outros aplicativos (C#)'
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314783"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a><span data-ttu-id="6e5e6-102">Como: Compartilhar um assembly com outros aplicativos (C#)</span><span class="sxs-lookup"><span data-stu-id="6e5e6-102">How to: Share an Assembly with Other Applications (C#)</span></span>
<span data-ttu-id="6e5e6-103">Os assemblies podem ser particulares ou compartilhados: por padrão, a maioria dos programas simples consistem em um assembly particular porque eles não se destinam a serem usados por outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="6e5e6-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="6e5e6-104">Para compartilhar um assembly com outros aplicativos, ele deve ser colocado no [GAC](../../../../framework/app-domains/gac.md) (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="6e5e6-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="6e5e6-105">Compartilhando um assembly</span><span class="sxs-lookup"><span data-stu-id="6e5e6-105">Sharing an assembly</span></span>  
  
1. <span data-ttu-id="6e5e6-106">Crie o assembly.</span><span class="sxs-lookup"><span data-stu-id="6e5e6-106">Create your assembly.</span></span> <span data-ttu-id="6e5e6-107">Para obter mais informações, consulte [Criando assemblies](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6e5e6-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2. <span data-ttu-id="6e5e6-108">Atribua um nome forte ao assembly.</span><span class="sxs-lookup"><span data-stu-id="6e5e6-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="6e5e6-109">Para obter mais informações, confira [Como: Assinar um assembly com um nome forte](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="6e5e6-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3. <span data-ttu-id="6e5e6-110">Atribua informações de versão ao assembly.</span><span class="sxs-lookup"><span data-stu-id="6e5e6-110">Assign version information to your assembly.</span></span> <span data-ttu-id="6e5e6-111">Para obter mais informações, consulte [Controle de versão do assembly](../../../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="6e5e6-111">For more information, see [Assembly Versioning](../../../../../docs/framework/app-domains/assembly-versioning.md).</span></span>  
  
4. <span data-ttu-id="6e5e6-112">Adicione o assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="6e5e6-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="6e5e6-113">Para obter mais informações, confira [Como: Instalar um assembly no cache de assembly global](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="6e5e6-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5. <span data-ttu-id="6e5e6-114">Acesse, de outros aplicativos, os tipos contidos no assembly.</span><span class="sxs-lookup"><span data-stu-id="6e5e6-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="6e5e6-115">Para obter mais informações, confira [Como: Referenciar um assembly de nome forte](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="6e5e6-115">For more information, see [How to: Reference a Strong-Named Assembly](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5e6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e5e6-116">See also</span></span>

- [<span data-ttu-id="6e5e6-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6e5e6-117">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6e5e6-118">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="6e5e6-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
