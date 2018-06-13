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
ms.openlocfilehash: 71722293bfb80a7e57393916560f922d970ea2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415636"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>Método ICorDebugModule::EnableJITDebugging
Controla se o compilador just-in-time (JIT) preserva as informações de depuração para métodos neste módulo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `bTrackJITInfo`  
 [in] Defina esse valor como `true` para habilitar o compilador JIT preservar as informações de mapeamento entre a versão do Microsoft intermediate language (MSIL) e a versão da compilação JIT de cada método neste módulo.  
  
 `bAllowJitOpts`  
 [in] Defina esse valor como `true` para habilitar o compilador JIT gerar o código com certas otimizações JIT específicos para depuração.  
  
## <a name="remarks"></a>Comentários  
 A depuração JIT está habilitada por padrão para todos os módulos que são carregados quando o depurador está ativo. Habilitar ou desabilitar as configurações de programaticamente substitui configurações globais.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
