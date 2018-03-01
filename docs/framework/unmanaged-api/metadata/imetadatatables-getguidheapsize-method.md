---
title: "Método IMetaDataTables::GetGuidHeapSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 297b8f3572f67aa5e8b17b1b94d71f59962cfe68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="98432-102">Método IMetaDataTables::GetGuidHeapSize</span><span class="sxs-lookup"><span data-stu-id="98432-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="98432-103">Obtém o tamanho, em bytes, do heap GUID.</span><span class="sxs-lookup"><span data-stu-id="98432-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98432-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98432-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98432-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98432-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="98432-106">[out] Um ponteiro para o tamanho, em bytes, do heap GUID.</span><span class="sxs-lookup"><span data-stu-id="98432-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98432-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98432-107">Requirements</span></span>  
 <span data-ttu-id="98432-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98432-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98432-109">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="98432-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="98432-110">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="98432-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="98432-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98432-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98432-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98432-112">See Also</span></span>  
 [<span data-ttu-id="98432-113">Interface IMetaDataTables</span><span class="sxs-lookup"><span data-stu-id="98432-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="98432-114">Interface IMetaDataTables2</span><span class="sxs-lookup"><span data-stu-id="98432-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
