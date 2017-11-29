---
title: "ICLRDataTarget3::Método GetExceptionThreadID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionThreadID
api_location: mscordbi.dll
api_type: COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f05d264d4bf55de930a07eda6bf369570c8b7fa8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a>ICLRDataTarget3::Método GetExceptionThreadID
Chamado pelos serviços de acesso a dados do CLR (Common Language Runtime) para obter a ID do segmento que gerou a exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadID`  
 [out] A ID do thread que acionou a exceção.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha. Os códigos `HRESULT` podem incluir, entre outros:  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|`S_OK`|O método foi bem-sucedido.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Não foi possível encontrar uma ID de thread válida para a exceção.|  
  
## <a name="remarks"></a>Comentários  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget3](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [Método GetExceptionContextRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [Método GetExceptionRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
