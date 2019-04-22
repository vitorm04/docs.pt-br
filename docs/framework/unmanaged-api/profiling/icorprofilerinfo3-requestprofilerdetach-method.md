---
title: Método ICorProfilerInfo3::RequestProfilerDetach
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b04c0453d9ff8545f79f235e7d73095c55203e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083277"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>Método ICorProfilerInfo3::RequestProfilerDetach
Instrui o tempo de execução para desanexar o criador de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwExpectedCompletionMilliseconds`  
 [in] O período de tempo, em milissegundos, o common language runtime (CLR) deve aguardar antes de verificar se ele é seguro descarregar o criador de perfil.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A solicitação de desanexação é válida e o procedimento de desanexar agora continua em outro thread. Quando a desanexação for totalmente concluída, um `ProfilerDetachSucceeded` evento é emitido.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|O criador de perfil falhou uma [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) tentativa para o [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interface, que ele deve implementar para dar suporte a operação desanexar. Desanexar não foi tentada.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|Desanexação é impossível porque o criador de perfil definir sinalizadores imutáveis na inicialização. Não foi tentada a desanexação; o criador de perfil ainda totalmente está anexado.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|Desanexação é impossível porque o criador de perfil usado instrumentado código Microsoft intermediate language (MSIL) ou inseridas `enter` / `leave` ganchos. Não foi tentada a desanexação; o criador de perfil ainda totalmente está anexado.<br /><br /> **Observação** MSIL instrumentado é o código é um código que é fornecido pelo criador de perfil usando o [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) método.|  
|CORPROF_E_RUNTIME_UNINITIALIZED|O tempo de execução não foi inicializado ainda no aplicativo gerenciado. (Ou seja, o tempo de execução não foi totalmente carregado.) Esse código de erro pode ser retornado quando desanexação for solicitada dentro do retorno de chamada criador de perfil [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) método.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` foi chamado em um tempo sem suporte. Isso ocorre se o método é chamado em um thread gerenciado, mas não de dentro um [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) método ou de dentro um [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) método que não pode tolerar uma coleta de lixo. Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Comentários  
 Durante o procedimento de desanexar, o thread de desanexar (o thread criado especificamente para desanexar o criador de perfil), ocasionalmente, verifica se todos os threads tenham saído código do criador de perfil. O criador de perfil deve fornecer uma estimativa de quanto tempo isso deve percorrer o `dwExpectedCompletionMilliseconds` parâmetro. Um bom valor para usar é a quantidade normal de tempo que o criador de perfil gasta em nenhum dado `ICorProfilerCallback*` método; esse valor não deve ser menos da metade da quantidade máxima de tempo de espera que o criador de perfil para gastar.  
  
 O thread de desanexar usa `dwExpectedCompletionMilliseconds` para decidir quanto no modo de suspensão antes de verificar se código de retorno de chamada do criador de perfil foram retirado todas as pilhas. Embora os detalhes da seguinte algoritmo podem mudar em versões futuras do CLR, ele ilustra uma maneira `dwExpectedCompletionMilliseconds` pode ser usado ao determinar quando é seguro descarregar o criador de perfil. O thread de desanexar primeiro fica suspenso `dwExpectedCompletionMilliseconds` milissegundos. Se, após a ativação do estado de suspensão, o CLR encontrar que código de retorno de chamada do criador de perfil ainda está presente, o thread de desanexar entra em suspensão, novamente, desta vez para duas vezes `dwExpectedCompletionMilliseconds` milissegundos. Se, após a ativação do modo de suspensão esse segundo, o thread de desanexar localiza que código de retorno de chamada do criador de perfil ainda está presente, ele entra em suspensão por 10 minutos antes de verificar novamente. O thread de desanexar continua a verificar novamente a cada 10 minutos.  
  
 Se o criador de perfil especifica `dwExpectedCompletionMilliseconds` como 0 (zero), o CLR usa um valor padrão de 5000, o que significa que ele executará uma verificação depois de 5 segundos, novamente após 10 segundos, e, em seguida, cada 10 minutos e depois disso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
