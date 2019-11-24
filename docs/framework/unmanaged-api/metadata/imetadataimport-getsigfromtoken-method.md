---
title: Método IMetaDataImport::GetSigFromToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetSigFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetSigFromToken
helpviewer_keywords:
- IMetaDataImport::GetSigFromToken method [.NET Framework metadata]
- GetSigFromToken method [.NET Framework metadata]
ms.assetid: ab894dc4-f7b6-4afc-bfcb-582a4b7e53a2
topic_type:
- apiref
ms.openlocfilehash: 205f48fb417365565695c72095187d349127e536
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436855"
---
# <a name="imetadataimportgetsigfromtoken-method"></a><span data-ttu-id="464e6-102">Método IMetaDataImport::GetSigFromToken</span><span class="sxs-lookup"><span data-stu-id="464e6-102">IMetaDataImport::GetSigFromToken Method</span></span>
<span data-ttu-id="464e6-103">Gets the binary metadata signature associated with the specified token.</span><span class="sxs-lookup"><span data-stu-id="464e6-103">Gets the binary metadata signature associated with the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="464e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="464e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSigFromToken (   
   [in]   mdSignature        mdSig,   
   [out]  PCCOR_SIGNATURE    *ppvSig,   
   [out]  ULONG              *pcbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="464e6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="464e6-105">Parameters</span></span>  
 `mdSig`  
 <span data-ttu-id="464e6-106">[in] The token to return the binary metadata signature for.</span><span class="sxs-lookup"><span data-stu-id="464e6-106">[in] The token to return the binary metadata signature for.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="464e6-107">[out] A pointer to the returned metadata signature.</span><span class="sxs-lookup"><span data-stu-id="464e6-107">[out] A pointer to the returned metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="464e6-108">[out] The size in bytes of the binary metadata signature.</span><span class="sxs-lookup"><span data-stu-id="464e6-108">[out] The size in bytes of the binary metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="464e6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="464e6-109">Requirements</span></span>  
 <span data-ttu-id="464e6-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="464e6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="464e6-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="464e6-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="464e6-112">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="464e6-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="464e6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="464e6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="464e6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="464e6-114">See also</span></span>

- [<span data-ttu-id="464e6-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="464e6-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="464e6-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="464e6-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
