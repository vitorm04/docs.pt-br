---
title: Programar com assemblies
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
ms.openlocfilehash: 9f07d36d9e47189d53e367fd1406e5684c024aa3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107062"
---
# <a name="program-with-assemblies"></a><span data-ttu-id="5a300-102">Programar com assemblies</span><span class="sxs-lookup"><span data-stu-id="5a300-102">Program with assemblies</span></span>
<span data-ttu-id="5a300-103">Os assemblies são os blocos de construção do .NET Framework; eles formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança.</span><span class="sxs-lookup"><span data-stu-id="5a300-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="5a300-104">Um assembly oferece ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo.</span><span class="sxs-lookup"><span data-stu-id="5a300-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="5a300-105">Trata-se de uma coleção de tipos e recursos compilados para trabalharem juntos e formar uma unidade lógica de funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="5a300-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="5a300-106">Para o runtime, um tipo não existe fora do contexto de um assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="5a300-107">Esta seção descreve como criar módulos, criar assemblies usando módulos, criar um par de chaves e assinar um assembly com um nome forte, bem como instalar um assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="5a300-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="5a300-108">Além disso, esta seção descreve como usar o [Desmontador de MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) para exibir informações do manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a300-109">A partir do .NET Framework versão 2.0, o runtime não carregará um assembly que foi compilado com uma versão do .NET Framework que tenha um número de versão mais alto do que o runtime atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="5a300-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="5a300-110">Isso vale para a combinação dos componentes principal e secundário do número de versão.</span><span class="sxs-lookup"><span data-stu-id="5a300-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a300-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5a300-111">In this section</span></span>  
 [<span data-ttu-id="5a300-112">Criar assemblies</span><span class="sxs-lookup"><span data-stu-id="5a300-112">Create assemblies</span></span>](create.md)  
 <span data-ttu-id="5a300-113">Fornece uma visão geral dos assemblies de arquivo único e vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="5a300-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="5a300-114">Nomes de assembly</span><span class="sxs-lookup"><span data-stu-id="5a300-114">Assembly names</span></span>](names.md)  
 <span data-ttu-id="5a300-115">Fornece uma visão geral da nomenclatura de assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="5a300-116">Como determinar o nome totalmente qualificado de um assembly</span><span class="sxs-lookup"><span data-stu-id="5a300-116">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)  
 <span data-ttu-id="5a300-117">Descreve como determinar o nome totalmente qualificado de um assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="5a300-118">Executar aplicativos de intranet com confiança total</span><span class="sxs-lookup"><span data-stu-id="5a300-118">Run intranet applications in full trust</span></span>](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="5a300-119">Descreve como especificar a política de segurança herdada para assemblies de confiança total em um compartilhamento de intranet.</span><span class="sxs-lookup"><span data-stu-id="5a300-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="5a300-120">Local do assembly</span><span class="sxs-lookup"><span data-stu-id="5a300-120">Assembly location</span></span>](location.md)  
 <span data-ttu-id="5a300-121">Fornece uma visão geral de onde localizar assemblies.</span><span class="sxs-lookup"><span data-stu-id="5a300-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="5a300-122">Como criar um assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="5a300-122">How to: Build a single-file assembly</span></span>](../../framework/app-domains/build-single-file-assembly.md)  
 <span data-ttu-id="5a300-123">Descreve como criar um assembly de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="5a300-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="5a300-124">Assemblies de multiarquivo</span><span class="sxs-lookup"><span data-stu-id="5a300-124">Multifile assemblies</span></span>](../../framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="5a300-125">Descreve os motivos para a criação de assemblies de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="5a300-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="5a300-126">Como compilar um assembly de multiarquivos</span><span class="sxs-lookup"><span data-stu-id="5a300-126">How to: Build a multifile assembly</span></span>](../../framework/app-domains/build-multifile-assembly.md)  
 <span data-ttu-id="5a300-127">Descreve como criar um assembly de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="5a300-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="5a300-128">Definir atributos de assembly</span><span class="sxs-lookup"><span data-stu-id="5a300-128">Set assembly attributes</span></span>](set-attributes.md)  
 <span data-ttu-id="5a300-129">Descreve os atributos de assembly e como defini-los.</span><span class="sxs-lookup"><span data-stu-id="5a300-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="5a300-130">Criar e usar assemblies de nome forte</span><span class="sxs-lookup"><span data-stu-id="5a300-130">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)  
 <span data-ttu-id="5a300-131">Descreve como e por que assinar um assembly com um nome forte, além de inclui tópicos explicativos.</span><span class="sxs-lookup"><span data-stu-id="5a300-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="5a300-132">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="5a300-132">Delay-sign an assembly</span></span>](delay-sign.md)  
 <span data-ttu-id="5a300-133">Descreve como assinar um assembly com atraso.</span><span class="sxs-lookup"><span data-stu-id="5a300-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="5a300-134">Trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="5a300-134">Work with assemblies and the global assembly cache</span></span>](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="5a300-135">Descreve como e por que adicionar assemblies ao cache de assembly global, além de incluir tópicos explicativos.</span><span class="sxs-lookup"><span data-stu-id="5a300-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="5a300-136">Como exibir o conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="5a300-136">How to: View assembly contents</span></span>](view-contents.md)  
 <span data-ttu-id="5a300-137">Descreve como usar o Desmontador de MSIL (Ildasm.exe) para exibir o conteúdo do assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="5a300-138">Encaminhamento de tipo no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="5a300-138">Type forwarding in the common language runtime</span></span>](type-forwarding.md)  
 <span data-ttu-id="5a300-139">Descreve como usar encaminhamento de tipo para mover um tipo para um assembly diferente sem interromper aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="5a300-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5a300-140">Referência</span><span class="sxs-lookup"><span data-stu-id="5a300-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="5a300-141">A classe do .NET Framework que representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a300-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="5a300-142">Related sections</span></span>  
 [<span data-ttu-id="5a300-143">Como obter informações de tipo e membro de um assembly</span><span class="sxs-lookup"><span data-stu-id="5a300-143">How to: Obtain type and member information from an assembly</span></span>](../../framework/reflection-and-codedom/get-type-member-information.md)  
 <span data-ttu-id="5a300-144">Descreve como obter de modo programático o tipo e outras informações de um assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="5a300-145">Assemblies no .NET</span><span class="sxs-lookup"><span data-stu-id="5a300-145">Assemblies in .NET</span></span>](index.md)  
 <span data-ttu-id="5a300-146">Fornece uma visão geral conceitual dos assemblies de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="5a300-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="5a300-147">Controle de versão do assembly</span><span class="sxs-lookup"><span data-stu-id="5a300-147">Assembly versioning</span></span>](versioning.md)  
 <span data-ttu-id="5a300-148">Fornece uma visão geral de associação de assembly e dos atributos <xref:System.Reflection.AssemblyVersionAttribute> e <xref:System.Reflection.AssemblyInformationalVersionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5a300-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="5a300-149">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="5a300-149">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="5a300-150">Descreve como o runtime determina qual assembly usar para atender a uma solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="5a300-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 <span data-ttu-id="5a300-151">[Reflexão](../../framework/reflection-and-codedom/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="5a300-151">[Reflection](../../framework/reflection-and-codedom/reflection.md) </span></span>  
 <span data-ttu-id="5a300-152">Descreve como usar a classe **Reflection** para obter informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="5a300-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
