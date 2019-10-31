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
ms.openlocfilehash: 728e8bdbce7f93176324d8f80261030f8cbae283
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140413"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="5274b-102">Método ICorPublishProcess::GetProcessID</span><span class="sxs-lookup"><span data-stu-id="5274b-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="5274b-103">Obtém o identificador do sistema operacional para esse processo.</span><span class="sxs-lookup"><span data-stu-id="5274b-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5274b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5274b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5274b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5274b-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="5274b-106">fora Um ponteiro para o identificador do processo representado por esse objeto [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5274b-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5274b-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5274b-107">Requirements</span></span>  
 <span data-ttu-id="5274b-108">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5274b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5274b-109">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="5274b-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5274b-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5274b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5274b-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5274b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5274b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5274b-112">See also</span></span>

- [<span data-ttu-id="5274b-113">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="5274b-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
