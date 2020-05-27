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
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007800"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="a6867-102">Método IMetaDataEmit::SetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="a6867-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="a6867-103">Define ou atualiza recursos da assinatura de metadados de um conjunto de permissões definido por uma chamada anterior para [IMetaDataEmit::D efinepermissionset](imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="a6867-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6867-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6867-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6867-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6867-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a6867-106">no Um token de metadados que representa o objeto a ser decorado.</span><span class="sxs-lookup"><span data-stu-id="a6867-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="a6867-107">no Um valor de [CorDeclSecurity](cordeclsecurity-enumeration.md) que especifica o tipo de segurança declarativa a ser usado.</span><span class="sxs-lookup"><span data-stu-id="a6867-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="a6867-108">no O BLOB de permissão.</span><span class="sxs-lookup"><span data-stu-id="a6867-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="a6867-109">no O tamanho, em bytes, de `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="a6867-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="a6867-110">fora Um `mdPermission` token de metadados que representa as permissões atualizadas.</span><span class="sxs-lookup"><span data-stu-id="a6867-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6867-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6867-111">Requirements</span></span>  
 <span data-ttu-id="a6867-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6867-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6867-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a6867-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6867-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a6867-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6867-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6867-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6867-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a6867-116">See also</span></span>

- [<span data-ttu-id="a6867-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="a6867-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a6867-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="a6867-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
