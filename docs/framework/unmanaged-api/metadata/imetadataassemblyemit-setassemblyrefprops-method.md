---
title: "Método IMetaDataAssemblyEmit::SetAssemblyRefProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84b6c0d748578b717a128ff3b808977ba902c6dc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="e8c5d-102">Método IMetaDataAssemblyEmit::SetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="e8c5d-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="e8c5d-103">Modifica especificado `AssemblyRef` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c5d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8c5d-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,   
    [in] const ASSEMBLYMETADATA     *pMetaData,   
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8c5d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8c5d-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="e8c5d-106">[in] O token de metadados que especifica o `AssemblyRef` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="e8c5d-107">[in] A chave pública do publicador do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="e8c5d-108">[in] O tamanho em bytes do `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="e8c5d-109">[in] O nome de texto legível do assembly.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="e8c5d-110">[in] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de localidade, plataforma e versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="e8c5d-111">[in] Um ponteiro para o hash de dados associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="e8c5d-112">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="e8c5d-113">[in] Uma combinação bit a bit de [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) valores que especificam os atributos do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8c5d-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8c5d-114">Remarks</span></span>  
 <span data-ttu-id="e8c5d-115">Para criar um `AssemblyRef` estrutura de metadados, use o [: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e8c5d-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8c5d-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8c5d-116">Requirements</span></span>  
 <span data-ttu-id="e8c5d-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8c5d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8c5d-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e8c5d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8c5d-119">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e8c5d-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8c5d-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8c5d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c5d-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8c5d-121">See Also</span></span>  
 [<span data-ttu-id="e8c5d-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="e8c5d-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
