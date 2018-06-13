---
title: Programação com assemblies
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a20a2e678c10157fed7da6f5de9f3ffee0c9ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751864"
---
# <a name="programming-with-assemblies"></a><span data-ttu-id="47c45-102">Programação com assemblies</span><span class="sxs-lookup"><span data-stu-id="47c45-102">Programming with Assemblies</span></span>
<span data-ttu-id="47c45-103">Os assemblies são os blocos de construção do .NET Framework; eles formam a unidade fundamental de implantação, controle de versão, reutilização, escopo de ativação e permissões de segurança.</span><span class="sxs-lookup"><span data-stu-id="47c45-103">Assemblies are the building blocks of the .NET Framework; they form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions.</span></span> <span data-ttu-id="47c45-104">Um assembly oferece ao Common Language Runtime as informações de que ele precisa para estar ciente das implementações de tipo.</span><span class="sxs-lookup"><span data-stu-id="47c45-104">An assembly provides the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="47c45-105">Trata-se de uma coleção de tipos e recursos compilados para trabalharem juntos e formar uma unidade lógica de funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="47c45-105">It is a collection of types and resources that are built to work together and form a logical unit of functionality.</span></span> <span data-ttu-id="47c45-106">Para o tempo de execução, um tipo não existe fora do contexto de um assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-106">To the runtime, a type does not exist outside the context of an assembly.</span></span>  
  
 <span data-ttu-id="47c45-107">Esta seção descreve como criar módulos, criar assemblies usando módulos, criar um par de chaves e assinar um assembly com um nome forte, bem como instalar um assembly no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="47c45-107">This section describes how to create modules, create assemblies from modules, create a key pair and sign an assembly with a strong name, and install an assembly into the global assembly cache.</span></span> <span data-ttu-id="47c45-108">Além disso, esta seção descreve como usar o [Desmontador de MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para exibir informações do manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-108">In addition, this section describes how to use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view assembly manifest information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47c45-109">A partir do .NET Framework versão 2.0, o tempo de execução não carregará um assembly que foi compilado com uma versão do .NET Framework que tenha um número de versão mais alto do que o tempo de execução atualmente carregado.</span><span class="sxs-lookup"><span data-stu-id="47c45-109">Starting with the .NET Framework version 2.0, the runtime will not load an assembly that was compiled with a version of the .NET Framework that has a higher version number than the currently loaded runtime.</span></span> <span data-ttu-id="47c45-110">Isso vale para a combinação dos componentes principal e secundário do número de versão.</span><span class="sxs-lookup"><span data-stu-id="47c45-110">This applies to the combination of the major and minor components of the version number.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="47c45-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="47c45-111">In This Section</span></span>  
 [<span data-ttu-id="47c45-112">Criação de assemblies</span><span class="sxs-lookup"><span data-stu-id="47c45-112">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 <span data-ttu-id="47c45-113">Fornece uma visão geral dos assemblies de arquivo único e vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="47c45-113">Provides an overview of single-file and multifile assemblies.</span></span>  
  
 [<span data-ttu-id="47c45-114">Nomes de assembly</span><span class="sxs-lookup"><span data-stu-id="47c45-114">Assembly Names</span></span>](../../../docs/framework/app-domains/assembly-names.md)  
 <span data-ttu-id="47c45-115">Fornece uma visão geral da nomenclatura de assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-115">Provides an overview of assembly naming.</span></span>  
  
 [<span data-ttu-id="47c45-116">Como determinar o nome totalmente qualificado de um assembly</span><span class="sxs-lookup"><span data-stu-id="47c45-116">How to: Determine an Assembly's Fully Qualified Name</span></span>](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 <span data-ttu-id="47c45-117">Descreve como determinar o nome totalmente qualificado de um assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-117">Describes how to determine the fully qualified name of an assembly.</span></span>  
  
 [<span data-ttu-id="47c45-118">Execução de aplicativos de intranet em confiança total</span><span class="sxs-lookup"><span data-stu-id="47c45-118">Running Intranet Applications in Full Trust</span></span>](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 <span data-ttu-id="47c45-119">Descreve como especificar a política de segurança herdada para assemblies de confiança total em um compartilhamento de intranet.</span><span class="sxs-lookup"><span data-stu-id="47c45-119">Describes how to specify legacy security policy for full-trust assemblies on an intranet share.</span></span>  
  
 [<span data-ttu-id="47c45-120">Local do assembly</span><span class="sxs-lookup"><span data-stu-id="47c45-120">Assembly Location</span></span>](../../../docs/framework/app-domains/assembly-location.md)  
 <span data-ttu-id="47c45-121">Fornece uma visão geral de onde localizar assemblies.</span><span class="sxs-lookup"><span data-stu-id="47c45-121">Provides an overview of where to locate assemblies.</span></span>  
  
 [<span data-ttu-id="47c45-122">Como compilar um assembly de arquivo único</span><span class="sxs-lookup"><span data-stu-id="47c45-122">How to: Build a Single-File Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 <span data-ttu-id="47c45-123">Descreve como criar um assembly de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="47c45-123">Describes how to create a single-file assembly.</span></span>  
  
 [<span data-ttu-id="47c45-124">Assemblies de vários arquivos</span><span class="sxs-lookup"><span data-stu-id="47c45-124">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 <span data-ttu-id="47c45-125">Descreve os motivos para a criação de assemblies de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="47c45-125">Describes reasons for creating multifile assemblies.</span></span>  
  
 [<span data-ttu-id="47c45-126">Como Compilar um Assembly de Vários Arquivos</span><span class="sxs-lookup"><span data-stu-id="47c45-126">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 <span data-ttu-id="47c45-127">Descreve como criar um assembly de vários arquivos.</span><span class="sxs-lookup"><span data-stu-id="47c45-127">Describes how to create a multifile assembly.</span></span>  
  
 [<span data-ttu-id="47c45-128">Configuração de atributos de assembly</span><span class="sxs-lookup"><span data-stu-id="47c45-128">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 <span data-ttu-id="47c45-129">Descreve os atributos de assembly e como defini-los.</span><span class="sxs-lookup"><span data-stu-id="47c45-129">Describes assembly attributes and how to set them.</span></span>  
  
 [<span data-ttu-id="47c45-130">Criando e usando assemblies com nome forte</span><span class="sxs-lookup"><span data-stu-id="47c45-130">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 <span data-ttu-id="47c45-131">Descreve como e por que assinar um assembly com um nome forte, além de inclui tópicos explicativos.</span><span class="sxs-lookup"><span data-stu-id="47c45-131">Describes how and why you sign an assembly with a strong name, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="47c45-132">Assinar um assembly com atraso</span><span class="sxs-lookup"><span data-stu-id="47c45-132">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 <span data-ttu-id="47c45-133">Descreve como assinar um assembly com atraso.</span><span class="sxs-lookup"><span data-stu-id="47c45-133">Describes how to delay-sign an assembly.</span></span>  
  
 [<span data-ttu-id="47c45-134">Como trabalhar com assemblies e o cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="47c45-134">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 <span data-ttu-id="47c45-135">Descreve como e por que adicionar assemblies ao cache de assembly global, além de incluir tópicos explicativos.</span><span class="sxs-lookup"><span data-stu-id="47c45-135">Describes how and why you add assemblies to the global assembly cache, and includes how-to topics.</span></span>  
  
 [<span data-ttu-id="47c45-136">Como exibir o conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="47c45-136">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 <span data-ttu-id="47c45-137">Descreve como usar o Desmontador de MSIL (Ildasm.exe) para exibir o conteúdo do assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-137">Describes how to use the MSIL Disassembler (Ildasm.exe) to view assembly contents.</span></span>  
  
 [<span data-ttu-id="47c45-138">Encaminhamento de tipo no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="47c45-138">Type Forwarding in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 <span data-ttu-id="47c45-139">Descreve como usar encaminhamento de tipo para mover um tipo para um assembly diferente sem interromper aplicativos existentes.</span><span class="sxs-lookup"><span data-stu-id="47c45-139">Describes how to use type forwarding to move a type into a different assembly without breaking existing applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="47c45-140">Referência</span><span class="sxs-lookup"><span data-stu-id="47c45-140">Reference</span></span>  
 <xref:System.Reflection.Assembly>  
 <span data-ttu-id="47c45-141">A classe do .NET Framework que representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-141">The .NET Framework class that represents an assembly.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="47c45-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="47c45-142">Related Sections</span></span>  
 [<span data-ttu-id="47c45-143">Como obter as informações de tipo e membro de um assembly</span><span class="sxs-lookup"><span data-stu-id="47c45-143">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="47c45-144">Descreve como obter de modo programático o tipo e outras informações de um assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-144">Describes how to programmatically obtain type and other information from an assembly.</span></span>  
  
 [<span data-ttu-id="47c45-145">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="47c45-145">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="47c45-146">Fornece uma visão geral conceitual dos assemblies de Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="47c45-146">Provides a conceptual overview of common language runtime assemblies.</span></span>  
  
 [<span data-ttu-id="47c45-147">Controle de versão do assembly</span><span class="sxs-lookup"><span data-stu-id="47c45-147">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 <span data-ttu-id="47c45-148">Fornece uma visão geral de associação de assembly e dos atributos <xref:System.Reflection.AssemblyVersionAttribute> e <xref:System.Reflection.AssemblyInformationalVersionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="47c45-148">Provides an overview of assembly binding and of the <xref:System.Reflection.AssemblyVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes.</span></span>  
  
 [<span data-ttu-id="47c45-149">Como o tempo de execução localiza assemblies</span><span class="sxs-lookup"><span data-stu-id="47c45-149">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 <span data-ttu-id="47c45-150">Descreve como o tempo de execução determina qual assembly usar para atender a uma solicitação de associação.</span><span class="sxs-lookup"><span data-stu-id="47c45-150">Describes how the runtime determines which assembly to use to fulfill a binding request.</span></span>  
  
 [<span data-ttu-id="47c45-151">Reflexão</span><span class="sxs-lookup"><span data-stu-id="47c45-151">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="47c45-152">Descreve como usar a classe **Reflection** para obter informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="47c45-152">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
