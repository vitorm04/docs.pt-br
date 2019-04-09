---
title: Interface ICorDebugAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd60defc1c003fa4b235ddcb0a78b9a819b1b0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198017"
---
# <a name="icordebugassembly-interface"></a>Interface ICorDebugAssembly

Representa um assembly.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|Obtém um enumerador para os módulos contidos no assembly.|  
|[Método GetAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo que contém este `ICorDebugAssembly` instância.|  
|[Método GetCodeBase](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|Não implementado na versão atual do .NET Framework.|  
|[Método GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|Obtém o nome do assembly.|  
|[Método GetProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|Obtém a instância de ICorDebugProcess no qual o assembly está em execução.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
