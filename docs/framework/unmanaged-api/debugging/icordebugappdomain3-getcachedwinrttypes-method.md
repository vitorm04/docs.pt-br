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
ms.openlocfilehash: b7d152edac34449a08b4bcfbe5525b63abcba0fb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480761"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="2bbfe-102">Método ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="2bbfe-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="2bbfe-103">Obtém um enumerador para todos os armazenados em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos.</span><span class="sxs-lookup"><span data-stu-id="2bbfe-103">Gets an enumerator for all cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bbfe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bbfe-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bbfe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2bbfe-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="2bbfe-106">[out] Um ponteiro para um [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) objeto de interface que pode enumerar as representações gerenciadas de [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos atualmente carregados no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2bbfe-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bbfe-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2bbfe-107">Requirements</span></span>  
 <span data-ttu-id="2bbfe-108">**Plataformas:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbfe-108">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="2bbfe-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bbfe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bbfe-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bbfe-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bbfe-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bbfe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bbfe-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bbfe-112">See also</span></span>
- [<span data-ttu-id="2bbfe-113">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="2bbfe-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
