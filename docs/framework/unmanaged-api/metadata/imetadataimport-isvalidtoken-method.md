---
title: Método IMetaDataImport::IsValidToken
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: edf24de8ae38aab97e41a53cc86ae5aa6c592c50
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434695"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="b9d40-102">Método IMetaDataImport::IsValidToken</span><span class="sxs-lookup"><span data-stu-id="b9d40-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="b9d40-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span><span class="sxs-lookup"><span data-stu-id="b9d40-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d40-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9d40-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9d40-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9d40-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b9d40-106">[in] The token to check the reference validity for.</span><span class="sxs-lookup"><span data-stu-id="b9d40-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9d40-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b9d40-107">Return Value</span></span>  
 <span data-ttu-id="b9d40-108">`true` if `tk` is a valid metadata token within the current scope.</span><span class="sxs-lookup"><span data-stu-id="b9d40-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="b9d40-109">Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b9d40-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d40-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9d40-110">Requirements</span></span>  
 <span data-ttu-id="b9d40-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9d40-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9d40-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9d40-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9d40-113">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b9d40-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9d40-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9d40-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d40-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9d40-115">See also</span></span>

- [<span data-ttu-id="b9d40-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b9d40-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b9d40-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b9d40-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
