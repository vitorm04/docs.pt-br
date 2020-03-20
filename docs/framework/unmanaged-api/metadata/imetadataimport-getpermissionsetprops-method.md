---
title: Método IMetaDataImport::GetPermissionSetProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: 5faf1a6ae89045b2ef17fab789ee6e5bf23eecf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175337"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="d1e74-102">Método IMetaDataImport::GetPermissionSetProps</span><span class="sxs-lookup"><span data-stu-id="d1e74-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="d1e74-103">Obtém os metadados <xref:System.Security.PermissionSet?displayProperty=nameWithType> associados ao representado pelo token de permissão especificado.</span><span class="sxs-lookup"><span data-stu-id="d1e74-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1e74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1e74-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="d1e74-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="d1e74-106">[em] O token de metadados de permissão que representa o conjunto de permissões para obter as propriedades de metadados para.</span><span class="sxs-lookup"><span data-stu-id="d1e74-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="d1e74-107">[fora] Um ponteiro para o conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="d1e74-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="d1e74-108">[fora] Um ponteiro para a assinatura binária de metadados do conjunto de permissões.</span><span class="sxs-lookup"><span data-stu-id="d1e74-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="d1e74-109">[fora] O tamanho em bytes de `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="d1e74-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1e74-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d1e74-110">Requirements</span></span>  
 <span data-ttu-id="d1e74-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1e74-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1e74-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d1e74-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d1e74-113">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1e74-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d1e74-114">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1e74-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e74-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="d1e74-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="d1e74-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d1e74-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d1e74-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d1e74-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
