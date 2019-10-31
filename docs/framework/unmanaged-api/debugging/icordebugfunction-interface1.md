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
ms.openlocfilehash: eb2b1e218314be01898ce90c4378fb713f9bf6ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137860"
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
|[Método GetLocalVarSigToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Obtém o token de metadados para a assinatura de variável local da função que é representada por essa instância de `ICorDebugFunction`.|  
|[Método GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Obtém o módulo no qual essa função é definida.|  
|[Método GetNativeCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Obtém o código nativo para esta função.|  
|[Método GetToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Obtém o token de metadados para esta função.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugFunction` não representa uma função com parâmetros de tipo genérico. Por exemplo, uma instância de `ICorDebugFunction` representaria `Func<T>`, mas não `Func<string>`. Chame [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) para obter os parâmetros de tipo genérico.  
  
 A relação entre o token de metadados de um método, `mdMethodDef`, e o objeto de `ICorDebugFunction` de um método depende de a permissão para editar e continuar na função:  
  
- Se editar e continuar não for permitido na função, existirá uma relação um-para-um entre o objeto `ICorDebugFunction` e o token de `mdMethodDef`. Ou seja, a função tem um objeto `ICorDebugFunction` e um token `mdMethodDef`.  
  
- Se editar e continuar for permitido na função, existirá uma relação muitos-para-um entre o objeto `ICorDebugFunction` e o token de `mdMethodDef`. Ou seja, a função pode ter muitas instâncias de `ICorDebugFunction`, uma para cada versão da função, mas apenas um token de `mdMethodDef`.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:**  CorGuids. lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
