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
ms.openlocfilehash: ba0e0b1b2bac785e28f41e09dda74841121a748d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794513"
---
# <a name="icordebugfunction-interface"></a>Interface ICorDebugFunction

Representa uma função ou um método gerenciado.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](icordebugfunction-createbreakpoint-method.md)|Cria um ponto de interrupção no início desta função.|  
|[Método GetClass](icordebugfunction-getclass-method.md)|Obtém um objeto ICorDebugClass que representa a classe da qual essa função é membro.|  
|[Método GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md)|Obtém o número de versão da edição mais recente feita a esta função.|  
|[Método GetILCode](icordebugfunction-getilcode-method.md)|Obtém o código da MSIL (Microsoft Intermediate Language) para esta função.|  
|[Método GetLocalVarSigToken](icordebugfunction-getlocalvarsigtoken-method.md)|Obtém o token de metadados para a assinatura de variável local da função que é representada por essa instância de `ICorDebugFunction`.|  
|[Método GetModule](icordebugfunction-getmodule-method.md)|Obtém o módulo no qual essa função é definida.|  
|[Método GetNativeCode](icordebugfunction-getnativecode-method.md)|Obtém o código nativo para esta função.|  
|[Método GetToken](icordebugfunction-gettoken-method.md)|Obtém o token de metadados para esta função.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugFunction` não representa uma função com parâmetros de tipo genérico. Por exemplo, uma instância de `ICorDebugFunction` representaria `Func<T>`, mas não `Func<string>`. Chame [ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) para obter os parâmetros de tipo genérico.  
  
 A relação entre o token de metadados de um método, `mdMethodDef`, e o objeto de `ICorDebugFunction` de um método depende de a permissão para editar e continuar na função:  
  
- Se editar e continuar não for permitido na função, existirá uma relação um-para-um entre o objeto `ICorDebugFunction` e o token de `mdMethodDef`. Ou seja, a função tem um objeto `ICorDebugFunction` e um token `mdMethodDef`.  
  
- Se editar e continuar for permitido na função, existirá uma relação muitos-para-um entre o objeto `ICorDebugFunction` e o token de `mdMethodDef`. Ou seja, a função pode ter muitas instâncias de `ICorDebugFunction`, uma para cada versão da função, mas apenas um token de `mdMethodDef`.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:**  CorGuids. lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
