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
ms.openlocfilehash: 00c9939b25f395010f6ea5832b405c3e9928a223
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792020"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a>Método ICorDebugRegisterSet2::GetRegistersAvailable
Obtém uma matriz de bytes que fornece um bitmap dos registros disponíveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `numChunks`  
 no O tamanho da matriz de `availableRegChunks`.  
  
 `availableRegChunks`  
 fora Uma matriz de bytes, cada bit corresponde a um registro. Se um registro estiver disponível, o bit correspondente do registro será definido.  
  
## <a name="remarks"></a>Comentários  
 Os valores da enumeração CorDebugRegister especificam os registros de diferentes microprocessadores. Os cinco bits superiores de cada valor são o índice na matriz de `availableRegChunks` de bytes. Os três bits inferiores de cada valor identificam a posição do bit dentro do byte indexado. Dado um valor `CorDebugRegister` que especifica um registro específico, a posição do registro na máscara é determinada da seguinte maneira:  
  
1. Extraia o índice necessário para acessar o byte correto na matriz de `availableRegChunks`:  
  
     `CorDebugRegister` valor > > 3  
  
2. Extraia a posição do bit dentro do byte indexado, em que bit zero é o bit menos significativo:  
  
     valor `CorDebugRegister` & 7  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
- [Interface ICorDebugRegisterSet](icordebugregisterset-interface.md)
