---
title: ICLRDataTarget3::Método GetExceptionContextRecord
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07065b15f449c2bcb84df7bbdcce65d61de007ee
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038343"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a>ICLRDataTarget3::Método GetExceptionContextRecord
Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de contexto associado ao processo de destino. Por exemplo, para um destino de despejo, isso seria equivalente ao registro de contexto passado por meio do `ExceptionParam` argumento para a função [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) na biblioteca de ajuda de depuração do Windows (dbghelp).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bufferSize`  
 [in] O tamanho do buffer de entrada, em bytes. Deve ser grande o suficiente para acomodar o registro de contexto.  
  
 `bufferUsed`  
 [out] Um ponteiro para um tipo `ULONG32` que recebe o número de bytes realmente gravados no buffer.  
  
 `buffer`  
 [out] Um ponteiro para um buffer de memória que recebe uma cópia do registro de contexto. O registro de exceção é retornado como um tipo de [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .  
  
## <a name="return-value"></a>Valor de retorno  
 O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha. Os códigos `HRESULT` podem incluir, entre outros:  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|`S_OK`|O método foi bem-sucedido. O registro de contexto foi copiado no buffer de saída.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nenhum registro de contexto está associado ao destino.|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|O tamanho do buffer de entrada não é grande o suficiente para acomodar o registro de contexto.|  
  
## <a name="remarks"></a>Comentários  
 O [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) é uma estrutura específica da plataforma definida nos cabeçalhos fornecidos pelo SDK do Windows.  
  
 Este método é implementado pelo autor do aplicativo de depuração.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICLRDataTarget3](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [Método GetExceptionRecord](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [Método GetExceptionThreadID](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
