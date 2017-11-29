---
title: "Método ICorDebug::EnumerateProcesses"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.EnumerateProcesses
api_location: mscordbi.dll
api_type: COM
f1_keywords: EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e48bc47945bc6c77758eeaa8597ad0ce57b72689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="786d8-102">Método ICorDebug::EnumerateProcesses</span><span class="sxs-lookup"><span data-stu-id="786d8-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="786d8-103">Obtém um enumerador para os processos que estão sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="786d8-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="786d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="786d8-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="786d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="786d8-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="786d8-106">Um ponteiro para o endereço de um objeto de ICorDebugProcessEnum que é o enumerador para os processos que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="786d8-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="786d8-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="786d8-107">Requirements</span></span>  
 <span data-ttu-id="786d8-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="786d8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="786d8-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="786d8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="786d8-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="786d8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="786d8-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="786d8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="786d8-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="786d8-112">See Also</span></span>  
 [<span data-ttu-id="786d8-113">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="786d8-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
