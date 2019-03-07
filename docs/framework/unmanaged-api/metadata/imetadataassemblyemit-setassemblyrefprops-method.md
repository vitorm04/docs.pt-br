---
title: Método IMetaDataAssemblyEmit::SetAssemblyRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b6c29861faa469f03ca5f2d3cb18e95b3e78f52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489898"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="851f0-102">Método IMetaDataAssemblyEmit::SetAssemblyRefProps</span><span class="sxs-lookup"><span data-stu-id="851f0-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="851f0-103">Modifica especificado `AssemblyRef` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="851f0-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="851f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="851f0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="851f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="851f0-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="851f0-106">[in] O token de metadados que especifica o `AssemblyRef` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="851f0-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="851f0-107">[in] A chave pública do Editor do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="851f0-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="851f0-108">[in] O tamanho em bytes do `pbPublicKeyOrToken`.</span><span class="sxs-lookup"><span data-stu-id="851f0-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="851f0-109">[in] O nome de texto legível do assembly.</span><span class="sxs-lookup"><span data-stu-id="851f0-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="851f0-110">[in] Um ponteiro para uma instância ASSEMBLYMETADATA que contém as informações de localidade, plataforma e versão para o assembly.</span><span class="sxs-lookup"><span data-stu-id="851f0-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="851f0-111">[in] Um ponteiro para o hash de dados associados ao assembly.</span><span class="sxs-lookup"><span data-stu-id="851f0-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="851f0-112">[in] O tamanho em bytes do `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="851f0-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="851f0-113">[in] Uma combinação bit a bit de [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) valores que especificam os atributos do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="851f0-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="851f0-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="851f0-114">Remarks</span></span>  
 <span data-ttu-id="851f0-115">Para criar uma `AssemblyRef` estrutura de metadados, use o [imetadataassemblyemit:: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="851f0-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="851f0-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="851f0-116">Requirements</span></span>  
 <span data-ttu-id="851f0-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="851f0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="851f0-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="851f0-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="851f0-119">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="851f0-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="851f0-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="851f0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="851f0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="851f0-121">See also</span></span>
- [<span data-ttu-id="851f0-122">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="851f0-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
