---
title: Interfaces de metadados
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4672cb813cec4a127f7888a2273eb26c3f34c3d9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431593"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="e1536-102">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="e1536-102">Metadata Interfaces</span></span>
<span data-ttu-id="e1536-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span><span class="sxs-lookup"><span data-stu-id="e1536-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1536-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e1536-104">In This Section</span></span>  
 [<span data-ttu-id="e1536-105">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="e1536-105">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 <span data-ttu-id="e1536-106">Provides methods for dynamic code compilation.</span><span class="sxs-lookup"><span data-stu-id="e1536-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="e1536-107">Interface IHostFilter</span><span class="sxs-lookup"><span data-stu-id="e1536-107">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 <span data-ttu-id="e1536-108">Provides a method for the run-time host to mark metadata tokens for processing.</span><span class="sxs-lookup"><span data-stu-id="e1536-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="e1536-109">Interface IMapToken</span><span class="sxs-lookup"><span data-stu-id="e1536-109">IMapToken Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 <span data-ttu-id="e1536-110">Provides mapping capabilities between imported and emitted metadata signatures.</span><span class="sxs-lookup"><span data-stu-id="e1536-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="e1536-111">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="e1536-111">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 <span data-ttu-id="e1536-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span><span class="sxs-lookup"><span data-stu-id="e1536-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="e1536-113">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="e1536-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 <span data-ttu-id="e1536-114">Provides methods to access and examine the contents of an assembly manifest.</span><span class="sxs-lookup"><span data-stu-id="e1536-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="e1536-115">Interface IMetaDataConverter</span><span class="sxs-lookup"><span data-stu-id="e1536-115">IMetaDataConverter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 <span data-ttu-id="e1536-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span><span class="sxs-lookup"><span data-stu-id="e1536-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="e1536-117">Interface IMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="e1536-117">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 <span data-ttu-id="e1536-118">`IMetaDataDispenser` é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="e1536-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="e1536-119">Use `IMetaDataDispenserEx` em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="e1536-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="e1536-120">Interface IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="e1536-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 <span data-ttu-id="e1536-121">Provides methods that map areas of memory for creating or modifying metadata.</span><span class="sxs-lookup"><span data-stu-id="e1536-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="e1536-122">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="e1536-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 <span data-ttu-id="e1536-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span><span class="sxs-lookup"><span data-stu-id="e1536-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="e1536-124">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="e1536-124">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 <span data-ttu-id="e1536-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1536-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="e1536-126">Interface IMetaDataError</span><span class="sxs-lookup"><span data-stu-id="e1536-126">IMetaDataError Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 <span data-ttu-id="e1536-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span><span class="sxs-lookup"><span data-stu-id="e1536-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="e1536-128">Interface IMetaDataFilter</span><span class="sxs-lookup"><span data-stu-id="e1536-128">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 <span data-ttu-id="e1536-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span><span class="sxs-lookup"><span data-stu-id="e1536-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="e1536-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e1536-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 <span data-ttu-id="e1536-131">Provides methods for importing and manipulating types from other assemblies.</span><span class="sxs-lookup"><span data-stu-id="e1536-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="e1536-132">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e1536-132">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 <span data-ttu-id="e1536-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span><span class="sxs-lookup"><span data-stu-id="e1536-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="e1536-134">Interface IMetaDataInfo</span><span class="sxs-lookup"><span data-stu-id="e1536-134">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 <span data-ttu-id="e1536-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span><span class="sxs-lookup"><span data-stu-id="e1536-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="e1536-136">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="e1536-136">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 <span data-ttu-id="e1536-137">Provides methods for the storage and retrieval of metadata information in tables.</span><span class="sxs-lookup"><span data-stu-id="e1536-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="e1536-138">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="e1536-138">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 <span data-ttu-id="e1536-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span><span class="sxs-lookup"><span data-stu-id="e1536-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="e1536-140">Interface IMetaDataValidate</span><span class="sxs-lookup"><span data-stu-id="e1536-140">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 <span data-ttu-id="e1536-141">Provides methods to use for validation of metadata signatures.</span><span class="sxs-lookup"><span data-stu-id="e1536-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e1536-142">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e1536-142">Related Sections</span></span>  
 [<span data-ttu-id="e1536-143">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="e1536-143">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [<span data-ttu-id="e1536-144">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="e1536-144">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [<span data-ttu-id="e1536-145">Estruturas de metadados</span><span class="sxs-lookup"><span data-stu-id="e1536-145">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [<span data-ttu-id="e1536-146">Uniões de metadados</span><span class="sxs-lookup"><span data-stu-id="e1536-146">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
