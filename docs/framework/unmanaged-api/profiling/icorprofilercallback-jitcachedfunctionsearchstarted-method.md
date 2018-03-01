---
title: "Método ICorProfilerCallback::JITCachedFunctionSearchStarted"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2208a1a1637b3bb8dd7d7963ab806aeae7921dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>Método ICorProfilerCallback::JITCachedFunctionSearchStarted
Notifica o criador de perfil que uma pesquisa foi iniciada por uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para a qual a pesquisa está sendo executada.  
  
 `pbUseCachedFunction`  
 [out] `true` se o mecanismo de execução deve usar a versão armazenada em cache de uma função (se disponível); caso contrário, `false`. Se o valor for `false`, a execução do mecanismo de JIT compila a função em vez de usar uma versão que não é compilado por JIT.  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 2.0, o `JITCachedFunctionSearchStarted` e [: Jitcachedfunctionsearchfinished método](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) retornos de chamada não serão feitos para todas as funções em imagens NGen normais. Somente imagens NGen otimizadas para um perfil gerará retornos de chamada para todas as funções na imagem. No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil com otimização de NGen imagens somente se pretender usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT). Caso contrário, o criador de perfil deve usar uma estratégia lenta para reunir informações de função.  
  
 Criadores de perfil devem dar suporte a casos em que vários threads de um aplicativo de perfil estiver chamando o mesmo método simultaneamente. Por exemplo, um thread de chamadas `JITCachedFunctionSearchStarted` e o criador de perfil responde definindo *pbUseCachedFunction*como FALSE para forçar a compilação JIT. Thread de um, em seguida, chama [: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) e [Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Agora thread B chamadas `JITCachedFunctionSearchStarted` para a mesma função. Mesmo que o criador de perfil declarou sua intenção de compilação JIT a função, o criador de perfil recebe o retorno de chamada segundo porque o thread B envia o retorno de chamada antes do criador de perfil respondeu a chamada do thread para `JITCachedFunctionSearchStarted`. A ordem na qual os threads fazer chamadas depende de como os threads são agendados.  
  
 Quando o criador de perfil recebe retornos de chamada duplicados, ele deve definir o valor referenciado por `pbUseCachedFunction` com o mesmo valor para retornos de chamada duplicados. Ou seja, quando `JITCachedFunctionSearchStarted` for chamado várias vezes com o mesmo `functionId` valor, o criador de perfil deve responder a mesma cada vez.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
