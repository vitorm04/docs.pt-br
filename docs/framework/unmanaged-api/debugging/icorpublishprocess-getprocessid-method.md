---
title: Método ICorPublishProcess::GetProcessID
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f3948e45b991e667ea90c7846ee0d6fd630c0db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165796"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="cbdbf-102">Método ICorPublishProcess::GetProcessID</span><span class="sxs-lookup"><span data-stu-id="cbdbf-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="cbdbf-103">Obtém o identificador de sistema operacional para que esse processo.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbdbf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbdbf-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbdbf-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbdbf-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="cbdbf-106">[out] Um ponteiro para o identificador do processo representado por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="cbdbf-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbdbf-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbdbf-107">Requirements</span></span>  
 <span data-ttu-id="cbdbf-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbdbf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbdbf-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="cbdbf-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cbdbf-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbdbf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbdbf-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbdbf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbdbf-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbdbf-112">See also</span></span>

- [<span data-ttu-id="cbdbf-113">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="cbdbf-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
