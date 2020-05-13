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
ms.openlocfilehash: 6c6ff428e378e973d8846674ffacdcd04b2dbdbc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378345"
---
# <a name="icordebugreferencevalue-interface"></a>Interface ICorDebugReferenceValue
Fornece métodos que gerenciam um valor que é uma referência a um objeto. (Ou seja, essa interface fornece métodos que gerenciam um ponteiro.) Essa interface implementa "ICorDebugValue".  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método Dereference](icordebugreferencevalue-dereference-method.md)|Obtém o objeto que é referenciado.|  
|[Método DereferenceStrong](icordebugreferencevalue-dereferencestrong-method.md)|Não implementado. Não chame esse método.|  
|[Método GetValue](icordebugreferencevalue-getvalue-method.md)|Obtém o endereço de memória atual do objeto referenciado.|  
|[Método IsNull](icordebugreferencevalue-isnull-method.md)|Obtém um valor que indica se este `ICorDebugReferenceValue` é um valor nulo; nesse caso, o `ICorDebugReferenceValue` não aponta para um objeto.|  
|[Método SetValue](icordebugreferencevalue-setvalue-method.md)|Define o endereço de memória atual. Ou seja, esse método define isso `ICorDebugReferenceValue` para apontar para um objeto.|  
  
## <a name="remarks"></a>Comentários  
 O Common Language Runtime (CLR) pode fazer uma coleta de lixo em objetos quando o processo depurado é continuado. A coleta de lixo pode mover objetos na memória. Um `ICorDebugReferenceValue` irá cooperar com a coleta de lixo para que suas informações sejam atualizadas após a coleta de lixo, ou elas serão invalidadas implicitamente antes da coleta de lixo.  
  
 O `ICorDebugReferenceValue` objeto pode ser implicitamente invalidado depois que o processo depurado tiver sido continuado. O "ICorDebugHandleValue" derivado não será invalidado até ser liberado ou exposto explicitamente.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
