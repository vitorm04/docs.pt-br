---
title: Interface ICorProfilerInfo2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3476a338191a4af9cc01b7e44456f1bd20f52a10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796533"
---
# <a name="icorprofilerinfo2-interface"></a>Interface ICorProfilerInfo2
Fornece métodos que os criadores de perfil de código usam para se comunicar com o CLR (CLR) para controlar o monitoramento de eventos e informações de solicitação. O `ICorProfilerInfo2` interface é uma extensão do [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface. Ou seja, ele fornece novos métodos com suporte no .NET Framework versão 2.0 e versões posteriores.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Percorre a pilha do thread especificado para relatar os quadros de chamada gerenciada para o criador de perfil.|  
|[Método EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Obtém um enumerador que permite a iteração por meio de objetos congelados no módulo especificado.|  
|[Método GetAppDomainStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Obtém o endereço do campo de domínio estáticos do aplicativo especificado que está no escopo do domínio do aplicativo especificado.|  
|[Método GetArrayObjectInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Obtém informações detalhadas sobre um objeto de matriz.|  
|[Método GetBoxClassLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Obtém informações sobre o layout de classe para um tipo de valor especificado é convertido.|  
|[Método GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Obtém o `ClassID` de um tipo usando o token de metadados especificado e o `ClassID` valores de qualquer tipo de argumentos.|  
|[Método GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Obtém o módulo pai, a classe genérica especificada, o token de metadados para a classe, o `ClassID` de sua classe pai e o `ClassID` para cada argumento de tipo, se presente, da classe.|  
|[Método GetClassLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Obtém informações sobre o layout, na memória, dos campos definidos pela classe especificada. Ou seja, esse método obtém os deslocamentos de campos da classe.|  
|[Método GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Obtém as extensões de código nativo associado especificado `FunctionID`.|  
|[Método GetContextStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Obtém o endereço do campo especificado do contexto estático que está no escopo do contexto especificado.|  
|[Método GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Obtém o `FunctionID` de uma função usando o token de metadados especificado, que contém a classe, e `ClassID` valores de qualquer tipo de argumentos.|  
|[Método GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Obtém a classe pai, o token de metadados e o `ClassID` de cada argumento de tipo, se presente, de uma função.|  
|[Método GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Obtém as regiões de memória (os segmentos do heap) que compõem as gerações do heap coletado como lixo.|  
|[Método GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Obtém as informações de endereço e o quadro nativas para a cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executado ou foi executado.|  
|[Método GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Obtém o segmento de heap que contém o objeto especificado.|  
|[Método GetRVAStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Obtém o endereço do endereço de virtual relativo especificado (RVA)-campo estático.|  
|[Método GetStaticFieldInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Obtém o escopo no qual o campo especificado é estático.|  
|[Método GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Obtém informações sobre o layout de um objeto de cadeia de caracteres.|  
|[Método GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Obtém a ID do domínio do aplicativo no qual o thread especificado está executando código.|  
|[Método GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Obtém o endereço do campo de thread estático especificado está no escopo do thread especificado.|  
|[Método SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Especifica as funções implementada pelo criador de perfil a ser chamado no "enter", "Sair" e "chamada tail" ganchos de funções gerenciadas.|  
  
## <a name="remarks"></a>Comentários  
 Um criador de perfil chama um método no `ICorProfilerInfo2` interface para se comunicar com o CLR para controlar o monitoramento de eventos e solicitar informações.  
  
 Os métodos do `ICorProfilerInfo2` interface são implementados pelo CLR usando o modelo de Threading livre. Cada método retorna um HRESULT para indicar êxito ou falha. Para obter uma lista dos possíveis códigos de retorno, consulte o arquivo CORERROR h.  
  
 O CLR passa um `ICorProfilerInfo2` interface para cada criador de perfil do código durante a inicialização, usando a implementação do criador de perfil do [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Um criador de perfil de código, em seguida, pode chamar métodos do `ICorProfilerInfo2` interface para obter informações sobre o código gerenciado que está sendo executada sob o controle do CLR.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
