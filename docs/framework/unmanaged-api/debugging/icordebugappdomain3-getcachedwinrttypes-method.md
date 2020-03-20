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
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>Método ICorDebugAppDomain3::GetCachedWinRTTypes
Obtém um enumerador para todos os tipos de tempo de execução do Windows em cache.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a>parâmetros  
 `ppGuidToTypeEnum`  
 [fora] Um ponteiro para um objeto de interface [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) que pode enumerar as representações gerenciadas dos tipos de tempo de execução do Windows atualmente carregados no domínio do aplicativo.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Tempo de execução do Windows  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugAppDomain3](icordebugappdomain3-interface.md)
