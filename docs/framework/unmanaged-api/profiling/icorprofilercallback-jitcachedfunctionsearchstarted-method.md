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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3550f4da497574ea5076766ad201e9431af52e4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174298"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>Método ICorProfilerCallback::JITCachedFunctionSearchStarted
Notifica o criador de perfil que uma pesquisa foi iniciada para uma função que foi compilada anteriormente usando o gerador de imagem nativa (NGen.exe).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `functionId`  
 [in] A ID da função para o qual a pesquisa está sendo executada.  
  
 `pbUseCachedFunction`  
 [out] `true` se o mecanismo de execução deve usar a versão em cache de uma função (se disponível); caso contrário `false`. Se o valor for `false`, a execução do mecanismo de JIT compila a função em vez de usar uma versão que não é compilado por JIT.  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 2.0, o `JITCachedFunctionSearchStarted` e [método ICorProfilerCallback:: Jitcachedfunctionsearchfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) retornos de chamada não serão feitos para todas as funções em imagens de NGen regulares. Somente as imagens NGen otimizadas para um perfil irá gerar retornos de chamada para todas as funções na imagem. No entanto, devido à sobrecarga adicional, um criador de perfil deve solicitar o criador de perfil otimizado as imagens NGen somente se ele pretende usar esses retornos de chamada para forçar uma função a ser compilado just-in-time (JIT). Caso contrário, o criador de perfil deve usar uma estratégia de lenta para reunir informações de função.  
  
 Os criadores de perfis devem dar suporte a casos em que vários threads de um aplicativo analisado estiver chamando o mesmo método simultaneamente. Por exemplo, o thread A chama `JITCachedFunctionSearchStarted` e o criador de perfil responde definindo *pbUseCachedFunction*como FALSE para forçar a compilação JIT. Thread de um, em seguida, chama [ICorProfilerCallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) e [ICorProfilerCallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Agora thread B chama `JITCachedFunctionSearchStarted` para a mesma função. Mesmo que o criador de perfil declarou sua intenção de JIT-compilar a função, o criador de perfil recebe o segundo retorno de chamada porque o thread B envia o retorno de chamada antes do criador de perfil tiver respondido à chamada do segmento para `JITCachedFunctionSearchStarted`. A ordem na qual os threads de fazer chamadas depende de como os threads são agendados.  
  
 Quando o criador de perfil recebe duplicados retornos de chamada, ele deve definir o valor referenciado pelo `pbUseCachedFunction` com o mesmo valor para todos os retornos de chamada duplicados. Ou seja, quando `JITCachedFunctionSearchStarted` é chamado várias vezes com o mesmo `functionId` valor, o criador de perfil deve responder a mesma cada vez.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
