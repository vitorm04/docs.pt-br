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
ms.openlocfilehash: 2efba22b4ec372c5ddedd4982a29d66945d3511c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792128"
---
# <a name="icordebugreferencevalue-interface"></a>Interface ICorDebugReferenceValue
Fornece métodos que gerenciam um valor que é uma referência a um objeto. (Ou seja, essa interface fornece métodos que gerenciam um ponteiro.) Essa interface implementa "ICorDebugValue".  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dereference](icordebugreferencevalue-dereference-method.md)|Obtém o objeto que é referenciado.|  
|[Método DereferenceStrong](icordebugreferencevalue-dereferencestrong-method.md)|Não implementado. Não chame esse método.|  
|[Método GetValue](icordebugreferencevalue-getvalue-method.md)|Obtém o endereço de memória atual do objeto referenciado.|  
|[Método IsNull](icordebugreferencevalue-isnull-method.md)|Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo; nesse caso, o `ICorDebugReferenceValue` não aponta para um objeto.|  
|[Método SetValue](icordebugreferencevalue-setvalue-method.md)|Define o endereço de memória atual. Ou seja, esse método define esse `ICorDebugReferenceValue` para apontar para um objeto.|  
  
## <a name="remarks"></a>Comentários  
 O Common Language Runtime (CLR) pode fazer uma coleta de lixo em objetos quando o processo depurado é continuado. A coleta de lixo pode mover objetos na memória. Um `ICorDebugReferenceValue` irá cooperar com a coleta de lixo para que suas informações sejam atualizadas após a coleta de lixo, ou elas serão invalidadas implicitamente antes da coleta de lixo.  
  
 O objeto `ICorDebugReferenceValue` pode ser implicitamente invalidado depois que o processo depurado tiver sido continuado. O "ICorDebugHandleValue" derivado não será invalidado até ser liberado ou exposto explicitamente.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
