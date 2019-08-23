---
title: Interface ICorDebugFunction
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917199"
---
# <a name="icordebugfunction-interface"></a>Interface ICorDebugFunction

Representa uma função ou um método gerenciado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Cria um ponto de interrupção no início desta função.|  
|[Método GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Obtém um objeto ICorDebugClass que representa a classe da qual essa função é membro.|  
|[Método GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Obtém o número de versão da edição mais recente feita a esta função.|  
|[Método GetILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Obtém o código da MSIL (Microsoft Intermediate Language) para esta função.|  
|[Método GetLocalVarSigToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Obtém o token de metadados para a assinatura de variável local da função que é representada por `ICorDebugFunction` essa instância.|  
|[Método GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Obtém o módulo no qual essa função é definida.|  
|[Método GetNativeCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Obtém o código nativo para esta função.|  
|[Método GetToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Obtém o token de metadados para esta função.|  
  
## <a name="remarks"></a>Comentários  
 A `ICorDebugFunction` interface não representa uma função com parâmetros de tipo genérico. Por exemplo, uma `ICorDebugFunction` instância representaria `Func<T>` , mas `Func<string>`não. Chame [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) para obter os parâmetros de tipo genérico.  
  
 A relação entre o token de metadados de um `mdMethodDef`método, o e o `ICorDebugFunction` objeto de um método depende se editar e continuar é permitido na função:  
  
- Se editar e continuar não for permitido na função, existirá uma relação um-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token. Ou seja, a função tem um `ICorDebugFunction` objeto e um `mdMethodDef` token.  
  
- Se editar e continuar for permitido na função, existirá uma relação muitos-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token. Ou seja, a função pode ter muitas instâncias de `ICorDebugFunction`, uma para cada versão da função, mas apenas um `mdMethodDef` token.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca**  CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
