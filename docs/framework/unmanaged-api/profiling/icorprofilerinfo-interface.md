---
title: Interface ICorProfilerInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
ms.openlocfilehash: 0af990930e8c30307e9da3b586621ca8ddb95d0c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438752"
---
# <a name="icorprofilerinfo-interface"></a>Interface ICorProfilerInfo
Fornece métodos para uso por infilers de código para se comunicar com o Common Language Runtime (CLR) para controlar o monitoramento de eventos e informações de solicitação.  
  
> [!NOTE]
> Cada método na interface `ICorProfilerInfo` retorna um HRESULT para indicar êxito ou falha. Consulte CorError. h para obter uma lista de possíveis códigos de retorno.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Inicializa o suporte à depuração em processo. Esse método é obsoleto no .NET Framework versão 2,0.|  
|[Método EndInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Desliga uma sessão de depuração em processo. Esse método é obsoleto no .NET Framework versão 2,0.|  
|[Método ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Força a coleta de lixo a ocorrer dentro do tempo de execução.|  
|[Método GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Obtém informações sobre o domínio de aplicativo especificado.|  
|[Método GetAssemblyInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Obtém informações sobre o assembly especificado.|  
|[Método GetClassFromObject](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Obtém a `ClassID` de um<br /><br /> objeto, dado seu `ObjectID`.|  
|[Método GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Obtém a ID da classe, dado o token de metadados. Esse método é obsoleto no .NET Framework versão 2,0. Em vez disso, use o método [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) .|  
|[Método GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Obtém o módulo pai e o token de metadados para a classe especificada.|  
|[Método GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Obtém a extensão do código nativo associado à ID da função especificada. Esse método é obsoleto. Em vez disso, use o método [ICorProfilerInfo2:: GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) .|  
|[Método GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Obtém a ID do thread atual, se for um thread gerenciado.|  
|[Método GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Obtém as categorias de evento atuais para as quais o criador de perfil deseja receber notificações de eventos do CLR.|  
|[Método GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Mapeia um ponteiro de instrução de código gerenciado para um `FunctionID`.|  
|[Método GetFunctionFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Obtém a ID de uma função. Esse método é obsoleto no .NET Framework versão 2,0. Em vez disso, use o método [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) .|  
|[Método GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Obtém a classe pai e o token de metadados para a função especificada.|  
|[Método GetHandleFromThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Mapeia a ID de um thread para um identificador de thread do Win32.|  
|[Método GetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Obtém um ponteiro para o corpo de um método no código da MSIL (Microsoft Intermediate Language), começando em seu cabeçalho.|  
|[Método GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|Obtém uma interface que fornece um método para alocar memória a ser usada para alternar o corpo de um método no código MSIL.|  
|[Método GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Obtém um mapa de deslocamentos MSIL para deslocamentos nativos para o código contido na função especificada.|  
|[Método GetInprocInspectionInterface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Obtém um objeto que pode ser consultado para uma interface ICorDebugProcess. Esse método é obsoleto no .NET Framework versão 2,0.|  
|[Método GetInprocInspectionIThisThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Obtém um objeto que pode ser consultado para a interface ICorDebugThread. Esse método é obsoleto no .NET Framework versão 2,0.|  
|[Método GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Dada uma ID de módulo, retorna o nome do arquivo do módulo e a ID do assembly pai do módulo.|  
|[Método GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Obtém uma instância de interface de metadados que mapeia para o módulo especificado.|  
|[Método GetObjectSize](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Obtém o tamanho de um objeto especificado.|  
|[Método GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Obtém a identidade de contexto atualmente associada ao thread especificado.|  
|[Método GetThreadInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Obtém a identidade do Thread Win32 atual para o thread especificado.|  
|[Método GetTokenAndMetadataFromFunction](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Obtém o token de metadados e uma instância da interface de metadados que pode ser usada em relação ao token para a função especificada.|  
|[Método IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Determina se a classe especificada é uma classe de matriz.|  
|[Método SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Especifica funções implementadas pelo Profiler a serem chamadas em "Inserir", "deixar" e "tailcall" ganchos de funções gerenciadas.|  
|[Método SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Define um valor que especifica os tipos de eventos para os quais o criador de perfil deseja receber a notificação do CLR.|  
|[Método SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Especifica a função implementada pelo criador de perfil que será chamada para mapear valores de `FunctionID` para valores alternativos, que são passados para os ganchos de entrada/saída da função do criador de perfil.|  
|[Método SetFunctionReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Não implementado. Não use.|  
|[Método SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Substitui o corpo da função especificada no módulo especificado.|  
|[Método SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Especifica como os deslocamentos de um MSIL original da função especificada são mapeados para os novos deslocamentos do MSIL do criador de perfil da função.|  
  
## <a name="remarks"></a>Comentários  
 Um criador de perfil chama um método na interface `ICorProfilerInfo` para se comunicar com o CLR para controlar as informações de solicitação e monitoramento de eventos.  
  
 Os métodos da interface `ICorProfilerInfo` são implementados pelo CLR usando o modelo de thread livre. Cada método retorna um HRESULT para indicar êxito ou falha. Consulte CorError. h para obter uma lista de possíveis códigos de retorno.  
  
 O CLR passa, por meio da implementação do criador de perfil de [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md), uma interface `ICorProfilerInfo` para cada criador de perfil de código durante a inicialização. Um criador de perfil de código pode então chamar métodos da interface `ICorProfilerInfo` para obter informações sobre o código gerenciado que está sendo executado sob o controle do CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
