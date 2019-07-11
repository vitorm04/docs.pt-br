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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aeb6ed448539db2720fee0d42cfcc344fd3bbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762767"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>Método ICorDebugModule::EnableJITDebugging
Controla se o compilador just-in-time (JIT) preserva informações de depuração para métodos neste módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bTrackJITInfo`  
 [in] Defina esse valor como `true` para habilitar o compilador JIT preservar as informações de mapeamento entre a versão do Microsoft intermediate language (MSIL) e a versão de cada método neste módulo compilado por JIT.  
  
 `bAllowJitOpts`  
 [in] Defina esse valor como `true` para habilitar o compilador JIT gerar código com determinadas otimizações JIT específicas para a depuração.  
  
## <a name="remarks"></a>Comentários  
 Depuração JIT é habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo. Programaticamente habilitando ou desabilitando as configurações de substituições de configurações globais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
