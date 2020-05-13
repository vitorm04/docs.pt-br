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
ms.openlocfilehash: 6b7b6969c1f207decbf47217e98b7fee3aa9ce54
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213229"
---
# <a name="icordebugfunction-interface"></a>Interface ICorDebugFunction

Representa uma função ou um método gerenciado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](icordebugfunction-createbreakpoint-method.md)|Cria um ponto de interrupção no início desta função.|  
|[Método GetClass](icordebugfunction-getclass-method.md)|Obtém um objeto ICorDebugClass que representa a classe da qual essa função é membro.|  
|[Método GetCurrentVersionNumber](icordebugfunction-getcurrentversionnumber-method.md)|Obtém o número de versão da edição mais recente feita a esta função.|  
|[Método GetILCode](icordebugfunction-getilcode-method.md)|Obtém o código da MSIL (Microsoft Intermediate Language) para esta função.|  
|[Método GetLocalVarSigToken](icordebugfunction-getlocalvarsigtoken-method.md)|Obtém o token de metadados para a assinatura de variável local da função que é representada por essa `ICorDebugFunction` instância.|  
|[Método GetModule](icordebugfunction-getmodule-method.md)|Obtém o módulo no qual essa função é definida.|  
|[Método GetNativeCode](icordebugfunction-getnativecode-method.md)|Obtém o código nativo para esta função.|  
|[Método GetToken](icordebugfunction-gettoken-method.md)|Obtém o token de metadados para esta função.|  
  
## <a name="remarks"></a>Comentários  
 A `ICorDebugFunction` interface não representa uma função com parâmetros de tipo genérico. Por exemplo, uma `ICorDebugFunction` instância representaria `Func<T>` , mas não `Func<string>` . Chame [ICorDebugILFrame2:: EnumerateTypeParameters](icordebugilframe2-enumeratetypeparameters-method.md) para obter os parâmetros de tipo genérico.  
  
 A relação entre o token de metadados de um método, o `mdMethodDef` e o objeto de um método `ICorDebugFunction` depende se editar e continuar é permitido na função:  
  
- Se editar e continuar não for permitido na função, existirá uma relação um-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token. Ou seja, a função tem um `ICorDebugFunction` objeto e um `mdMethodDef` token.  
  
- Se editar e continuar for permitido na função, existirá uma relação muitos-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token. Ou seja, a função pode ter muitas instâncias de `ICorDebugFunction` , uma para cada versão da função, mas apenas um `mdMethodDef` token.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:**  CorGuids. lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
