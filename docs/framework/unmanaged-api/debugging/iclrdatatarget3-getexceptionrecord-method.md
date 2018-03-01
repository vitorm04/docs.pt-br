---
title: "Método ICLRDataTarget3::GetExceptionRecord"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e78131eda9d10646a881dbbd4e3f7a4aaf8f607
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>Método ICLRDataTarget3::GetExceptionRecord
Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino. Por exemplo, para um destino de despejo de memória, isso seria equivalente para o registro de exceção transmitido por meio de `ExceptionParam` argumento para o [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) função na biblioteca do Windows depurar ajuda (DbgHelp).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bufferSize`  
 [in] O tamanho do buffer de entrada, em bytes. Isso deve ser igual a `sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.  
  
 `bufferUsed`  
 [out] Um ponteiro para um tipo `ULONG32` que recebe o número de bytes realmente gravados no buffer.  
  
 `buffer`  
 [out] Um ponteiro para um buffer de memória que recebe uma cópia do registro de exceção. O registro de exceção é retornado como um [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) tipo.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha. Os códigos `HRESULT` podem incluir, entre outros:  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|`S_OK`|O método foi bem-sucedido. O registro de exceção foi copiado para o buffer de saída.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nenhum registro de exceção está associado ao destino.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|O tamanho do buffer de entrada não é igual à `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Comentários  
 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) é uma estrutura definida em dbghelp.h e imagehlp.h no SDK do Windows.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget3](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [Método GetExceptionContextRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [Método GetExceptionThreadID](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
