---
title: "Método ICorDebugProcess::EnableLogMessages"
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
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4c67d211e9408cec54d069c4d9bad963aeabb09d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="ea94d-102">Método ICorDebugProcess::EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="ea94d-102">ICorDebugProcess::EnableLogMessages Method</span></span>
<span data-ttu-id="ea94d-103">Habilita e desabilita a transmissão de mensagens de log para o depurador.</span><span class="sxs-lookup"><span data-stu-id="ea94d-103">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea94d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea94d-104">Syntax</span></span>  
  
```  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea94d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea94d-105">Parameters</span></span>  
 `fOnOff`  
 <span data-ttu-id="ea94d-106">[in] `true` permite a transmissão de mensagens de log; `false` desabilita a transmissão.</span><span class="sxs-lookup"><span data-stu-id="ea94d-106">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea94d-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea94d-107">Remarks</span></span>  
 <span data-ttu-id="ea94d-108">Este método é válido somente após o [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) ocorre de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="ea94d-108">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea94d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea94d-109">Requirements</span></span>  
 <span data-ttu-id="ea94d-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea94d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea94d-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea94d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea94d-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea94d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea94d-113">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea94d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
