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
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008112"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="dc648-102">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="dc648-102">IMetaDataAssemblyEmit Interface</span></span>
<span data-ttu-id="dc648-103">Fornece métodos que dão suporte ao modelo de autodescrição usado pelo Common Language Runtime para resolver e consumir recursos.</span><span class="sxs-lookup"><span data-stu-id="dc648-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc648-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="dc648-104">Methods</span></span>  
  
|<span data-ttu-id="dc648-105">Método</span><span class="sxs-lookup"><span data-stu-id="dc648-105">Method</span></span>|<span data-ttu-id="dc648-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc648-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc648-107">Método DefineAssembly</span><span class="sxs-lookup"><span data-stu-id="dc648-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="dc648-108">Cria uma estrutura de dados de assembly contendo metadados para o assembly especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="dc648-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="dc648-109">Método DefineAssemblyRef</span><span class="sxs-lookup"><span data-stu-id="dc648-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="dc648-110">Cria uma `AssemblyRef` estrutura que contém metadados para o assembly ao qual este assembly faz referência e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="dc648-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="dc648-111">Método DefineExportedType</span><span class="sxs-lookup"><span data-stu-id="dc648-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="dc648-112">Cria uma `ExportedType` estrutura que contém metadados para o tipo exportado especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="dc648-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="dc648-113">Método DefineFile</span><span class="sxs-lookup"><span data-stu-id="dc648-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="dc648-114">Cria uma `File` estrutura de metadados que contém metadados para o assembly referenciado por esse assembly e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="dc648-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="dc648-115">Método DefineManifestResource</span><span class="sxs-lookup"><span data-stu-id="dc648-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="dc648-116">Cria uma `ManifestResource` estrutura que contém metadados para o recurso de manifesto especificado e retorna o token de metadados associado.</span><span class="sxs-lookup"><span data-stu-id="dc648-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="dc648-117">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="dc648-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="dc648-118">Modifica a estrutura de `Assembly` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="dc648-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="dc648-119">Método SetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="dc648-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="dc648-120">Modifica a estrutura de `AssemblyRef` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="dc648-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="dc648-121">Método SetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="dc648-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="dc648-122">Modifica a estrutura de `ExportedType` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="dc648-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="dc648-123">Método SetFileProps</span><span class="sxs-lookup"><span data-stu-id="dc648-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="dc648-124">Modifica a estrutura de `File` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="dc648-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="dc648-125">Método SetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="dc648-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="dc648-126">Modifica a estrutura de `ManifestResource` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="dc648-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc648-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="dc648-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc648-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc648-128">Requirements</span></span>  
 <span data-ttu-id="dc648-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc648-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc648-130">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dc648-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc648-131">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc648-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc648-132">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc648-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc648-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="dc648-133">See also</span></span>

- [<span data-ttu-id="dc648-134">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="dc648-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="dc648-135">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="dc648-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
