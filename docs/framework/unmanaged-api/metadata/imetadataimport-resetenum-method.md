---
title: "Método IMetaDataImport::ResetEnum"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.ResetEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 794dcd1b211f5fe3a4ac9f2c840eba6bb908c6ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="d34e3-102">Método IMetaDataImport::ResetEnum</span><span class="sxs-lookup"><span data-stu-id="d34e3-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="d34e3-103">Redefine o enumerador especificado para a posição especificada.</span><span class="sxs-lookup"><span data-stu-id="d34e3-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d34e3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d34e3-104">Syntax</span></span>  
  
```  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,   
   [in] ULONG       ulPos  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d34e3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d34e3-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d34e3-106">[in] O enumerador para redefinir.</span><span class="sxs-lookup"><span data-stu-id="d34e3-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="d34e3-107">[in] A nova posição na qual colocar o enumerador.</span><span class="sxs-lookup"><span data-stu-id="d34e3-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d34e3-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d34e3-108">Requirements</span></span>  
 <span data-ttu-id="d34e3-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d34e3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d34e3-110">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d34e3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d34e3-111">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d34e3-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d34e3-112">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d34e3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d34e3-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d34e3-113">See Also</span></span>  
 [<span data-ttu-id="d34e3-114">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d34e3-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d34e3-115">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d34e3-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
