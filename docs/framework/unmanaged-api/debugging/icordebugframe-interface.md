---
title: Interface ICorDebugFrame
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937002"
---
# <a name="icordebugframe-interface"></a>Interface ICorDebugFrame

Representa um quadro na pilha atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Obtém um ICorDebugStepper para executar operações de depuração relativas a `ICorDebugFrame`isso.|  
|[Método GetCallee](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Obtém um ponteiro para o `ICorDebugFrame` na cadeia atual que este quadro chamou ou retorna NULL se esse for o quadro interno na cadeia.|  
|[Método GetCaller](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Obtém um ponteiro para o `ICorDebugFrame` na cadeia atual que chamou esse quadro ou retorna NULL se esse for o quadro mais externo na cadeia.|  
|[Método GetChain](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Obtém um ponteiro para o ICorDebugChain `ICorDebugFrame` que faz parte de.|  
|[Método GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Obtém um ponteiro para o ICorDebugCode associado a este quadro de pilhas.|  
|[Método GetFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Obtém um ponteiro para o ICorDebugFunction que contém o código associado a esse quadro de pilhas.|  
|[Método GetFunctionToken](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Obtém o token de metadados para a função que contém o código associado a esse quadro de pilha.|  
|[Método GetStackRange](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Obtém o intervalo de endereços absolutos do quadro de pilha representado `ICorDebugFrame`por isso.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
