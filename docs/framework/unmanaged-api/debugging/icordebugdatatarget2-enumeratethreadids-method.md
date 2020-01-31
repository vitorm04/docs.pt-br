---
title: Método ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 74d4905f2b386f8e0345e4300dd2c8c6d0c882ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783649"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>Método ICorDebugDataTarget2::EnumerateThreadIDs
Retorna uma lista de IDs de thread ativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 cThreadIDs  
 [in] O número máximo de threads cujos IDs podem ser retornados.  
  
 pcThreadIds  
 [out] Um ponteiro para um `ULONG32` que indica o número real de IDs de thread gravadas na matriz `pThreadIds`.  
  
 pThreadIDs  
 Uma matriz de identificadores de thread.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** Consulte [requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md). **Cabeçalho:** CorDebug. idl, CorDebug. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugDataTarget2](icordebugdatatarget2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
