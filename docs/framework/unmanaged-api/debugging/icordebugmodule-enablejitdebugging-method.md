---
title: Método ICorDebugModule::EnableJITDebugging
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
ms.openlocfilehash: da532ee1b5909a68bedbb9e6f6c96333e88002a8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109720"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>Método ICorDebugModule::EnableJITDebugging
Controla se o compilador JIT (just-in-time) preserva informações de depuração para métodos dentro deste módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bTrackJITInfo`  
 no Defina esse valor como `true` para permitir que o compilador JIT preserve informações de mapeamento entre a versão da Microsoft Intermediate Language (MSIL) e a versão compilada em JIT de cada método neste módulo.  
  
 `bAllowJitOpts`  
 no Defina esse valor como `true` para permitir que o compilador JIT gere código com determinadas otimizações específicas de JIT para depuração.  
  
## <a name="remarks"></a>Comentários  
 A depuração JIT é habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo. Habilitar ou desabilitar programaticamente as configurações substitui as configurações globais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
