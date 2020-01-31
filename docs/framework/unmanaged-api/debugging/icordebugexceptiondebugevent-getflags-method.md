---
title: 'Método ICorDebugExceptionDebugEvent:: GetFlags'
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782914"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a>Método ICorDebugExceptionDebugEvent:: GetFlags
Obtém um sinalizador que indica se a exceção pode ser interceptada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pdwFlags`  
 fora Um ponteiro para um valor [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) que indica se a exceção pode ser interceptada.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
