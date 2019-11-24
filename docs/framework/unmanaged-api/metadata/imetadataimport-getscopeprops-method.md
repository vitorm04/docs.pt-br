---
title: Método IMetaDataImport::GetScopeProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: af1c3d599c5280e584ffb842c96c70a7c3d4ed08
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436882"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="a59da-102">Método IMetaDataImport::GetScopeProps</span><span class="sxs-lookup"><span data-stu-id="a59da-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="a59da-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="a59da-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59da-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a59da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a59da-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a59da-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="a59da-106">[out] A buffer for the assembly or module name.</span><span class="sxs-lookup"><span data-stu-id="a59da-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a59da-107">[in] The size in wide characters of `szName`.</span><span class="sxs-lookup"><span data-stu-id="a59da-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="a59da-108">[out] The number of wide characters returned in `szName`.</span><span class="sxs-lookup"><span data-stu-id="a59da-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="a59da-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span><span class="sxs-lookup"><span data-stu-id="a59da-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a59da-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a59da-110">Remarks</span></span>  
 <span data-ttu-id="a59da-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span><span class="sxs-lookup"><span data-stu-id="a59da-111">The [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59da-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a59da-112">Requirements</span></span>  
 <span data-ttu-id="a59da-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a59da-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59da-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a59da-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a59da-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a59da-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a59da-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59da-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59da-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a59da-117">See also</span></span>

- [<span data-ttu-id="a59da-118">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a59da-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a59da-119">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a59da-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
