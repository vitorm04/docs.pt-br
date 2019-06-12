---
title: Método ICorDebugAppDomain3::GetCachedWinRTTypes
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7e2685d17f3dd32db295f926fc19121d29e1752
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025916"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="2cf61-102">Método ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="2cf61-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="2cf61-103">Obtém um enumerador para todos os tipos de tempo de execução do Windows em cache.</span><span class="sxs-lookup"><span data-stu-id="2cf61-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cf61-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cf61-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cf61-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="2cf61-106">[out] Um ponteiro para um [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) objeto de interface que pode enumerar as representações gerenciadas dos tipos de tempo de execução do Windows atualmente carregados no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2cf61-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf61-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cf61-107">Requirements</span></span>  
 <span data-ttu-id="2cf61-108">**Plataformas:** Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="2cf61-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="2cf61-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cf61-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cf61-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cf61-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cf61-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf61-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf61-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cf61-112">See also</span></span>

- [<span data-ttu-id="2cf61-113">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="2cf61-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
