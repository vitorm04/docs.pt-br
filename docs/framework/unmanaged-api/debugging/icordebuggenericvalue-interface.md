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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988670"
---
# <a name="icordebuggenericvalue-interface"></a>Interface ICorDebugGenericValue

Uma subclasse de "ICorDebugValue" que se aplica a todos os valores. Essa interface fornece métodos Get e Set para o valor.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|Copia o valor para o buffer especificado.|  
|[Método SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|Copia um novo valor de buffer especificado.|  
  
## <a name="remarks"></a>Comentários  
 `ICorDebugGenericValue` é uma interface de subpropriedades porque ele é não remotas.  
  
 Para tipos de referência, o valor é a referência em vez do conteúdo de referência.  
  
 Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
