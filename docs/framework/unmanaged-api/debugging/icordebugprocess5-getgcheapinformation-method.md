---
title: "Método ICorDebugProcess5::GetGCHeapInformation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 70e9e3ab6c7332e492b7146e52e0265653803bf7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>Método ICorDebugProcess5::GetGCHeapInformation
Fornece informações gerais sobre o heap de coleta de lixo, incluindo se ele está atualmente enumerável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pHeapInfo`  
 [out] Um ponteiro para um [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) valor que fornece informações gerais sobre o heap de coleta de lixo.  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugProcess5::GetGCHeapInformation` método deve ser chamado antes de enumerar o heap ou regiões de heap individuais para garantir que a coleta de lixo estruturas no processo são válidos no momento. O heap de coleta de lixo não pode ser percorrido durante uma coleção está em andamento. Caso contrário, a enumeração pode capturar as estruturas de coleta de lixo que são inválidas.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
