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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8a4d3b7014d0da88e83b507c39c039d39ba93d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542672"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="49729-102">Método IMetaDataEmit::SetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="49729-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="49729-103">Define ou atualiza os recursos da assinatura de metadados de um conjunto de permissões definida por uma chamada anterior a [imetadataemit:: Definepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="49729-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49729-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49729-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49729-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49729-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="49729-106">[in] Um token de metadados que representa o objeto ser decorada.</span><span class="sxs-lookup"><span data-stu-id="49729-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="49729-107">[in] Um [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valor que especifica o tipo de segurança declarativa a ser usado.</span><span class="sxs-lookup"><span data-stu-id="49729-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="49729-108">[in] A permissão de BLOB.</span><span class="sxs-lookup"><span data-stu-id="49729-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="49729-109">[in] O tamanho, em bytes, do `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="49729-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="49729-110">[out] Um `mdPermission` token de metadados que representa as permissões atualizadas.</span><span class="sxs-lookup"><span data-stu-id="49729-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49729-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49729-111">Requirements</span></span>  
 <span data-ttu-id="49729-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49729-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49729-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="49729-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49729-114">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="49729-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49729-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49729-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49729-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49729-116">See also</span></span>
- [<span data-ttu-id="49729-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="49729-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="49729-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="49729-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
