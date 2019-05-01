---
title: Interface ICorProfilerInfo3
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b523c5819994e6da0332188311b4b631e3f9072
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000578"
---
# <a name="icorprofilerinfo3-interface"></a>Interface ICorProfilerInfo3
Fornece métodos que os criadores de perfil de código usam para se comunicar com o common language runtime (CLR) para controlar o monitoramento de eventos e solicitar informações. O `ICorProfilerInfo3` interface é uma extensão do [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interface. Ele fornece novos métodos com suporte no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] e versões posteriores.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|Retorna um enumerador para todas as funções anteriormente compilado por JIT.|  
|[Método EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|Retorna um enumerador que fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos gerenciados que são carregados no aplicativo.|  
|[Método GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Obtém os identificadores dos domínios de aplicativo no qual o determinado módulo foi carregado.|  
|[Método GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|Fornece as informações de quadro e o argumento de pilha da função que está sendo relatada ao criador de perfil, o [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) função; pode ser chamado somente durante o `FunctionEnter3WithInfo` retorno de chamada.|  
|[Método GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|Fornece o quadro de pilha e o valor de retorno da função que está sendo relatada ao criador de perfil pela [função FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) função; pode ser chamado somente durante o `FunctionLeave3WithInfo` retorno de chamada.|  
|[Método GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|Fornece o quadro de pilhas da função que está sendo relatado ao criador de perfil, o [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) função; pode ser chamado somente durante o `FunctionTailcall3WithInfo` retorno de chamada.|  
|[Método GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|Dado um ID de módulo, retorna o nome do arquivo do módulo, a ID do pai do módulo de assembly e um bitmask que descreve as propriedades do módulo.|  
|[Método GetRuntimeInformation](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|Fornece informações de versão sobre o tempo de execução que está sendo analisado.|  
|[Método GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|Obtém informações sobre o layout de um objeto de cadeia de caracteres.|  
|[Método GetThreadStaticAddress2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|Obtém o endereço do campo de thread estático especificado está no escopo do thread especificado e do domínio de aplicativo.|  
|[Método RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|Instrui o tempo de execução para desanexar o criador de perfil.|  
|[Método SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Especifica as funções implementadas pelo criador de perfil que serão chamadas na [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) funções.|  
|[Método SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Especifica as funções implementadas pelo criador de perfil que serão chamadas na [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) ganchos de funções gerenciadas.|  
|[Método SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|Especifica a função implementada pelo criador de perfil que será chamada para mapear `FunctionID` ganchos de entrada/saída de função de valores em valores alternativos que são passados para o criador de perfil. Este método estende [ICorProfilerInfo:: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) com um parâmetro que os criadores de perfis podem usar para resolver a ambiguidade os tempos de execução.|  
  
## <a name="remarks"></a>Comentários  
 O CLR implementa os métodos do `ICorProfilerInfo3` interface usando o modelo de Threading livre. Cada método retorna um HRESULT para indicar êxito ou falha. Para obter uma lista dos possíveis códigos de retorno, consulte o arquivo CORERROR h.  
  
 O CLR passa um `ICorProfilerInfo3` interface para cada criador de perfil do código durante a inicialização, usando a implementação do criador de perfil do [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) ou [ICorProfilerCallback3::I nitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) método. Um criador de perfil de código, em seguida, pode chamar o `ICorProfilerInfo3` métodos para obter informações sobre o código gerenciado que está sendo executado sob o controle do CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
