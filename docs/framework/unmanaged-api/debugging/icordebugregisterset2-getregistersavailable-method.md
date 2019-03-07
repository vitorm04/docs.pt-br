---
title: Método ICorDebugRegisterSet2::GetRegistersAvailable
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ffa862ebe631471030e1e87a28645e278062d18
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469112"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>Método ICorDebugRegisterSet2::GetRegistersAvailable
Obtém uma matriz de bytes que fornece um bitmap de registros disponíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `numChunks`  
 [in] O tamanho do `availableRegChunks` matriz.  
  
 `availableRegChunks`  
 [out] Uma matriz de bytes, cada bit que corresponde a um registro. Se um registro estiver disponível, o bit correspondente do registro é definido.  
  
## <a name="remarks"></a>Comentários  
 Os valores da enumeração CorDebugRegister especificam os registros de microprocessadores diferentes. Os cinco bits superiores de cada valor são o índice para o `availableRegChunks` matriz de bytes. Três bits inferiores de cada valor de identificar a posição de bit dentro do byte indexada. Dado um `CorDebugRegister` valor que especifica um registro específico, a posição do registro na máscara é determinado da seguinte maneira:  
  
1.  Extrair o índice necessário para acessar o byte correto no `availableRegChunks` matriz:  
  
     `CorDebugRegister` valor >> 3  
  
2.  Extrai a posição de bit dentro do byte indexada, em que o bit de zero é o bit menos significativo:  
  
     `CorDebugRegister` valor & 7  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [Interface ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
