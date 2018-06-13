---
title: Interface IMetaDataAssemblyEmit
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bda949db469d4b8629e54c9e5907da23ac7e169b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449371"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="98d5c-102">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="98d5c-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="98d5c-103">Fornece métodos que suportam o modelo de descrição Self usado pelo common language runtime para resolver e consomem recursos.</span><span class="sxs-lookup"><span data-stu-id="98d5c-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98d5c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="98d5c-104">Methods</span></span>  
  
|<span data-ttu-id="98d5c-105">Método</span><span class="sxs-lookup"><span data-stu-id="98d5c-105">Method</span></span>|<span data-ttu-id="98d5c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="98d5c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98d5c-107">Método DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="98d5c-107">DefineAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="98d5c-108">Cria uma estrutura de dados do assembly que contém metadados para o assembly especificado e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="98d5c-109">Método DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="98d5c-109">DefineAssemblyRef Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="98d5c-110">Cria um `AssemblyRef` estrutura que contém metadados para o assembly que faz referência a esse assembly e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="98d5c-111">Método DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="98d5c-111">DefineExportedType Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="98d5c-112">Cria um `ExportedType` estrutura que contém os metadados de tipo exportado de especificado e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="98d5c-113">Método DefineFile</span><span class="sxs-lookup"><span data-stu-id="98d5c-113">DefineFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="98d5c-114">Cria um `File` estrutura de metadados que contém metadados para o assembly referenciado pelo assembly e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="98d5c-115">Método DefineManifestResource</span><span class="sxs-lookup"><span data-stu-id="98d5c-115">DefineManifestResource Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="98d5c-116">Cria um `ManifestResource` estrutura que contém metadados para o recurso de manifesto especificado e retorna o token de metadados associados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="98d5c-117">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="98d5c-117">SetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="98d5c-118">Modifica especificado `Assembly` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="98d5c-119">Método SetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="98d5c-119">SetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="98d5c-120">Modifica especificado `AssemblyRef` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="98d5c-121">Método SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="98d5c-121">SetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="98d5c-122">Modifica especificado `ExportedType` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="98d5c-123">Método SetFileProps</span><span class="sxs-lookup"><span data-stu-id="98d5c-123">SetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="98d5c-124">Modifica especificado `File` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="98d5c-125">Método SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="98d5c-125">SetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="98d5c-126">Modifica especificado `ManifestResource` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="98d5c-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98d5c-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="98d5c-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98d5c-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98d5c-128">Requirements</span></span>  
 <span data-ttu-id="98d5c-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98d5c-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d5c-130">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="98d5c-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98d5c-131">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="98d5c-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98d5c-132">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98d5c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d5c-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98d5c-133">See Also</span></span>  
 [<span data-ttu-id="98d5c-134">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="98d5c-134">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="98d5c-135">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="98d5c-135">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
