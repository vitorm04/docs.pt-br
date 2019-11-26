---
title: Método ICorProfilerCallback::JITCachedFunctionSearchStarted
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 5d3fe6691a2d9989de002bad09c2e8f66a094f56
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448438"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>Método ICorProfilerCallback::JITCachedFunctionSearchStarted
Notifica o criador de perfil de que uma pesquisa foi iniciada para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen. exe).  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 no A ID da função para a qual a pesquisa está sendo executada.  
  
 `pbUseCachedFunction`  
 [fora] `true` se o mecanismo de execução deve usar a versão em cache de uma função (se disponível); caso contrário `false`. Se o valor for `false`, o mecanismo de execução JIT compilará a função em vez de usar uma versão que não seja compilada por JIT.  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 2,0, os retornos de chamada do método `JITCachedFunctionSearchStarted` e [ICorProfilerCallback:: JITCachedFunctionSearchFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) não serão feitos para todas as funções em imagens NGen regulares. Somente imagens NGen otimizadas para um perfil gerarão retornos de chamada para todas as funções na imagem. No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar imagens NGen otimizadas para o criador de perfil somente se pretender usar esses retornos de chamada para forçar uma função a ser compilada just-in-time (JIT). Caso contrário, o criador de perfil deve usar uma estratégia lenta para coletar informações de função.  
  
 Os profileres devem oferecer suporte a casos em que vários threads de um aplicativo de perfil criado chamem o mesmo método simultaneamente. Por exemplo, thread A chama `JITCachedFunctionSearchStarted` e o criador de perfil responde definindo *pbUseCachedFunction*como false para forçar a compilação JIT. O thread A chama [ICorProfilerCallback:: JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) e [ICorProfilerCallback:: JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Agora, o thread B chama `JITCachedFunctionSearchStarted` para a mesma função. Embora o criador de perfil tenha declarado sua intenção de compilar a função por JIT, o criador de perfil recebe o segundo retorno de chamada, pois o thread B envia o retorno de chamada antes que o criador de perfil tenha respondido à chamada do thread a `JITCachedFunctionSearchStarted`. A ordem na qual os threads fazem chamadas depende de como os threads são agendados.  
  
 Quando o criador de perfil recebe retornos de chamada duplicados, ele deve definir o valor referenciado por `pbUseCachedFunction` com o mesmo valor para todos os retornos de chamada duplicados. Ou seja, quando `JITCachedFunctionSearchStarted` é chamado várias vezes com o mesmo valor de `functionId`, o criador de perfil deve responder o mesmo a cada vez.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
