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
ms.openlocfilehash: e5fd1730bbe5b6f2905691dce41a7f503227534a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179077"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="da287-102">Método ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="da287-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="da287-103">Obtém um enumerador para todos os tipos de tempo de execução do Windows em cache.</span><span class="sxs-lookup"><span data-stu-id="da287-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da287-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="da287-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="da287-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="da287-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="da287-106">[fora] Um ponteiro para um objeto de interface [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) que pode enumerar as representações gerenciadas dos tipos de tempo de execução do Windows atualmente carregados no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="da287-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da287-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="da287-107">Requirements</span></span>  
 <span data-ttu-id="da287-108">**Plataformas:** Tempo de execução do Windows</span><span class="sxs-lookup"><span data-stu-id="da287-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="da287-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da287-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da287-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da287-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da287-111">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da287-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da287-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="da287-112">See also</span></span>

- [<span data-ttu-id="da287-113">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="da287-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
