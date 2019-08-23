---
title: 'Método ICorDebugVirtualUnwinder:: Next'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a3d4bac42731bc94ecef7a0756392c8c0882fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967930"
---
# <a name="icordebugvirtualunwindernext-method"></a>Método ICorDebugVirtualUnwinder:: Next
Avança para o contexto do chamador.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parâmetros  
 nenhuma.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK`Se o desenrolar tiver ocorrido com `CORDBG_S_AT_END_OF_STACK` êxito ou se o desenrolamento não puder ser concluído porque não há mais quadros.  
  
 Se um HRESULT com falha for retornado, as APIs do `CORDBG_E_DATA_TARGET_ERROR`ICorDebug serão retornadas.  
  
## <a name="remarks"></a>Comentários  
 O Stack Walker deve garantir que ele faça o andamento do encaminhamento, de modo que `Next` , eventualmente, uma chamada para `CORDBG_S_AT_END_OF_STACK`retornará um HRESULT com falha ou. Retornar `S_OK` indefinidamente pode causar um loop infinito.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
