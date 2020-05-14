---
title: 'Método ICorDebugVirtualUnwinder:: Next'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 55f10a6148f0b11cf74492afe947d5921a1d1458
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396421"
---
# <a name="icordebugvirtualunwindernext-method"></a>Método ICorDebugVirtualUnwinder:: Next
Avança para o contexto do chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parâmetros  
 Nenhum.  
  
## <a name="return-value"></a>Valor retornado  
 `S_OK`Se o desenrolar tiver ocorrido com êxito ou `CORDBG_S_AT_END_OF_STACK` se o desenrolamento não puder ser concluído porque não há mais quadros.  
  
 Se um HRESULT com falha for retornado, as APIs do ICorDebug serão retornadas `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Comentários  
 O Stack Walker deve garantir que ele faça o andamento do encaminhamento, de modo que, eventualmente, uma chamada para retornará `Next` um HRESULT com falha ou `CORDBG_S_AT_END_OF_STACK` . Retornar `S_OK` indefinidamente pode causar um loop infinito.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
