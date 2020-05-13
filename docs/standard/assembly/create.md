---
title: Criar assemblies
description: Saiba como criar assemblies de arquivo único ou de multiarquivos usando um IDE, como o Visual Studio, ou os compiladores e ferramentas fornecidos pelo SDK do Windows.
ms.date: 08/19/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
ms.openlocfilehash: 3e17d6a066d937a161135b8b03c3f9258f3586b0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378521"
---
# <a name="create-assemblies"></a><span data-ttu-id="bc909-103">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="bc909-103">Create assemblies</span></span>

<span data-ttu-id="bc909-104">Você pode criar assemblies de vários arquivos ou um único arquivo usando um IDE, como Visual Studio, ou outros compiladores e ferramentas fornecidos pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="bc909-104">You can create single-file or multifile assemblies using an IDE, such as Visual Studio, or the compilers and tools provided by the Windows SDK.</span></span> <span data-ttu-id="bc909-105">O assembly mais simples é um único arquivo que tem um nome simples e é carregado em um único domínio de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bc909-105">The simplest assembly is a single file that has a simple name and is loaded into a single application domain.</span></span> <span data-ttu-id="bc909-106">Esse assembly não pode ser referenciado por outros assemblies fora do diretório do aplicativo e não é submetido à verificação de versão.</span><span class="sxs-lookup"><span data-stu-id="bc909-106">This assembly cannot be referenced by other assemblies outside the application directory and does not undergo version checking.</span></span> <span data-ttu-id="bc909-107">Para desinstalar o aplicativo composto do assembly, você simplesmente exclui o diretório em que ele reside.</span><span class="sxs-lookup"><span data-stu-id="bc909-107">To uninstall the application made up of the assembly, you simply delete the directory where it resides.</span></span> <span data-ttu-id="bc909-108">Para muitos desenvolvedores, um assembly com esses recursos é tudo o que é necessário para implantar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bc909-108">For many developers, an assembly with these features is all that is needed to deploy an application.</span></span>

<span data-ttu-id="bc909-109">Você pode criar um assembly de vários arquivos de vários módulos de código e arquivos de recurso.</span><span class="sxs-lookup"><span data-stu-id="bc909-109">You can create a multifile assembly from several code modules and resource files.</span></span> <span data-ttu-id="bc909-110">Você também pode criar um assembly que pode ser compartilhado por vários aplicativos.</span><span class="sxs-lookup"><span data-stu-id="bc909-110">You can also create an assembly that can be shared by multiple applications.</span></span> <span data-ttu-id="bc909-111">Um assembly compartilhado deve ter um nome forte e pode ser implantado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="bc909-111">A shared assembly must have a strong name and can be deployed in the global assembly cache.</span></span>

<span data-ttu-id="bc909-112">Você tem várias opções ao agrupar módulos de código e recursos em assemblies, dependendo dos seguintes fatores:</span><span class="sxs-lookup"><span data-stu-id="bc909-112">You have several options when grouping code modules and resources into assemblies, depending on the following factors:</span></span>

- <span data-ttu-id="bc909-113">Controle de versão</span><span class="sxs-lookup"><span data-stu-id="bc909-113">Versioning</span></span>

     <span data-ttu-id="bc909-114">Agrupe módulos que devem ter as mesmas informações de versão.</span><span class="sxs-lookup"><span data-stu-id="bc909-114">Group modules that should have the same version information.</span></span>

- <span data-ttu-id="bc909-115">Implantação</span><span class="sxs-lookup"><span data-stu-id="bc909-115">Deployment</span></span>

     <span data-ttu-id="bc909-116">Agrupe recursos e módulos de código que dão suporte ao seu modelo de implantação.</span><span class="sxs-lookup"><span data-stu-id="bc909-116">Group code modules and resources that support your model of deployment.</span></span>

- <span data-ttu-id="bc909-117">Reutilização</span><span class="sxs-lookup"><span data-stu-id="bc909-117">Reuse</span></span>

     <span data-ttu-id="bc909-118">Agrupe os módulos se eles puderem ser usados em conjunto de forma lógica para alguma finalidade.</span><span class="sxs-lookup"><span data-stu-id="bc909-118">Group modules if they can be logically used together for some purpose.</span></span> <span data-ttu-id="bc909-119">Por exemplo, um assembly composto pelos tipos e classes usados com pouca frequência para a manutenção do programa podem ser colocados no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="bc909-119">For example, an assembly consisting of types and classes used infrequently for program maintenance can be put in the same assembly.</span></span> <span data-ttu-id="bc909-120">Além disso, os tipos que você pretende compartilhar com vários aplicativos devem ser agrupados em um assembly e o assembly deve ser assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="bc909-120">In addition, types that you intend to share with multiple applications should be grouped into an assembly and the assembly should be signed with a strong name.</span></span>

- <span data-ttu-id="bc909-121">Segurança</span><span class="sxs-lookup"><span data-stu-id="bc909-121">Security</span></span>

     <span data-ttu-id="bc909-122">Agrupe módulos que contêm tipos que exigem as mesmas permissões de segurança.</span><span class="sxs-lookup"><span data-stu-id="bc909-122">Group modules containing types that require the same security permissions.</span></span>

- <span data-ttu-id="bc909-123">Scoping</span><span class="sxs-lookup"><span data-stu-id="bc909-123">Scoping</span></span>

     <span data-ttu-id="bc909-124">Agrupe módulos que contêm tipos cuja visibilidade deve ser restrita ao mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="bc909-124">Group modules containing types whose visibility should be restricted to the same assembly.</span></span>

<span data-ttu-id="bc909-125">Há considerações especiais ao tornar Common Language Runtime assemblies disponíveis para aplicativos COM não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="bc909-125">There are special considerations when making common language runtime assemblies available to unmanaged COM applications.</span></span> <span data-ttu-id="bc909-126">Para obter mais informações sobre como trabalhar com código não gerenciado, consulte [expor .NET Framework Components to com](../../framework/interop/exposing-dotnet-components-to-com.md).</span><span class="sxs-lookup"><span data-stu-id="bc909-126">For more information about working with unmanaged code, see [Expose .NET Framework components to COM](../../framework/interop/exposing-dotnet-components-to-com.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc909-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc909-127">See also</span></span>

- [<span data-ttu-id="bc909-128">Controle de versão do assembly</span><span class="sxs-lookup"><span data-stu-id="bc909-128">Assembly versioning</span></span>](versioning.md)
- [<span data-ttu-id="bc909-129">Como: criar um assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="bc909-129">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)
- [<span data-ttu-id="bc909-130">Como: criar um assembly de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="bc909-130">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)
- [<span data-ttu-id="bc909-131">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="bc909-131">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="bc909-132">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="bc909-132">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)
