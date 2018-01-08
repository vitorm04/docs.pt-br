---
title: Manifesto de um assembly
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 41dc27798e9d39d391e5958b86f691e3a0062582
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-manifest"></a><span data-ttu-id="28ba6-102">Manifesto de um assembly</span><span class="sxs-lookup"><span data-stu-id="28ba6-102">Assembly Manifest</span></span>
<span data-ttu-id="28ba6-103">Cada assembly, seja estático ou dinâmico, contém uma coleção de dados que descreve como os elementos do assembly se relacionam.</span><span class="sxs-lookup"><span data-stu-id="28ba6-103">Every assembly, whether static or dynamic, contains a collection of data that describes how the elements in the assembly relate to each other.</span></span> <span data-ttu-id="28ba6-104">O manifesto do assembly contém esses metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-104">The assembly manifest contains this assembly metadata.</span></span> <span data-ttu-id="28ba6-105">O manifesto de um assembly contém todos os metadados necessários para especificar os requisitos de versão e a identidade de segurança, além de todos os metadados necessários para definir o escopo do assembly e resolver referências a recursos e classes.</span><span class="sxs-lookup"><span data-stu-id="28ba6-105">An assembly manifest contains all the metadata needed to specify the assembly's version requirements and security identity, and all metadata needed to define the scope of the assembly and resolve references to resources and classes.</span></span> <span data-ttu-id="28ba6-106">O manifesto do assembly pode ser armazenado em um arquivo PE (.exe ou .dll) com código MSIL (Microsoft Intermediate Language) ou em um arquivo PE autônomo que contém somente informações do manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-106">The assembly manifest can be stored in either a PE file (an .exe or .dll) with Microsoft intermediate language (MSIL) code or in a standalone PE file that contains only assembly manifest information.</span></span>  
  
 <span data-ttu-id="28ba6-107">A ilustração a seguir mostra as diferentes maneiras nas quais o manifesto pode se armazenado.</span><span class="sxs-lookup"><span data-stu-id="28ba6-107">The following illustration shows the different ways the manifest can be stored.</span></span>  
  
 <span data-ttu-id="28ba6-108">![Um assembly de arquivo único](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span><span class="sxs-lookup"><span data-stu-id="28ba6-108">![A single&#45;file assembly](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")</span></span>  
<span data-ttu-id="28ba6-109">Tipos de assemblies</span><span class="sxs-lookup"><span data-stu-id="28ba6-109">Types of assemblies</span></span>  
  
 <span data-ttu-id="28ba6-110">Para um assembly com um arquivo associado, o manifesto é incorporado ao arquivo PE para formar um assembly de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="28ba6-110">For an assembly with one associated file, the manifest is incorporated into the PE file to form a single-file assembly.</span></span> <span data-ttu-id="28ba6-111">Você pode criar um assembly de vários arquivos com um arquivo de manifesto autônomo ou com o manifesto incorporado a um dos arquivos PE do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-111">You can create a multifile assembly with a standalone manifest file or with the manifest incorporated into one of the PE files in the assembly.</span></span>  
  
 <span data-ttu-id="28ba6-112">Cada manifesto de um assembly executa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="28ba6-112">Each assembly's manifest performs the following functions:</span></span>  
  
-   <span data-ttu-id="28ba6-113">Enumera os arquivos que compõem o assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-113">Enumerates the files that make up the assembly.</span></span>  
  
-   <span data-ttu-id="28ba6-114">Determina como as referências a tipos e recursos do assembly são mapeadas para arquivos que contenham suas declarações e implementações.</span><span class="sxs-lookup"><span data-stu-id="28ba6-114">Governs how references to the assembly's types and resources map to the files that contain their declarations and implementations.</span></span>  
  
-   <span data-ttu-id="28ba6-115">Enumera outros assemblies dos quais o assembly depende.</span><span class="sxs-lookup"><span data-stu-id="28ba6-115">Enumerates other assemblies on which the assembly depends.</span></span>  
  
-   <span data-ttu-id="28ba6-116">Fornece um nível de indireção entre consumidores do assembly e detalhes da implementação do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-116">Provides a level of indirection between consumers of the assembly and the assembly's implementation details.</span></span>  
  
-   <span data-ttu-id="28ba6-117">Renderiza o assembly autodescritivo.</span><span class="sxs-lookup"><span data-stu-id="28ba6-117">Renders the assembly self-describing.</span></span>  
  
## <a name="assembly-manifest-contents"></a><span data-ttu-id="28ba6-118">Conteúdo do manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="28ba6-118">Assembly Manifest Contents</span></span>  
 <span data-ttu-id="28ba6-119">A tabela a seguir mostra as informações contidas no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-119">The following table shows the information contained in the assembly manifest.</span></span> <span data-ttu-id="28ba6-120">Os primeiros quatro itens — informações sobre o nome, o número de versão, a cultura e o nome forte do assembly — compõem a identidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-120">The first four items—the assembly name, version number, culture, and strong name information—make up the assembly's identity.</span></span>  
  
|<span data-ttu-id="28ba6-121">Informações</span><span class="sxs-lookup"><span data-stu-id="28ba6-121">Information</span></span>|<span data-ttu-id="28ba6-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="28ba6-122">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="28ba6-123">Nome do assembly</span><span class="sxs-lookup"><span data-stu-id="28ba6-123">Assembly name</span></span>|<span data-ttu-id="28ba6-124">Uma cadeia de caracteres de texto especificando o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-124">A text string specifying the assembly's name.</span></span>|  
|<span data-ttu-id="28ba6-125">Número de versão</span><span class="sxs-lookup"><span data-stu-id="28ba6-125">Version number</span></span>|<span data-ttu-id="28ba6-126">Um número de versão principal e secundário, além de um número de revisão e de compilação.</span><span class="sxs-lookup"><span data-stu-id="28ba6-126">A major and minor version number, and a revision and build number.</span></span> <span data-ttu-id="28ba6-127">O Common Language Runtime usa esses números para impor uma política de versões.</span><span class="sxs-lookup"><span data-stu-id="28ba6-127">The common language runtime uses these numbers to enforce version policy.</span></span>|  
|<span data-ttu-id="28ba6-128">Cultura</span><span class="sxs-lookup"><span data-stu-id="28ba6-128">Culture</span></span>|<span data-ttu-id="28ba6-129">Informações sobre a cultura ou a linguagem compatível com o assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-129">Information on the culture or language the assembly supports.</span></span> <span data-ttu-id="28ba6-130">Essas informações só devem ser usadas para designar um assembly como um assembly satélite contendo informações específicas de cultura ou de linguagem.</span><span class="sxs-lookup"><span data-stu-id="28ba6-130">This information should be used only to designate an assembly as a satellite assembly containing culture- or language-specific information.</span></span> <span data-ttu-id="28ba6-131">(Um assembly com informações de cultura é automaticamente considerado um assembly satélite.)</span><span class="sxs-lookup"><span data-stu-id="28ba6-131">(An assembly with culture information is automatically assumed to be a satellite assembly.)</span></span>|  
|<span data-ttu-id="28ba6-132">Informações sobre nome forte</span><span class="sxs-lookup"><span data-stu-id="28ba6-132">Strong name information</span></span>|<span data-ttu-id="28ba6-133">A chave pública do editor, caso tenha sido dado ao assembly um nome forte.</span><span class="sxs-lookup"><span data-stu-id="28ba6-133">The public key from the publisher if the assembly has been given a strong name.</span></span>|  
|<span data-ttu-id="28ba6-134">Lista de todos os arquivos no assembly</span><span class="sxs-lookup"><span data-stu-id="28ba6-134">List of all files in the assembly</span></span>|<span data-ttu-id="28ba6-135">Um hash de cada arquivo contido no assembly e um nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="28ba6-135">A hash of each file contained in the assembly and a file name.</span></span> <span data-ttu-id="28ba6-136">Observe que todos os arquivos que compõem o assembly devem estar no mesmo diretório que o arquivo que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-136">Note that all files that make up the assembly must be in the same directory as the file containing the assembly manifest.</span></span>|  
|<span data-ttu-id="28ba6-137">Informações de referência de tipo</span><span class="sxs-lookup"><span data-stu-id="28ba6-137">Type reference information</span></span>|<span data-ttu-id="28ba6-138">Informações usadas pelo ambiente de execução para mapear a referência de um tipo para o arquivo que contém sua declaração e implementação.</span><span class="sxs-lookup"><span data-stu-id="28ba6-138">Information used by the runtime to map a type reference to the file that contains its declaration and implementation.</span></span> <span data-ttu-id="28ba6-139">Usado em tipos que são exportados do assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-139">This is used for types that are exported from the assembly.</span></span>|  
|<span data-ttu-id="28ba6-140">Informações sobre assemblies referenciados</span><span class="sxs-lookup"><span data-stu-id="28ba6-140">Information on referenced assemblies</span></span>|<span data-ttu-id="28ba6-141">Uma lista de outros assemblies que são referenciados estaticamente pelo assembly.</span><span class="sxs-lookup"><span data-stu-id="28ba6-141">A list of other assemblies that are statically referenced by the assembly.</span></span> <span data-ttu-id="28ba6-142">Cada referência inclui o nome do assembly dependente, metadados do assembly (versão, cultura, sistema operacional etc.) e chave pública, caso o assembly possua um nome forte.</span><span class="sxs-lookup"><span data-stu-id="28ba6-142">Each reference includes the dependent assembly's name, assembly metadata (version, culture, operating system, and so on), and public key, if the assembly is strong named.</span></span>|  
  
 <span data-ttu-id="28ba6-143">Você pode adicionar ou alterar informações do manifesto do assembly usando os atributos do assembly em seu código.</span><span class="sxs-lookup"><span data-stu-id="28ba6-143">You can add or change some information in the assembly manifest by using assembly attributes in your code.</span></span> <span data-ttu-id="28ba6-144">Você pode alterar informações sobre versão e atributos informativos, incluindo marca comercial, direitos autorais, produto, empresa e versão informativa.</span><span class="sxs-lookup"><span data-stu-id="28ba6-144">You can change version information and informational attributes, including Trademark, Copyright, Product, Company, and Informational Version.</span></span> <span data-ttu-id="28ba6-145">Para obter uma lista completa dos atributos do assembly, confira [Configuração de atributos de assembly](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="28ba6-145">For a complete list of assembly attributes, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ba6-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28ba6-146">See Also</span></span>  
 [<span data-ttu-id="28ba6-147">Conteúdo do assembly</span><span class="sxs-lookup"><span data-stu-id="28ba6-147">Assembly Contents</span></span>](../../../docs/framework/app-domains/assembly-contents.md)  
 [<span data-ttu-id="28ba6-148">Controle de versão do assembly</span><span class="sxs-lookup"><span data-stu-id="28ba6-148">Assembly Versioning</span></span>](../../../docs/framework/app-domains/assembly-versioning.md)  
 [<span data-ttu-id="28ba6-149">Criando assemblies satélite</span><span class="sxs-lookup"><span data-stu-id="28ba6-149">Creating Satellite Assemblies</span></span>](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [<span data-ttu-id="28ba6-150">Assemblies de nomes fortes</span><span class="sxs-lookup"><span data-stu-id="28ba6-150">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
