---
title: Criando assemblies
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 583c448bd939cd4d1d16bff372afff4172dcf985
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="creating-assemblies"></a><span data-ttu-id="08416-102">Criando assemblies</span><span class="sxs-lookup"><span data-stu-id="08416-102">Creating Assemblies</span></span>
<span data-ttu-id="08416-103">Você pode criar assemblies de vários arquivos ou um único arquivo usando um IDE, como [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ou outros compiladores e ferramentas fornecidas pelo [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08416-103">You can create single-file or multifile assemblies using an IDE, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], or the compilers and tools provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span> <span data-ttu-id="08416-104">O assembly mais simples é um único arquivo que tem um nome simples e é carregado em um único domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08416-104">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="08416-105">Esse assembly não pode ser referenciado por outros assemblies fora do diretório do aplicativo e não é submetido à verificação de versão.</span><span class="sxs-lookup"><span data-stu-id="08416-105">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="08416-106">Para desinstalar o aplicativo composto do assembly, você simplesmente exclui o diretório em que ele reside.</span><span class="sxs-lookup"><span data-stu-id="08416-106">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="08416-107">Para muitos desenvolvedores, um assembly com esses recursos é tudo o que é necessário para implantar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08416-107">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>  
  
 <span data-ttu-id="08416-108">Você pode criar um assembly de vários arquivos de vários módulos de código e arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="08416-108">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="08416-109">Você também pode criar um assembly que pode ser compartilhado por vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="08416-109">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="08416-110">Um assembly compartilhado deve ter um nome forte e pode ser implantado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="08416-110">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="08416-111">Você tem várias opções ao agrupar módulos de código e recursos em assemblies, dependendo dos seguintes fatores:</span><span class="sxs-lookup"><span data-stu-id="08416-111">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>  
  
-   <span data-ttu-id="08416-112">Controle de versão</span><span class="sxs-lookup"><span data-stu-id="08416-112">Versioning</span></span>  
  
     <span data-ttu-id="08416-113">Agrupe módulos que devem ter as mesmas informações de versão.</span><span class="sxs-lookup"><span data-stu-id="08416-113">Group modules that should have the same version information.</span></span>  
  
-   <span data-ttu-id="08416-114">Implantação</span><span class="sxs-lookup"><span data-stu-id="08416-114">Deployment</span></span>  
  
     <span data-ttu-id="08416-115">Agrupe recursos e módulos de código que dão suporte ao seu modelo de implantação.</span><span class="sxs-lookup"><span data-stu-id="08416-115">Group code modules and resources that support your model of deployment.</span></span>  
  
-   <span data-ttu-id="08416-116">Reutilização</span><span class="sxs-lookup"><span data-stu-id="08416-116">Reuse</span></span>  
  
     <span data-ttu-id="08416-117">Agrupe os módulos se eles puderem ser usados em conjunto de forma lógica para alguma finalidade.</span><span class="sxs-lookup"><span data-stu-id="08416-117">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="08416-118">Por exemplo, um assembly composto pelos tipos e classes usados com pouca frequência para a manutenção do programa podem ser colocados no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="08416-118">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="08416-119">Além disso, os tipos que você pretende compartilhar com vários aplicativos devem ser agrupados em um assembly e o assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="08416-119">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>  
  
-   <span data-ttu-id="08416-120">Segurança</span><span class="sxs-lookup"><span data-stu-id="08416-120">Security</span></span>  
  
     <span data-ttu-id="08416-121">Agrupe módulos que contêm tipos que exigem as mesmas permissões de segurança.</span><span class="sxs-lookup"><span data-stu-id="08416-121">Group modules containing types that require the same security permissions.</span></span>  
  
-   <span data-ttu-id="08416-122">Definição de escopo</span><span class="sxs-lookup"><span data-stu-id="08416-122">Scoping</span></span>  
  
     <span data-ttu-id="08416-123">Agrupe módulos que contêm tipos cuja visibilidade deve ser restrita ao mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="08416-123">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>  
  
 <span data-ttu-id="08416-124">Devem ser feitas considerações especiais ao disponibilizar assemblies de Common Language Runtime para aplicativos COM não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="08416-124">Special considerations must be made when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="08416-125">Para obter mais informações sobre como trabalhar com código não gerenciado, consulte [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md) (Expondo componentes do .NET Framework para COM).</span><span class="sxs-lookup"><span data-stu-id="08416-125">For more information about working with unmanaged code, see [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08416-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08416-126">See Also</span></span>  
 <span data-ttu-id="08416-127">[Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="08416-127">[Programming with Assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md) </span></span>  
 <span data-ttu-id="08416-128">[Controle de versão do assembly](../../../docs/framework/app-domains/assembly-versioning.md) </span><span class="sxs-lookup"><span data-stu-id="08416-128">[Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md) </span></span>  
 <span data-ttu-id="08416-129">[Como compilar um assembly de arquivo único](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="08416-129">[How to: Build a Single-File Assembly](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md) </span></span>  
 <span data-ttu-id="08416-130">[Como compilar um assembly de vários arquivos](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="08416-130">[How to: Build a Multifile Assembly](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md) </span></span>  
 <span data-ttu-id="08416-131">[Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="08416-131">[How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md) </span></span>  
 [<span data-ttu-id="08416-132">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="08416-132">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)

