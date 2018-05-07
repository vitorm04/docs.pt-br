---
title: ICorDebugReferenceValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6cdfa9f3717e4025ff6f4fe6da3c1457cdebf7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugreferencevalue-interface1"></a>ICorDebugReferenceValue Interface1
Fornece métodos que gerenciar um valor que é uma referência a um objeto. (Ou seja, essa interface fornece métodos que gerencia um ponteiro). Essa interface implementa "ICorDebugValue".  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dereference](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Obtém o objeto referenciado.|  
|[Método DereferenceStrong](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Não implementado. Não chame este método.|  
|[Método GetValue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Obtém o endereço de memória atual do objeto referenciado.|  
|[Método IsNull](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo, caso em que o `ICorDebugReferenceValue` não aponta para um objeto.|  
|[Método SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Define o endereço de memória atual. Ou seja, esse método define esta `ICorDebugReferenceValue` para apontar para um objeto.|  
  
## <a name="remarks"></a>Comentários  
 O common language runtime (CLR) pode fazer uma coleta de lixo nos objetos quando o processo depurado é continuado. A coleta de lixo pode mover objetos na memória. Um `ICorDebugReferenceValue` será um cooperam com a coleta de lixo para que suas informações são atualizadas após a coleta de lixo, ou serem invalidado implicitamente antes da coleta de lixo.  
  
 O `ICorDebugReferenceValue` objeto pode ser invalidado implicitamente depois do processo depurado continuou. Derivada "ICorDebugHandleValue" não é invalidado até ele ser explicitamente liberado ou exposto.  
  
> [!NOTE]
>  Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
    
    
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
