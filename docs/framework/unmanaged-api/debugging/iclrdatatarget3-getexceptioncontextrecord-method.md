---
title: "ICLRDataTarget3::Método GetExceptionContextRecord"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetContextRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 517e2a692c3b67a85bc24437dd5fbaedd5fc7254
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::Método GetExceptionContextRecord
Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de contexto associado ao processo de destino. Por exemplo, para um destino de despejo de memória, isso seria equivalente para o registro de contexto passado por meio de `ExceptionParam` argumento para o [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) função na biblioteca do Windows depurar ajuda (DbgHelp).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bufferSize`  
 [in] O tamanho do buffer de entrada, em bytes. Deve ser grande o suficiente para acomodar o registro de contexto.  
  
 `bufferUsed`  
 [out] Um ponteiro para um tipo `ULONG32` que recebe o número de bytes realmente gravados no buffer.  
  
 `buffer`  
 [out] Um ponteiro para um buffer de memória que recebe uma cópia do registro de contexto. O registro de exceção é retornado como um [contexto](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) tipo.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha. Os códigos `HRESULT` podem incluir, entre outros:  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|`S_OK`|O método foi bem-sucedido. O registro de contexto foi copiado no buffer de saída.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nenhum registro de contexto está associado ao destino.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|O tamanho do buffer de entrada não é grande o suficiente para acomodar o registro de contexto.|  
  
## <a name="remarks"></a>Comentários  
 [CONTEXTO](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) é uma estrutura específica de plataforma definida em cabeçalhos fornecidos pelo SDK do Windows.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget3](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [Método GetExceptionRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [Método GetExceptionThreadID](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
