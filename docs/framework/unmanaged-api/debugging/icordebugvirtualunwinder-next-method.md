---
title: 'Método ICorDebugVirtualUnwinder:: Next'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790811"
---
# <a name="icordebugvirtualunwindernext-method"></a>Método ICorDebugVirtualUnwinder:: Next
Avança para o contexto do chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parâmetros  
 Nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se o desenrolar tiver ocorrido com êxito ou `CORDBG_S_AT_END_OF_STACK` se o desenrolamento não puder ser concluído porque não há mais quadros.  
  
 Se um HRESULT com falha for retornado, as APIs ICorDebug retornarão `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Comentários  
 O Stack Walker deve garantir que ele faça o andamento do encaminhamento, de modo que, eventualmente, uma chamada para `Next` retornará um HRESULT ou `CORDBG_S_AT_END_OF_STACK`com falha. Retornar `S_OK` indefinidamente pode causar um loop infinito.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
