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
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124068"
---
# <a name="icordebugframe-interface"></a>Interface ICorDebugFrame

Representa um quadro na pilha atual.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateStepper](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|Obtém um ICorDebugStepper para executar operações de depuração relativas a esse `ICorDebugFrame`.|  
|[Método GetCallee](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|Obtém um ponteiro para a `ICorDebugFrame` na cadeia atual que esse quadro chamou ou retorna NULL se esse for o quadro interno na cadeia.|  
|[Método GetCaller](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|Obtém um ponteiro para a `ICorDebugFrame` na cadeia atual que chamou esse quadro ou retorna NULL se esse for o quadro mais externo na cadeia.|  
|[Método GetChain](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|Obtém um ponteiro para o ICorDebugChain para o qual este `ICorDebugFrame` faz parte.|  
|[Método GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|Obtém um ponteiro para o ICorDebugCode associado a este quadro de pilhas.|  
|[Método GetFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|Obtém um ponteiro para o ICorDebugFunction que contém o código associado a esse quadro de pilhas.|  
|[Método GetFunctionToken](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|Obtém o token de metadados para a função que contém o código associado a esse quadro de pilha.|  
|[Método GetStackRange](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|Obtém o intervalo de endereços absolutos do registro de ativação representado por este `ICorDebugFrame`.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
