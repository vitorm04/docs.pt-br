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
ms.openlocfilehash: 53a75b8e7edd15cd233577e0a3714fb5d981495f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432330"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="dc03d-102">Método IMetaDataEmit::SetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="dc03d-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="dc03d-103">Define ou atualiza recursos da assinatura de metadados de um conjunto de permissões definido por uma chamada anterior para [IMetaDataEmit::D efinepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="dc03d-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc03d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc03d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc03d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dc03d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="dc03d-106">no Um token de metadados que representa o objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="dc03d-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="dc03d-107">no Um valor de [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) que especifica o tipo de segurança declarativa a ser usado.</span><span class="sxs-lookup"><span data-stu-id="dc03d-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="dc03d-108">no O BLOB de permissão.</span><span class="sxs-lookup"><span data-stu-id="dc03d-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="dc03d-109">no O tamanho, em bytes, de `pvPermission`.</span><span class="sxs-lookup"><span data-stu-id="dc03d-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="dc03d-110">fora Um `mdPermission` token de metadados que representa as permissões atualizadas.</span><span class="sxs-lookup"><span data-stu-id="dc03d-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc03d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc03d-111">Requirements</span></span>  
 <span data-ttu-id="dc03d-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc03d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc03d-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dc03d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc03d-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc03d-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc03d-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc03d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc03d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc03d-116">See also</span></span>

- [<span data-ttu-id="dc03d-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="dc03d-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="dc03d-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="dc03d-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
