---
title: Interface ICorProfilerInfo4
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34c358a3405262787ed495bf9d8d75462d97a71f
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380340"
---
# <a name="icorprofilerinfo4-interface"></a>Interface ICorProfilerInfo4
Fornece métodos que os criadores de perfil de código usam para se comunicar com o CLR (CLR) para controlar o monitoramento de eventos e informações de solicitação. . O `ICorProfilerInfo4` interface é uma extensão do outro `ICorProfilerInfo` interfaces. Ele fornece novos métodos para dar suporte a recompilação de (JIT) just-in-time, adicionada no .NET Framework 4.5.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Retorna um enumerador para todas as funções que foram previamente compilado por JIT e recompilado por JIT.|  
|[Método EnumThreads](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Obtém um enumerador que fornece métodos para iterar de forma sequencial por meio da coleção de todos os threads gerenciados no processo de criação de perfil.|  
|[Método GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Obtém as extensões de código nativo associado com a versão recompilado por JIT da função especificada.|  
|[Método GetFunctionFromIP2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Mapeia um ponteiro de instrução de código gerenciado para a versão recompilado por JIT de uma função especificada.|  
|[Método GetILToNativeMapping2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Obtém um mapa da Microsoft intermediate language (MSIL) deslocamentos para deslocamentos nativos para o código contido na versão recompilado por JIT da função especificada.|  
|[Método GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Retorna o tamanho de um objeto especificado.|  
|[Método GetReJITIDs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Retorna uma matriz de IDs que identificam todos os recompilado por JIT versões da função especificada que ainda são alocadas.|  
|[Método InitializeCurrentThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Inicializa o thread atual com antecedência sobre o criador de perfil subsequente, chamadas de API no mesmo thread, portanto, esse deadlock pode ser evitado.|  
|[Método RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Solicita uma recompilação JIT de todas as instâncias das funções especificadas.|  
|[Método RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Reverte todas as instâncias das funções especificadas para suas versões originais.|  
  
## <a name="remarks"></a>Comentários  
 O CLR implementa os métodos do `ICorProfilerInfo4` interface usando o modelo de Threading livre. Cada método retorna um HRESULT para indicar êxito ou falha. Para obter uma lista dos possíveis códigos de retorno, consulte o arquivo CORERROR h.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
