---
title: "Método ICorProfilerInfo4::RequestReJIT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestReJIT
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4da57e95813afa1135482bef7cf6ab50ee6365cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrejit-method"></a>Método ICorProfilerInfo4::RequestReJIT
Solicita uma recompilação de JIT de todas as instâncias das funções especificadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 [in] O número de funções de recompilar.  
  
 `moduleIds`  
 [in] Especifica o `moduleId` parte das (`module`, `methodDef`) pares que identificam as funções a ser recompilado.  
  
 `methodIds`  
 [in] Especifica o `methodId` parte das (`module`, `methodDef`) pares que identificam as funções a ser recompilado.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|Foi feita uma tentativa para marcar todos os métodos para recompilação de JIT. O criador de perfil deve implementar o [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) método para determinar quais métodos com êxito foram marcados para recompilação de JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|O criador de perfil deve implementar o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface para a chamada com suporte.|  
|CORPROF_E_REJIT_NOT_ENABLED|Recompilação de JIT não foi habilitada. Você deve habilitar recompilação JIT durante a inicialização por meio de [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir o `COR_PRF_ENABLE_REJIT` sinalizador.|  
|E_INVALIDARG|`cFunctions`é 0, ou `moduleIds` ou `methodIds` é `NULL`.|  
|||  
|E_OUTOFMEMORY|O CLR não pôde concluir a solicitação porque ele ficou sem memória.|  
  
## <a name="remarks"></a>Comentários  
 Chamar `RequestReJIT` para que o tempo de execução recompilar um conjunto especificado de funções. Um criador de perfil de código, em seguida, pode usar o [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface para ajustar o código que é gerado quando as funções são recompiladas. Isso não afeta a funções em execução no momento, apenas futuras invocações. Se qualquer uma das funções especificadas anteriormente foi recompilado JIT, solicitar uma recompilação é equivalente a reversão e recompilar a função. Para preservar a possibilidade de reversão, quando o compilador JIT compila a versão original de uma função, ele considera apenas as versões originais de seus chamados para decisões de inlining. Quando o compilador JIT recompila uma função, ele considera as versões atuais (recompiladas ou originais) de seus chamados de inlining.  
  
 Um criador de perfil normalmente chama `RequestReJIT` em resposta à entrada do usuário solicitando que o criador de perfil instrumentar um ou mais métodos. `RequestReJIT`Normalmente, suspende o tempo de execução para fazer parte de seu trabalho e podem potencialmente gatilho uma coleta de lixo. Como tal, o criador de perfil deve chamar `RequestReJIT` de um thread ele criou anteriormente e não de um thread criado pelo CLR que está executando um retorno de chamada do criador de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
