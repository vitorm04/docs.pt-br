---
title: Método ICLRDataTarget3::GetExceptionRecord
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b667ac16a4bbe6bdab1814b66fb1121b34b2d945
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039579"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a>Método ICLRDataTarget3::GetExceptionRecord
Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino. Por exemplo, para um destino de despejo, isso seria equivalente ao registro de exceção passado por meio do `ExceptionParam` argumento para a função [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) na biblioteca de ajuda de depuração do Windows (dbghelp).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bufferSize`  
 [in] O tamanho do buffer de entrada, em bytes. Isso deve ser igual a `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.  
  
 `bufferUsed`  
 [out] Um ponteiro para um tipo `ULONG32` que recebe o número de bytes realmente gravados no buffer.  
  
 `buffer`  
 [out] Um ponteiro para um buffer de memória que recebe uma cópia do registro de exceção. O registro de exceção é retornado como um tipo [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) .  
  
## <a name="return-value"></a>Valor de retorno  
 O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha. Os códigos `HRESULT` podem incluir, entre outros:  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|`S_OK`|O método foi bem-sucedido. O registro de exceção foi copiado para o buffer de saída.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nenhum registro de exceção está associado ao destino.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|O tamanho do buffer de entrada não é igual à `sizeof(MINIDUMP_EXCEPTION)`.|  
  
## <a name="remarks"></a>Comentários  
 [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) é uma estrutura definida em dbghelp. h e imagehlp. h no SDK do Windows.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRDataTarget3](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [Método GetExceptionContextRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [Método GetExceptionThreadID](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
