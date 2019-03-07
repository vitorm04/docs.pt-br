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
ms.openlocfilehash: 61c67e074fc32098fa0d8326ea2f0ecfb1efa952
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471759"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="2bdda-102">Método ICorPublishProcess::GetProcessID</span><span class="sxs-lookup"><span data-stu-id="2bdda-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="2bdda-103">Obtém o identificador de sistema operacional para que esse processo.</span><span class="sxs-lookup"><span data-stu-id="2bdda-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bdda-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bdda-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bdda-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2bdda-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="2bdda-106">[out] Um ponteiro para o identificador do processo representado por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="2bdda-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bdda-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2bdda-107">Requirements</span></span>  
 <span data-ttu-id="2bdda-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bdda-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bdda-109">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2bdda-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2bdda-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bdda-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bdda-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bdda-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bdda-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bdda-112">See also</span></span>
- [<span data-ttu-id="2bdda-113">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="2bdda-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
