---
title: ICorDebugFunction Interface1
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
ms.openlocfilehash: b810ce8634781438faccac25f96442624a78ea0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676764"
---
# <a name="icordebugfunction-interface1"></a>ICorDebugFunction Interface1
Representa uma função ou um método gerenciado.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CreateBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|Cria um ponto de interrupção no início desta função.|  
|[Método GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|Obtém um objeto ICorDebugClass que representa essa função é um membro da classe.|  
|[Método GetCurrentVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|Obtém o número de versão da edição mais recente feita para essa função.|  
|[Método GetILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|Obtém o código do Microsoft intermediate language (MSIL) para essa função.|  
|[Método GetLocalVarSigToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|Obtém os metadados de token para a assinatura de variável local da função que é representada por esse `ICorDebugFunction` instância.|  
|[Método GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Obtém o módulo no qual essa função é definida.|  
|[Método GetNativeCode](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|Obtém o código nativo para essa função.|  
|[Método GetToken](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|Obtém os metadados de token para essa função.|  
  
## <a name="remarks"></a>Comentários  
 O `ICorDebugFunction` interface não representa uma função com parâmetros de tipo genérico. Por exemplo, um `ICorDebugFunction` instância representariam `Func<T>` , mas não `Func<string>`. Chame [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) para obter os parâmetros de tipo genérico.  
  
 A relação entre o token de metadados de um método `mdMethodDef`e um método `ICorDebugFunction` objeto é dependente de editar e continuar é permitida na função:  
  
-   Se editar e continuar não é permitida na função, existe uma relação um para um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token. Ou seja, a função tem um `ICorDebugFunction` objeto e um `mdMethodDef` token.  
  
-   Se editar e continuar é permitida na função, existe uma relação de muitos-para-um entre o `ICorDebugFunction` objeto e o `mdMethodDef` token. Ou seja, a função pode ter muitas instâncias do `ICorDebugFunction`, um para cada versão da função, mas somente um `mdMethodDef` token.  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:**  CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
