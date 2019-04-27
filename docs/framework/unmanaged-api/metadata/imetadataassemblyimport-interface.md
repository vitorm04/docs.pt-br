---
title: Interface IMetaDataAssemblyImport
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 373ff0470e2403f91534df0c0ffe4039dbb0f832
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905405"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="d66bc-102">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="d66bc-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="d66bc-103">Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d66bc-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d66bc-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d66bc-104">Methods</span></span>  
  
|<span data-ttu-id="d66bc-105">Método</span><span class="sxs-lookup"><span data-stu-id="d66bc-105">Method</span></span>|<span data-ttu-id="d66bc-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d66bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d66bc-107">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="d66bc-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="d66bc-108">Libera o identificador para o enumerador especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="d66bc-109">Método EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="d66bc-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="d66bc-110">Obtém um ponteiro de interface para um enumerador que contém o `mdAssemblyRef` tokens dos assemblies referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="d66bc-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="d66bc-111">Método EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="d66bc-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="d66bc-112">Obtém um ponteiro de interface para um enumerador que contém o `mdExportedType` tokens dos tipos COM referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="d66bc-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="d66bc-113">Método EnumFiles</span><span class="sxs-lookup"><span data-stu-id="d66bc-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="d66bc-114">Obtém um ponteiro de interface para um enumerador que contém o `mdFile` tokens dos arquivos referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="d66bc-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="d66bc-115">Método EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="d66bc-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="d66bc-116">Obtém um ponteiro de interface para um enumerador que contém o `mdManifestResource` tokens dos recursos referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="d66bc-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="d66bc-117">Método FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="d66bc-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="d66bc-118">Obtém uma matriz de `mdAssemblyRef` tokens para os assemblies com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="d66bc-119">Método FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="d66bc-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="d66bc-120">Obtém um `mdExportedType` token para o tipo de COM o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="d66bc-121">Método FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="d66bc-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="d66bc-122">Obtém um `mdManifestResource` token para o recurso com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="d66bc-123">Método GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="d66bc-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="d66bc-124">Obtém o token para o assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="d66bc-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="d66bc-125">Método GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="d66bc-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="d66bc-126">Obtém as configurações de propriedade do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="d66bc-127">Método GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="d66bc-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="d66bc-128">Obtém as configurações de propriedade especificada `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="d66bc-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="d66bc-129">Método GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="d66bc-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="d66bc-130">Obtém as configurações de propriedade do tipo COM especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="d66bc-131">Método GetFileProps</span><span class="sxs-lookup"><span data-stu-id="d66bc-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="d66bc-132">Obtém as configurações de propriedade do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="d66bc-133">Método GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="d66bc-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="d66bc-134">Obtém as configurações de propriedade do recurso de manifesto especificado.</span><span class="sxs-lookup"><span data-stu-id="d66bc-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d66bc-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d66bc-135">Requirements</span></span>  
 <span data-ttu-id="d66bc-136">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d66bc-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d66bc-137">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d66bc-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d66bc-138">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="d66bc-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d66bc-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d66bc-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66bc-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d66bc-140">See also</span></span>

- [<span data-ttu-id="d66bc-141">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="d66bc-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="d66bc-142">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="d66bc-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
