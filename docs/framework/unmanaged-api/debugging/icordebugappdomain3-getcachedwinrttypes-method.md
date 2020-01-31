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
ms.openlocfilehash: 55d0b40bbdb5628f60090d9d70f7dccbebe9d58f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784993"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="c6583-102">Método ICorDebugAppDomain3::GetCachedWinRTTypes</span><span class="sxs-lookup"><span data-stu-id="c6583-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="c6583-103">Obtém um enumerador para todos os tipos de Windows Runtime em cache.</span><span class="sxs-lookup"><span data-stu-id="c6583-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6583-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6583-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6583-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6583-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="c6583-106">fora Um ponteiro para um objeto de interface [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) que pode enumerar as representações gerenciadas dos tipos de Windows Runtime atualmente carregados no domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6583-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6583-107">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c6583-107">Requirements</span></span>  
 <span data-ttu-id="c6583-108">**Plataformas:** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="c6583-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="c6583-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6583-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6583-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6583-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6583-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6583-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6583-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="c6583-112">See also</span></span>

- [<span data-ttu-id="c6583-113">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="c6583-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
