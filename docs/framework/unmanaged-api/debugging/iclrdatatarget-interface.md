---
title: Interface ICLRDataTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a40276b28f3d20428f0d7eb0556a762fdb56801
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget-interface"></a>Interface ICLRDataTarget
Fornece métodos para interação com um item de destino do common language runtime (CLR).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetCurrentThreadID](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Obtém o identificador de sistema operacional para o thread atual.|  
|[Método GetImageBase](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Obtém o endereço de memória de base para a imagem especificada.|  
|[Método GetMachineType](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Obtém um identificador para o tipo de conjunto de instruções que o processo de destino está usando.|  
|[Método GetPointerSize](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Obtém o tamanho, em bytes, de um ponteiro para o destino atual.|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Obtém um ponteiro para o contexto do thread com o identificador especificado.|  
|[Método GetTLSValue](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Obtém um valor no armazenamento local de thread (TLS) no índice especificado para o segmento especificado.|  
|[Método ReadVirtual](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Lê dados do endereço de memória virtual especificado no buffer especificado.|  
|[Método de solicitação](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Chamado pelos comuns language runtime (CLR) dados serviços de acesso para uma operação de solicitação, conforme definido pela implementação.|  
|[Método SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Define o contexto atual do thread especificado no processo de destino.|  
|[Método SetTLSValue](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Define um valor no armazenamento local de thread (TLS) do thread no processo de destino especificado.|  
|[Método WriteVirtual](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Grava dados de buffer especificado para o endereço de memória virtual especificado.|  
  
## <a name="remarks"></a>Comentários  
 O cliente de API (ou seja, o depurador) deve implementar essa interface conforme apropriado para o item de destino específico. Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData.idl, ClrData.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [Interfaces de depuração](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
