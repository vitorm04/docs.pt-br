---
title: ICLRDataTarget3::Método GetExceptionThreadID
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6503efbaa4db89b243a85b69f60b091c6bb49ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215294"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a>ICLRDataTarget3::Método GetExceptionThreadID
Chamado pelos serviços de acesso a dados do CLR (Common Language Runtime) para obter a ID do segmento que gerou a exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
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
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRDataTarget3](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [Método GetExceptionContextRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [Método GetExceptionRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
