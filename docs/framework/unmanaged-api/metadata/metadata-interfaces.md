---
title: Interfaces de metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 638727dae1f0f32e5c92c0da7513719bd11ae8d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="metadata-interfaces"></a><span data-ttu-id="e5ce5-102">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="e5ce5-102">Metadata Interfaces</span></span>
<span data-ttu-id="e5ce5-103">Esta seção descreve as interfaces não gerenciadas que fornecem acesso aos metadados expostos por tipos do .NET Framework, métodos, campos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5ce5-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e5ce5-104">In This Section</span></span>  
 [<span data-ttu-id="e5ce5-105">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="e5ce5-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="e5ce5-106">Fornece métodos para compilação de código dinâmico.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="e5ce5-107">Interface IHostFilter</span><span class="sxs-lookup"><span data-stu-id="e5ce5-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="e5ce5-108">Fornece um método para o host de tempo de execução marcar os tokens de metadados para processamento.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="e5ce5-109">Interface IMapToken</span><span class="sxs-lookup"><span data-stu-id="e5ce5-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="e5ce5-110">Fornece recursos de mapeamento entre importados e emitidos assinaturas de metadados.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="e5ce5-111">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="e5ce5-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="e5ce5-112">Fornece métodos que suportam o modelo de descrição Self usado pelo common language runtime (CLR) para resolver e consomem recursos.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="e5ce5-113">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="e5ce5-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="e5ce5-114">Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="e5ce5-115">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="e5ce5-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="e5ce5-116">Fornece métodos para mapear as bibliotecas de tipo para suas assinaturas de metadados e para converter de um ao outro.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="e5ce5-117">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="e5ce5-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="e5ce5-118">`IMetaDataDispenser` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="e5ce5-119">Use `IMetaDataDispenserEx` em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="e5ce5-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="e5ce5-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="e5ce5-121">Fornece métodos que mapeiam as áreas de memória para criação ou modificação de metadados.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="e5ce5-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e5ce5-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="e5ce5-123">Fornece métodos para criar, modificar e armazenar os metadados sobre o assembly no escopo definido no momento.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="e5ce5-124">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e5ce5-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="e5ce5-125">Fornece métodos para definir e modificar as assinaturas de metadados de métodos e construtores com parâmetros de tipo <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="e5ce5-126">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="e5ce5-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="e5ce5-127">Fornece um mecanismo de retorno de chamada para o relatório de erros durante a resolução da assinatura de metadados para um assembly.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="e5ce5-128">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="e5ce5-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="e5ce5-129">Fornece métodos para a marcação e a filtragem de tokens de metadados para evitar a repetição de ações que já foi usadas.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="e5ce5-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e5ce5-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="e5ce5-131">Fornece métodos para importação e manipulação de tipos de outros assemblies.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="e5ce5-132">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e5ce5-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="e5ce5-133">Estende `IMetaDataImport` para fornecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="e5ce5-134">Interface IMetaDataInfo</span><span class="sxs-lookup"><span data-stu-id="e5ce5-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="e5ce5-135">Fornece um método que obtém informações sobre o mapeamento de metadados de um arquivo em disco na memória.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="e5ce5-136">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="e5ce5-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="e5ce5-137">Fornece métodos para o armazenamento e recuperação de informações de metadados nas tabelas.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="e5ce5-138">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="e5ce5-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="e5ce5-139">Estende `IMetaDataTables` para incluir os métodos para trabalhar com fluxos de metadados.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="e5ce5-140">Interface IMetaDataValidate</span><span class="sxs-lookup"><span data-stu-id="e5ce5-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="e5ce5-141">Fornece métodos para usar para validação de assinaturas de metadados.</span><span class="sxs-lookup"><span data-stu-id="e5ce5-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5ce5-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e5ce5-142">Related Sections</span></span>  
 [<span data-ttu-id="e5ce5-143">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="e5ce5-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="e5ce5-144">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="e5ce5-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="e5ce5-145">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="e5ce5-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="e5ce5-146">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="e5ce5-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
