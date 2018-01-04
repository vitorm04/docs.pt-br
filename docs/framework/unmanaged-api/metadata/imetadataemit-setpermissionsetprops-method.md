---
title: "Método IMetaDataEmit::SetPermissionSetProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetPermissionSetProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34f2357de8d7ec522b4d10212eb82e351df8d152
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="5549a-102">Método IMetaDataEmit::SetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="5549a-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="5549a-103">Define ou atualiza os recursos da assinatura de metadados de um conjunto de permissões definida por uma chamada anterior ao [: Definepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="5549a-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5549a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5549a-104">Syntax</span></span>  
  
```  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5549a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5549a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5549a-106">[in] Um token de metadados que representa o objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="5549a-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="5549a-107">[in] Um [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) valor que especifica o tipo de segurança declarativa para ser usado.</span><span class="sxs-lookup"><span data-stu-id="5549a-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="5549a-108">[in] O BLOB de permissão.</span><span class="sxs-lookup"><span data-stu-id="5549a-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="5549a-109">[in] O tamanho, em bytes, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="5549a-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="5549a-110">[out] Um `mdPermission` token de metadados que representa as permissões atualizadas.</span><span class="sxs-lookup"><span data-stu-id="5549a-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5549a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5549a-111">Requirements</span></span>  
 <span data-ttu-id="5549a-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5549a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5549a-113">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5549a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5549a-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5549a-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5549a-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5549a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5549a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5549a-116">See Also</span></span>  
 [<span data-ttu-id="5549a-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="5549a-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5549a-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="5549a-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
