---
title: "Método ICorDebugModule::EnableJITDebugging"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
