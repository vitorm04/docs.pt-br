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
ms.openlocfilehash: 9f213bcb9f87c34d23b53c2016bd841aae7c7194
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540267"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="fc5e8-102">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="fc5e8-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="fc5e8-103">Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc5e8-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fc5e8-104">Methods</span></span>  
  
|<span data-ttu-id="fc5e8-105">Método</span><span class="sxs-lookup"><span data-stu-id="fc5e8-105">Method</span></span>|<span data-ttu-id="fc5e8-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc5e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc5e8-107">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="fc5e8-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="fc5e8-108">Libera o identificador para o enumerador especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="fc5e8-109">Método EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="fc5e8-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="fc5e8-110">Obtém um ponteiro de interface para um enumerador que contém o `mdAssemblyRef` tokens dos assemblies referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fc5e8-111">Método EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="fc5e8-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="fc5e8-112">Obtém um ponteiro de interface para um enumerador que contém o `mdExportedType` tokens dos tipos COM referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fc5e8-113">Método EnumFiles</span><span class="sxs-lookup"><span data-stu-id="fc5e8-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="fc5e8-114">Obtém um ponteiro de interface para um enumerador que contém o `mdFile` tokens dos arquivos referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fc5e8-115">Método EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="fc5e8-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="fc5e8-116">Obtém um ponteiro de interface para um enumerador que contém o `mdManifestResource` tokens dos recursos referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fc5e8-117">Método FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="fc5e8-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="fc5e8-118">Obtém uma matriz de `mdAssemblyRef` tokens para os assemblies com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="fc5e8-119">Método FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="fc5e8-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="fc5e8-120">Obtém um `mdExportedType` token para o tipo de COM o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="fc5e8-121">Método FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="fc5e8-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="fc5e8-122">Obtém um `mdManifestResource` token para o recurso com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="fc5e8-123">Método GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="fc5e8-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="fc5e8-124">Obtém o token para o assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fc5e8-125">Método GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="fc5e8-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="fc5e8-126">Obtém as configurações de propriedade do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="fc5e8-127">Método GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="fc5e8-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="fc5e8-128">Obtém as configurações de propriedade especificada `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="fc5e8-129">Método GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="fc5e8-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="fc5e8-130">Obtém as configurações de propriedade do tipo COM especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="fc5e8-131">Método GetFileProps</span><span class="sxs-lookup"><span data-stu-id="fc5e8-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="fc5e8-132">Obtém as configurações de propriedade do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="fc5e8-133">Método GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="fc5e8-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="fc5e8-134">Obtém as configurações de propriedade do recurso de manifesto especificado.</span><span class="sxs-lookup"><span data-stu-id="fc5e8-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc5e8-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fc5e8-135">Requirements</span></span>  
 <span data-ttu-id="fc5e8-136">**Plataforma:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc5e8-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc5e8-137">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc5e8-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc5e8-138">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fc5e8-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc5e8-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc5e8-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc5e8-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc5e8-140">See also</span></span>
- [<span data-ttu-id="fc5e8-141">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="fc5e8-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="fc5e8-142">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="fc5e8-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
