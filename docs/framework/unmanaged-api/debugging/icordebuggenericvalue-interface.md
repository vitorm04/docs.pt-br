---
title: Interface ICorDebugGenericValue
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: e60d4b128bf03ff81863e0c95815b2c204807583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794464"
---
# <a name="icordebuggenericvalue-interface"></a>Interface ICorDebugGenericValue

Uma subclasse de "ICorDebugValue" que se aplica a todos os valores. Essa interface fornece métodos Get e Set para o valor.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetValue](icordebuggenericvalue-getvalue-method.md)|Copia o valor no buffer especificado.|  
|[Método SetValue](icordebuggenericvalue-setvalue-method.md)|Copia um novo valor do buffer especificado.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugGenericValue` é uma subinterface porque ela não é remota.  
  
 Para tipos de referência, o valor é a referência em vez do conteúdo da referência.  
  
 Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
