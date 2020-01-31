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
ms.openlocfilehash: ecd4ad31b8dad55e9538642a4dc652341bc84b97
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784670"
---
# <a name="icordebugassembly-interface"></a>Interface ICorDebugAssembly

Representa um assembly.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumerateModules](icordebugassembly-enumeratemodules-method.md)|Obtém um enumerador para os módulos contidos no assembly.|  
|[Método GetAppDomain](icordebugassembly-getappdomain-method.md)|Obtém um ponteiro de interface para o domínio do aplicativo que contém esta instância de `ICorDebugAssembly`.|  
|[Método GetCodeBase](icordebugassembly-getcodebase-method.md)|Não implementado na versão atual do .NET Framework.|  
|[Método GetName](icordebugassembly-getname-method.md)|Obtém o nome do assembly.|  
|[Método GetProcess](icordebugassembly-getprocess-method.md)|Obtém a instância ICorDebugProcess na qual o assembly está em execução.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
