---
title: Interface ICorProfilerInfo4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4
helpviewer_keywords: ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: db91347ad2c951c28ea7b653336450929d37bdcb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4-interface"></a>Interface ICorProfilerInfo4
Fornece métodos que criadores de perfil de código usam para se comunicar com o common language runtime (CLR) para controlar o monitoramento de eventos e informações de solicitação. . O `ICorProfilerInfo4` interface é uma extensão do outro `ICorProfilerInfo` interfaces. Ele fornece novos métodos para dar suporte a recompilação just-in-time (JIT), adicionada no [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Retorna um enumerador para todas as funções que foram anteriormente compilados JIT e recompilado JIT.|  
|[Método EnumThreads](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Obtém um enumerador que fornece métodos para sequencialmente iterar através da coleção de todos os threads gerenciados no processo com perfil.|  
|[Método GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Obtém as extensões de código nativo associado com a versão recompilada JIT da função especificada.|  
|[Método GetFunctionFromIP2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Um ponteiro de instrução do código gerenciado é mapeado para a versão recompilada JIT de uma função especificada.|  
|[Método GetILToNativeMapping2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Obtém um mapa do Microsoft intermediate language (MSIL) desloca para deslocamentos nativo para o código contido na versão recompilada JIT da função especificada.|  
|[Método GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Retorna o tamanho de um objeto especificado.|  
|[Método GetReJITIDs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Retorna uma matriz de IDs de identificar todos os recompilado JIT versões da função especificada ainda alocados.|  
|[Método InitializeCurrentThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Inicializa o thread atual antes de criador de perfil subsequente chamadas à API no mesmo thread, portanto esse deadlock pode ser evitado.|  
|[Método RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Solicita uma recompilação de JIT de todas as instâncias das funções especificadas.|  
|[Método RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Reverte todas as instâncias das funções especificadas para suas versões originais.|  
  
## <a name="remarks"></a>Comentários  
 O CLR implementa os métodos do `ICorProfilerInfo4` interface usando o modelo de segmentação livre. Cada método retorna um HRESULT indicando êxito ou falha. Para obter uma lista de possíveis códigos de retorno, consulte o arquivo corerror.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
