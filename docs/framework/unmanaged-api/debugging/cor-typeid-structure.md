---
title: Estrutura COR_TYPEID
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPEID
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPEID
helpviewer_keywords: COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca6c9b3b02314843a3eaf01d8cd4a9eac5513efa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cortypeid-structure"></a>Estrutura COR_TYPEID
Contém um identificador de tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`token1`|O primeiro token.|  
|`token2`|O segundo token.|  
  
## <a name="remarks"></a>Comentários  
 O `COR_TYPEID` estrutura é retornada por um número de métodos de depuração que fornecem informações sobre objetos a serem coletados como lixo. Ele pode ser passado como um argumento para outros métodos de depuração que fornecem informações adicionais sobre esse item. Por exemplo, enumerando uma [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) do objeto, você pode recuperar individuais [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objetos que representam objetos individuais no heap gerenciado. Você pode passar o `COR_TYPEID` o valor do `COR_HEAPOBJECT.type` campo para o [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) método para recuperar um objeto de ICorDebugType que fornece informações sobre o objeto de tipo.  
  
 Um `COR_TYPEID` objeto deve ser opaco. Seus campos individuais não devem ser acessados ou manipulados. Seu uso exclusivo é como um identificador que é fornecido como um `out` parâmetro em uma chamada de método e que pode, por sua vez, ser passado para outros métodos para fornecer informações adicionais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Depuração](../../../../docs/framework/unmanaged-api/debugging/index.md)
