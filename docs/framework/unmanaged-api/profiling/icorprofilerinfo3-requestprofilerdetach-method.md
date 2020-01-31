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
ms.openlocfilehash: 8520f5fc0a6ff7e71f40cd7fbb1caf68aab63197
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868506"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>Método ICorProfilerInfo3::RequestProfilerDetach
Instrui o tempo de execução para desanexar o criador de perfil.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwExpectedCompletionMilliseconds`  
 no O período de tempo, em milissegundos, que o Common Language Runtime (CLR) deve aguardar antes de verificar se é seguro descarregar o criador de perfil.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|A solicitação de desanexação é válida e o procedimento de desanexação agora está continuando em outro thread. Quando a desanexação estiver totalmente concluída, um evento `ProfilerDetachSucceeded` será emitido.|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|O criador de perfil falhou em uma tentativa de [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) para a interface [ICorProfilerCallback3](icorprofilercallback3-interface.md) , que deve ser implementada para oferecer suporte à operação de desanexação. A desanexação não foi tentada.|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|A desanexação é impossível porque o criador de perfil define sinalizadores imutáveis na inicialização. A desanexação não foi tentada; o criador de perfil ainda está totalmente anexado.|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|A desanexação é impossível porque o criador de perfil usou o código MSIL (Microsoft Intermediate Language) instrumentado ou inseriu `enter`/`leave` ganchos. A desanexação não foi tentada; o criador de perfil ainda está totalmente anexado.<br /><br /> **Observação** O código MSIL instrumentado é o código que é fornecido pelo criador de perfil usando o método [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) .|  
|CORPROF_E_RUNTIME_UNINITIALIZED|O tempo de execução ainda não foi inicializado no aplicativo gerenciado. (Ou seja, o tempo de execução não foi totalmente carregado.) Esse código de erro pode ser retornado quando a desanexação é solicitada dentro do método [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) do retorno de perfil.|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` foi chamado em um tempo sem suporte. Isso ocorrerá se o método for chamado em um thread gerenciado, mas não dentro de um método [ICorProfilerCallback](icorprofilercallback-interface.md) ou de dentro de um método [ICorProfilerCallback](icorprofilercallback-interface.md) que não possa tolerar uma coleta de lixo. Para obter mais informações, consulte [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).|  
  
## <a name="remarks"></a>Comentários  
 Durante o procedimento de desanexação, o thread de desanexação (o thread criado especificamente para desanexar o criador de perfil) verifica ocasionalmente se todos os threads saíram do código do criador de perfil. O criador de perfil deve fornecer uma estimativa de quanto tempo isso deve levar por meio do parâmetro `dwExpectedCompletionMilliseconds`. Um bom valor a ser usado é a quantidade comum de tempo que o criador de perfil gasta dentro de qualquer determinado método de `ICorProfilerCallback*`; Esse valor não deve ser menor que metade da quantidade máxima de tempo que o criador de perfil espera gastar.  
  
 O thread de desanexação usa `dwExpectedCompletionMilliseconds` para decidir por quanto tempo suspender antes de verificar se o código de retorno de chamada do profiler foi desativado em todas as pilhas. Embora os detalhes do algoritmo a seguir possam ser alterados em versões futuras do CLR, ele ilustra uma maneira `dwExpectedCompletionMilliseconds` pode ser usado ao determinar quando é seguro descarregar o criador de perfil. Primeiro, o thread de desanexação é suspenso por `dwExpectedCompletionMilliseconds` milissegundos. Se, depois de despertar da suspensão, o CLR descobrir que o código de retorno de chamada do criador de perfil ainda está presente, o thread de desanexação será suspenso novamente, desta vez por duas vezes `dwExpectedCompletionMilliseconds` milissegundos. Se, depois de despertar dessa segunda suspensão, o thread de desanexação descobrir que o código de retorno de chamada do criador de perfil ainda está presente, ele será suspenso por 10 minutos antes de verificar novamente. O thread de desanexação continua a verificar novamente a cada 10 minutos.  
  
 Se o criador de perfil especificar `dwExpectedCompletionMilliseconds` como 0 (zero), o CLR usará um valor padrão de 5000, o que significa que ele executará uma verificação após 5 segundos, novamente após 10 segundos e, em seguida, a cada 10 minutos depois.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
