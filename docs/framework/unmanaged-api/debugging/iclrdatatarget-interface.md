---
title: Interface ICLRDataTarget
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 30806394a8895084068acaec6f7d03c6b67bb14b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860572"
---
# <a name="iclrdatatarget-interface"></a>Interface ICLRDataTarget
Fornece métodos para interação com um item de destino do Common Language Runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetCurrentThreadID](iclrdatatarget-getcurrentthreadid-method.md)|Obtém o identificador do sistema operacional para o thread atual.|  
|[Método GetImageBase](iclrdatatarget-getimagebase-method.md)|Obtém o endereço de memória base da imagem especificada.|  
|[Método GetMachineType](iclrdatatarget-getmachinetype-method.md)|Obtém um identificador para o tipo de instrução que o processo de destino está usando.|  
|[Método GetPointerSize](iclrdatatarget-getpointersize-method.md)|Obtém o tamanho, em bytes, de um ponteiro para o destino atual.|  
|[Método GetThreadContext](iclrdatatarget-getthreadcontext-method.md)|Obtém um ponteiro para o contexto do thread com o identificador especificado.|  
|[Método GetTLSValue](iclrdatatarget-gettlsvalue-method.md)|Obtém um valor no armazenamento local de thread (TLS) no índice especificado para o thread especificado.|  
|[Método ReadVirtual](iclrdatatarget-readvirtual-method.md)|Lê dados do endereço de memória virtual especificado no buffer especificado.|  
|[Método Request](iclrdatatarget-request-method.md)|Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para solicitar uma operação, conforme definido pela implementação.|  
|[Método SetThreadContext](iclrdatatarget-setthreadcontext-method.md)|Define o contexto atual do thread especificado no processo de destino.|  
|[Método SetTLSValue](iclrdatatarget-settlsvalue-method.md)|Define um valor no armazenamento local de threads (TLS) do thread especificado no processo de destino.|  
|[Método WriteVirtual](iclrdatatarget-writevirtual-method.md)|Grava dados do buffer especificado para o endereço de memória virtual especificado.|  
  
## <a name="remarks"></a>Comentários  
 O cliente de API (ou seja, o depurador) deve implementar essa interface conforme apropriado para o item de destino específico. Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICLRDataTarget2](iclrdatatarget2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
