---
title: Método IMetaDataAssemblyImport::EnumExportedTypes
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumExportedTypes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumExportedTypes
helpviewer_keywords:
- EnumExportedTypes method [.NET Framework metadata]
- IMetaDataAssemblyImport::EnumExportedTypes method [.NET Framework metadata]
ms.assetid: e5912ed8-e4ce-438b-8ea3-d9e4c288d109
topic_type:
- apiref
ms.openlocfilehash: 45e2348b4726447548544d975e60b93e464fb402
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450334"
---
# <a name="imetadataassemblyimportenumexportedtypes-method"></a><span data-ttu-id="78e75-102">Método IMetaDataAssemblyImport::EnumExportedTypes</span><span class="sxs-lookup"><span data-stu-id="78e75-102">IMetaDataAssemblyImport::EnumExportedTypes Method</span></span>
<span data-ttu-id="78e75-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="78e75-103">Enumerates the exported types referenced in the assembly manifest in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78e75-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumExportedTypes (  
    [in, out] HCORENUM     *phEnum,   
    [out] mdExportedType   rExportedTypes[],   
    [in]  ULONG            cMax,   
    [out] ULONG            *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78e75-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78e75-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="78e75-106">[in, out] A pointer to the enumerator.</span><span class="sxs-lookup"><span data-stu-id="78e75-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="78e75-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span><span class="sxs-lookup"><span data-stu-id="78e75-107">This must be a null value when the `EnumExportedTypes` method is called for the first time.</span></span>  
  
 `rExportedTypes`  
 <span data-ttu-id="78e75-108">[out] The enumeration of `mdExportedType` metadata tokens.</span><span class="sxs-lookup"><span data-stu-id="78e75-108">[out] The enumeration of `mdExportedType` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="78e75-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span><span class="sxs-lookup"><span data-stu-id="78e75-109">[in] The maximum number of `mdExportedType` tokens that can be placed in the `rExportedTypes` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="78e75-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span><span class="sxs-lookup"><span data-stu-id="78e75-110">[out] The number of `mdExportedType` tokens actually placed in `rExportedTypes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78e75-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="78e75-111">Return Value</span></span>  
  
|<span data-ttu-id="78e75-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78e75-112">HRESULT</span></span>|<span data-ttu-id="78e75-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="78e75-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="78e75-114">`EnumExportedTypes` returned successfully.</span><span class="sxs-lookup"><span data-stu-id="78e75-114">`EnumExportedTypes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="78e75-115">There are no tokens to enumerate.</span><span class="sxs-lookup"><span data-stu-id="78e75-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="78e75-116">In this case, `pcTokens` is set to zero.</span><span class="sxs-lookup"><span data-stu-id="78e75-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="78e75-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78e75-117">Requirements</span></span>  
 <span data-ttu-id="78e75-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78e75-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e75-119">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78e75-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78e75-120">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78e75-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78e75-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e75-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e75-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78e75-122">See also</span></span>

- [<span data-ttu-id="78e75-123">Interface IMetaDataAssemblyImport</span><span class="sxs-lookup"><span data-stu-id="78e75-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
