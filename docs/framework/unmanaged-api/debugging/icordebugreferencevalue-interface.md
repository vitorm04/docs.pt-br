---
title: Interface ICorDebugReferenceValue
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
ms.openlocfilehash: 4709d1b8126436d4400c788891960100915cd1bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971424"
---
# <a name="icordebugreferencevalue-interface"></a>Interface ICorDebugReferenceValue
Fornece métodos que gerenciam um valor que é uma referência a um objeto. (Ou seja, essa interface fornece métodos que gerenciam um ponteiro). Essa interface implementa "ICorDebugValue".  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dereference](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|Obtém o objeto referenciado.|  
|[Método DereferenceStrong](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|Não implementado. Não chame este método.|  
|[Método GetValue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|Obtém o endereço de memória atual do objeto referenciado.|  
|[Método IsNull](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo, caso em que o `ICorDebugReferenceValue` não aponta para um objeto.|  
|[Método SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|Define o endereço de memória atual. Ou seja, esse método define isso `ICorDebugReferenceValue` para apontar para um objeto.|  
  
## <a name="remarks"></a>Comentários  
 O common language runtime (CLR) pode fazer uma coleta de lixo nos objetos quando o processo depurado é continuado. A coleta de lixo pode mover objetos na memória. Um `ICorDebugReferenceValue` será um cooperar com a coleta de lixo para que suas informações são atualizadas após a coleta de lixo, ou ser invalidado implicitamente antes da coleta de lixo.  
  
 O `ICorDebugReferenceValue` objeto pode ser invalidado implicitamente depois que o processo depurado foi continuado. A derivada "ICorDebugHandleValue" não é invalidado até que ele é liberado explicitamente ou exposto.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também


- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
