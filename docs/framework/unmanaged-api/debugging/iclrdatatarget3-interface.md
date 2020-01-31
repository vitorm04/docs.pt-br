---
title: Interface ICLRDataTarget3
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: f7635dc3fad9b3de30fa052c7d2e67a7e6953fb3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789050"
---
# <a name="iclrdatatarget3-interface"></a>Interface ICLRDataTarget3
Uma subclasse de [ICLRDataTarget2](iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetExceptionRecord](iclrdatatarget3-getexceptionrecord-method.md)|Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.|  
|[Método GetExceptionContextRecord](iclrdatatarget3-getexceptioncontextrecord-method.md)|Chamado pelo serviço de acesso a dados do CLR para recuperar o registro de contexto associado ao processo de destino.|  
|[Método GetExceptionThreadID](iclrdatatarget3-getexceptionthreadid-method.md)|Chamado pelos serviços de acesso a dados do CLR para obter o ID do thread que lança a exceção.|  
  
## <a name="remarks"></a>Comentários  
 O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico. Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória. O destino pode não oferecer suporte à modificação de suas regiões de memória.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** ClrData. idl, ClrData. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRDataTarget](iclrdatatarget-interface.md)
- [Interface ICLRDataTarget2](iclrdatatarget2-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
