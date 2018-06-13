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
ms.openlocfilehash: da75f98edb54080658dc86f48d4ebb458d72f20d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449306"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="fac91-102">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="fac91-102">IMetaDataAssemblyImport Interface</span></span>
<span data-ttu-id="fac91-103">Fornece métodos para acessar e examinar o conteúdo de um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="fac91-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fac91-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fac91-104">Methods</span></span>  
  
|<span data-ttu-id="fac91-105">Método</span><span class="sxs-lookup"><span data-stu-id="fac91-105">Method</span></span>|<span data-ttu-id="fac91-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fac91-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fac91-107">Método CloseEnum</span><span class="sxs-lookup"><span data-stu-id="fac91-107">CloseEnum Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="fac91-108">Libera o identificador para o enumerador especificado.</span><span class="sxs-lookup"><span data-stu-id="fac91-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="fac91-109">Método EnumAssemblyRefs</span><span class="sxs-lookup"><span data-stu-id="fac91-109">EnumAssemblyRefs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="fac91-110">Obtém um ponteiro de interface para um enumerador que contém o `mdAssemblyRef` tokens dos assemblies referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fac91-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fac91-111">Método EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="fac91-111">EnumExportedTypes Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="fac91-112">Obtém um ponteiro de interface para um enumerador que contém o `mdExportedType` tokens dos tipos COM referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fac91-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fac91-113">Método EnumFiles</span><span class="sxs-lookup"><span data-stu-id="fac91-113">EnumFiles Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="fac91-114">Obtém um ponteiro de interface para um enumerador que contém o `mdFile` tokens dos arquivos referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fac91-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fac91-115">Método EnumManifestResources</span><span class="sxs-lookup"><span data-stu-id="fac91-115">EnumManifestResources Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="fac91-116">Obtém um ponteiro de interface para um enumerador que contém o `mdManifestResource` tokens dos recursos referenciados pelo assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fac91-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fac91-117">Método FindAssembliesByName</span><span class="sxs-lookup"><span data-stu-id="fac91-117">FindAssembliesByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="fac91-118">Obtém uma matriz de `mdAssemblyRef` tokens para os assemblies com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fac91-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="fac91-119">Método FindExportedTypeByName</span><span class="sxs-lookup"><span data-stu-id="fac91-119">FindExportedTypeByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="fac91-120">Obtém um `mdExportedType` token para o tipo COM o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fac91-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="fac91-121">Método FindManifestResourceByName</span><span class="sxs-lookup"><span data-stu-id="fac91-121">FindManifestResourceByName Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="fac91-122">Obtém um `mdManifestResource` token para o recurso com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="fac91-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="fac91-123">Método GetAssemblyFromScope</span><span class="sxs-lookup"><span data-stu-id="fac91-123">GetAssemblyFromScope Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="fac91-124">Obtém o token para o assembly no escopo atual de metadados.</span><span class="sxs-lookup"><span data-stu-id="fac91-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="fac91-125">Método GetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="fac91-125">GetAssemblyProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="fac91-126">Obtém as configurações de propriedade do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="fac91-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="fac91-127">Método GetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="fac91-127">GetAssemblyRefProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="fac91-128">Obtém as configurações de propriedade especificada `mdAssemblyRef` token.</span><span class="sxs-lookup"><span data-stu-id="fac91-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="fac91-129">Método GetExportedTypeProps</span><span class="sxs-lookup"><span data-stu-id="fac91-129">GetExportedTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="fac91-130">Obtém as configurações de propriedade do tipo especificado COM.</span><span class="sxs-lookup"><span data-stu-id="fac91-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="fac91-131">Método GetFileProps</span><span class="sxs-lookup"><span data-stu-id="fac91-131">GetFileProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="fac91-132">Obtém as configurações de propriedade do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="fac91-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="fac91-133">Método GetManifestResourceProps</span><span class="sxs-lookup"><span data-stu-id="fac91-133">GetManifestResourceProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="fac91-134">Obtém as configurações de propriedade do recurso de manifesto especificado.</span><span class="sxs-lookup"><span data-stu-id="fac91-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fac91-135">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fac91-135">Requirements</span></span>  
 <span data-ttu-id="fac91-136">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fac91-136">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fac91-137">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fac91-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fac91-138">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fac91-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fac91-139">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fac91-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac91-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fac91-140">See Also</span></span>  
 [<span data-ttu-id="fac91-141">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="fac91-141">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="fac91-142">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="fac91-142">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
