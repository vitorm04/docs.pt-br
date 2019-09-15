---
title: Programa com assemblies
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03babe701b46eab54a76094c4728af80e6d9911e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973134"
---
# <a name="program-with-assemblies"></a><span data-ttu-id="fa6d9-102">Programa com assemblies</span><span class="sxs-lookup"><span data-stu-id="fa6d9-102">Program with assemblies</span></span>
<span data-ttu-id="fa6d9-103">Os assemblies são os blocos de construção do .NET Framework; eles formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="fa6d9-104">Um assembly oferece ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="fa6d9-105">Trata-se de uma coleção de tipos e recursos compilados para trabalharem juntos e formar uma unidade lógica de funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="fa6d9-106">Para o tempo de execução, um tipo não existe fora do contexto de um assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="fa6d9-107">Esta seção descreve como criar módulos, criar assemblies usando módulos, criar um par de chaves e assinar um assembly com um nome forte, bem como instalar um assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="fa6d9-108">Além disso, esta seção descreve como usar o [Desmontador de MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) para exibir informações do manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa6d9-109">A partir do .NET Framework versão 2.0, o tempo de execução não carregará um assembly que foi compilado com uma versão do .NET Framework que tenha um número de versão mais alto do que o tempo de execução atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="fa6d9-110">Isso vale para a combinação dos componentes principal e secundário do número de versão.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa6d9-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="fa6d9-111">In this section</span></span>  
 [<span data-ttu-id="fa6d9-112">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="fa6d9-112">Create assemblies</span></span>](create.md)  
 <span data-ttu-id="fa6d9-113">Fornece uma visão geral dos assemblies de arquivo único e vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="fa6d9-114">Nomes de assembly</span><span class="sxs-lookup"><span data-stu-id="fa6d9-114">Assembly names</span></span>](names.md)  
 <span data-ttu-id="fa6d9-115">Fornece uma visão geral da nomenclatura de assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="fa6d9-116">Como: Determinar o nome totalmente qualificado de um assembly</span><span class="sxs-lookup"><span data-stu-id="fa6d9-116">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)  
 <span data-ttu-id="fa6d9-117">Descreve como determinar o nome totalmente qualificado de um assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="fa6d9-118">Executar aplicativos de intranet com confiança total</span><span class="sxs-lookup"><span data-stu-id="fa6d9-118">Run intranet applications in full trust</span></span>](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="fa6d9-119">Descreve como especificar a política de segurança herdada para assemblies de confiança total em um compartilhamento de intranet.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="fa6d9-120">Local do assembly</span><span class="sxs-lookup"><span data-stu-id="fa6d9-120">Assembly location</span></span>](location.md)  
 <span data-ttu-id="fa6d9-121">Fornece uma visão geral de onde localizar assemblies.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="fa6d9-122">Como: Compilar um assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="fa6d9-122">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)  
 <span data-ttu-id="fa6d9-123">Descreve como criar um assembly de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="fa6d9-124">Assemblies de multiarquivo</span><span class="sxs-lookup"><span data-stu-id="fa6d9-124">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="fa6d9-125">Descreve os motivos para a criação de assemblies de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="fa6d9-126">Como: Compilar um assembly de multiarquivos</span><span class="sxs-lookup"><span data-stu-id="fa6d9-126">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)  
 <span data-ttu-id="fa6d9-127">Descreve como criar um assembly de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="fa6d9-128">Definir atributos de assembly</span><span class="sxs-lookup"><span data-stu-id="fa6d9-128">Set assembly attributes</span></span>](set-attributes.md)  
 <span data-ttu-id="fa6d9-129">Descreve os atributos de assembly e como defini-los.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="fa6d9-130">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="fa6d9-130">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)  
 <span data-ttu-id="fa6d9-131">Descreve como e por que assinar um assembly com um nome forte, além de inclui tópicos explicativos.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="fa6d9-132">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="fa6d9-132">Delay-sign an assembly</span></span>](delay-sign.md)  
 <span data-ttu-id="fa6d9-133">Descreve como assinar um assembly com atraso.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="fa6d9-134">Trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="fa6d9-134">Work with assemblies and the global assembly cache</span></span>](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="fa6d9-135">Descreve como e por que adicionar assemblies ao cache de assembly global, além de incluir tópicos explicativos.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="fa6d9-136">Como: Exibir conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="fa6d9-136">How to: View assembly contents</span></span>](view-contents.md)  
 <span data-ttu-id="fa6d9-137">Descreve como usar o Desmontador de MSIL (Ildasm.exe) para exibir o conteúdo do assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="fa6d9-138">Encaminhamento de tipo no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="fa6d9-138">Type forwarding in the common language runtime</span></span>](type-forwarding.md)  
 <span data-ttu-id="fa6d9-139">Descreve como usar encaminhamento de tipo para mover um tipo para um assembly diferente sem interromper aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fa6d9-140">Referência</span><span class="sxs-lookup"><span data-stu-id="fa6d9-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="fa6d9-141">A classe do .NET Framework que representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fa6d9-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="fa6d9-142">Related sections</span></span>  
 [<span data-ttu-id="fa6d9-143">Como: Obter informações de tipo e membro de um assembly</span><span class="sxs-lookup"><span data-stu-id="fa6d9-143">How to: Obtain type and member information from an assembly</span></span>](../../framework/reflection-and-codedom/get-type-member-information.md)  
 <span data-ttu-id="fa6d9-144">Descreve como obter de modo programático o tipo e outras informações de um assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="fa6d9-145">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="fa6d9-145">Assemblies in .NET</span></span>](index.md)  
 <span data-ttu-id="fa6d9-146">Fornece uma visão geral conceitual dos assemblies de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="fa6d9-147">Controle de versão do assembly</span><span class="sxs-lookup"><span data-stu-id="fa6d9-147">Assembly versioning</span></span>](versioning.md)  
 <span data-ttu-id="fa6d9-148">Fornece uma visão geral de associação de assembly e dos atributos <xref:System.Reflection.AssemblyVersionAttribute> e <xref:System.Reflection.AssemblyInformationalVersionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="fa6d9-149">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="fa6d9-149">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="fa6d9-150">Descreve como o tempo de execução determina qual assembly usar para atender a uma solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 <span data-ttu-id="fa6d9-151">[Reflexão](../../framework/reflection-and-codedom/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="fa6d9-151">[Reflection](../../framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="fa6d9-152">Descreve como usar a classe **Reflection** para obter informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="fa6d9-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
