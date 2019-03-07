---
title: Método ICorDebugFrame::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82902e6a395fe62464065ccea4cca5b52c960f0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492212"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="6b352-102">Método ICorDebugFrame::GetCaller</span><span class="sxs-lookup"><span data-stu-id="6b352-102">ICorDebugFrame::GetCaller Method</span></span>
<span data-ttu-id="6b352-103">Obtém um ponteiro para o objeto ICorDebugFrame da atual cadeia que chamou esse quadro.</span><span class="sxs-lookup"><span data-stu-id="6b352-103">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b352-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b352-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b352-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b352-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="6b352-106">[out] Um ponteiro para o endereço de um `ICorDebugFrame` objeto que representa o quadro de chamada.</span><span class="sxs-lookup"><span data-stu-id="6b352-106">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="6b352-107">Esse valor será nulo se o quadro de chamada é o quadro mais externo da cadeia atual.</span><span class="sxs-lookup"><span data-stu-id="6b352-107">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b352-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b352-108">Requirements</span></span>  
 <span data-ttu-id="6b352-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b352-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b352-110">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b352-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b352-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b352-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b352-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b352-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
