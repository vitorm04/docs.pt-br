---
title: Método IMetaDataEmit::SetPermissionSetProps
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: de4cfdf2a9353eebdebaf4df9e481d06d776ff04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177482"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="b61a2-102">Método IMetaDataEmit::SetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="b61a2-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="b61a2-103">Define ou atualiza os recursos da assinatura de metadados de um conjunto de permissões definido por uma chamada anterior ao [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="b61a2-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b61a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b61a2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b61a2-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="b61a2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b61a2-106">[em] Um token de metadados que representa o objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="b61a2-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="b61a2-107">[em] Um valor [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) que especifica o tipo de segurança declarativa a ser usada.</span><span class="sxs-lookup"><span data-stu-id="b61a2-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="b61a2-108">[em] A permissão BLOB.</span><span class="sxs-lookup"><span data-stu-id="b61a2-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="b61a2-109">[em] O tamanho, em bytes, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="b61a2-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="b61a2-110">[fora] Um `mdPermission` token de metadados que representa as permissões atualizadas.</span><span class="sxs-lookup"><span data-stu-id="b61a2-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b61a2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b61a2-111">Requirements</span></span>  
 <span data-ttu-id="b61a2-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b61a2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b61a2-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b61a2-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b61a2-114">**Biblioteca:** Usado como recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b61a2-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b61a2-115">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b61a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61a2-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b61a2-116">See also</span></span>

- [<span data-ttu-id="b61a2-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="b61a2-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b61a2-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="b61a2-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
