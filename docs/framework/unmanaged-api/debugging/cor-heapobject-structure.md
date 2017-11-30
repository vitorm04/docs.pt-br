---
title: Estrutura COR_HEAPOBJECT
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_HEAPOBJECT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_HEAPOBJECT
helpviewer_keywords: COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bcd971853707349bf0d60459cb46b0fea1e8a97b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corheapobject-structure"></a>Estrutura COR_HEAPOBJECT
Fornece informações sobre um objeto no heap gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`address`|O endereço do objeto na memória.|  
|`size`|O tamanho total do objeto, em bytes.|  
|`type`|Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token que representa o tipo do objeto.|  
  
## <a name="remarks"></a>Comentários  
 `COR_HEAPOBJECT`instâncias podem ser recuperadas enumerando uma [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objeto de interface que é preenchido com a chamada a [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) método.  
  
 Um `COR_HEAPOBJECT` instância fornece informações sobre um objeto vivo no heap gerenciado ou sobre um objeto que não tem raiz de qualquer objeto, mas que ainda não foram coletado pelo coletor de lixo.  
  
 Para obter melhor desempenho, o `COR_HEAPOBJECT.address` campo é um `CORDB_ADDRESS` valor, em vez de ICorDebugValue valor usado em grande parte da API de depuração da interface. Para obter um objeto ICorDebugValue para um endereço de objeto em questão, você pode passar o `CORDB_ADDRESS` o valor para o [Icordebugprocess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) método.  
  
 Para obter melhor desempenho, o `COR_HEAPOBJECT.type` campo é um `COR_TYPEID` valor, em vez de ICorDebugType valor usado em grande parte da API de depuração da interface. Para obter um objeto ICorDebugType para uma determinado tipo ID, você pode passar o `COR_TYPEID` o valor para o [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) método.  
  
 O `COR_HEAPOBJECT` estrutura inclui uma interface de COM contado por referência. Se você recuperar um `COR_HEAPOBJECT` instância do enumerador chamando o [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) método, posteriormente, você deve liberar a referência.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
