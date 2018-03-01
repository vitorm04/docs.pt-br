---
title: "Método ICorDebugThread::GetRegisterSet"
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
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3eb4acd546a2a87f7844a442110dc15343cc218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="c7d07-102">Método ICorDebugThread::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="c7d07-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="c7d07-103">Obtém um ponteiro de interface para o conjunto de registro que está associado com a parte ativa do objeto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="c7d07-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d07-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7d07-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7d07-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7d07-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="c7d07-106">[out] Um ponteiro para o endereço de um [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) conjunto de objetos de interface que representa o registro para a parte ativa desse thread.</span><span class="sxs-lookup"><span data-stu-id="c7d07-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d07-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7d07-107">Requirements</span></span>  
 <span data-ttu-id="c7d07-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7d07-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7d07-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7d07-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7d07-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7d07-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7d07-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7d07-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
