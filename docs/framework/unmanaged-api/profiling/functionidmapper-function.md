---
title: Função FunctionIDMapper
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: d5bf6626e2c6ba15fa9a5da08bcf2d9052866750
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866938"
---
# <a name="functionidmapper-function"></a>Função FunctionIDMapper
Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)e [FunctionTailcall2](functiontailcall2-function.md) para essa função. `FunctionIDMapper` também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parâmetros

- `funcId`

  \[em] o identificador de função a ser remapeado.

- `pbHookFunction`

  \[out] um ponteiro para um valor que o criador de perfil define para `true` se quiser receber retornos de chamada `FunctionEnter2`, `FunctionLeave2`e `FunctionTailcall2`; caso contrário, ele definirá esse valor como `false`.

## <a name="return-value"></a>Valor de retorno  
 O criador de perfil retorna um valor que o mecanismo de execução usa como um identificador de função alternativo. O valor de retorno não pode ser nulo, a menos que `false` seja retornado em `pbHookFunction`. Caso contrário, um valor de retorno nulo produzirá resultados imprevisíveis, incluindo possivelmente interromper o processo.  
  
## <a name="remarks"></a>Comentários  
 A função `FunctionIDMapper` é um retorno de chamada. Ele é implementado pelo criador de perfil para remapear uma ID de função para algum outro identificador que seja mais útil para o criador de perfil. O `FunctionIDMapper` retorna a ID alternativa a ser usada para qualquer função específica. Em seguida, o mecanismo de execução honra a solicitação do criador de perfil, passando essa ID alternativa, além da ID de função tradicional, de volta para o criador de perfil no parâmetro `clientData` dos ganchos `FunctionEnter2`, `FunctionLeave2`e `FunctionTailcall2`, para identificar a função para a qual o gancho está sendo chamado.  
  
 Você pode usar o método [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) para especificar a implementação da função `FunctionIDMapper`. Você pode chamar o método `ICorProfilerInfo::SetFunctionIDMapper` apenas uma vez e é recomendável fazer isso no retorno de chamada [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) .  
  
 Por padrão, supõe-se que um criador de perfil que define o sinalizador de COR_PRF_MONITOR_ENTERLEAVE usando [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)e que define ganchos via [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) ou [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), deve receber os retornos de chamada `FunctionEnter2`, `FunctionLeave2`e `FunctionTailcall2` para cada função. No entanto, os profileres podem implementar `FunctionIDMapper` para evitar seletivamente o recebimento desses retornos de chamada para determinadas funções, definindo `pbHookFunction` como `false`.  
  
 Os profileres devem ser tolerantes a casos em que vários threads de um aplicativo de perfil criado chamam o mesmo método/função simultaneamente. Nesses casos, o criador de perfil pode receber vários `FunctionIDMapper` retornos de chamada para o mesmo `FunctionID`. O criador de perfil deve ter certeza de retornar os mesmos valores desse retorno de chamada quando ele é chamado várias vezes com o mesmo `FunctionID`.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [Função FunctionIDMapper2](functionidmapper2-function.md)
- [Função FunctionEnter2](functionenter2-function.md)
- [Função FunctionLeave2](functionleave2-function.md)
- [Função FunctionTailcall2](functiontailcall2-function.md)
- [Criando perfil de funções estáticas globais](profiling-global-static-functions.md)
