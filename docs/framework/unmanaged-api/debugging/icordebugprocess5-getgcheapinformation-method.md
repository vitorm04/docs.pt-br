---
title: Método ICorDebugProcess5::GetGCHeapInformation
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 703f159c5bc6b73dcd0e770bdeb61f676aae034c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792372"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>Método ICorDebugProcess5::GetGCHeapInformation
Fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele é enumerável no momento.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pHeapInfo`  
 fora Um ponteiro para um valor [COR_HEAPINFO](cor-heapinfo-structure.md) que fornece informações gerais sobre o heap de coleta de lixo.  
  
## <a name="remarks"></a>Comentários  
 O método de `ICorDebugProcess5::GetGCHeapInformation` deve ser chamado antes de enumerar o heap ou regiões de heap individuais para garantir que as estruturas de coleta de lixo no processo sejam válidas no momento. O heap de coleta de lixo não pode ser movimentado enquanto uma coleção está em andamento. Caso contrário, a enumeração poderá capturar as estruturas de coleta de lixo que são inválidas.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugProcess5](icordebugprocess5-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
