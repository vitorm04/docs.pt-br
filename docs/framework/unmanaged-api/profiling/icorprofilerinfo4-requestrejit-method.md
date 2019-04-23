---
title: Método ICorProfilerInfo4::RequestReJIT
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ddad2497f18aa510ade41f58ba20c9de1a46ce5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135090"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>Método ICorProfilerInfo4::RequestReJIT
Solicita uma recompilação JIT de todas as instâncias das funções especificadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 [in] O número de funções para recompilar.  
  
 `moduleIds`  
 [in] Especifica o `moduleId` parte do (`module`, `methodDef`) pares que identificam as funções a ser recompilado.  
  
 `methodIds`  
 [in] Especifica o `methodId` parte do (`module`, `methodDef`) pares que identificam as funções a ser recompilado.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|Foi feita uma tentativa para marcar todos os métodos de recompilação JIT. O criador de perfis deve implementar o [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) método para determinar quais métodos foram marcados para recompilação JIT com êxito.|  
|CORPROF_E_CALLBACK4_REQUIRED|O criador de perfis deve implementar o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface para a chamada a ter suporte.|  
|CORPROF_E_REJIT_NOT_ENABLED|Recompilação JIT não foi habilitada. Você deve habilitar recompilação JIT durante a inicialização usando o [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir o `COR_PRF_ENABLE_REJIT` sinalizador.|  
|E_INVALIDARG|`cFunctions` é 0, ou `moduleIds` ou `methodIds` é `NULL`.|  
|||  
|E_OUTOFMEMORY|O CLR não pôde concluir a solicitação porque ele ficou sem memória.|  
  
## <a name="remarks"></a>Comentários  
 Chamar `RequestReJIT` para ter o tempo de execução a recompilar um conjunto de funções especificado. Um criador de perfil de código, em seguida, pode usar o [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface para ajustar o código que é gerado quando as funções são recompiladas. Isso não afeta as funções em execução no momento, invocações de função só futuras. Se qualquer uma das funções especificadas anteriormente tiver sido recompilado por JIT, solicitar uma recompilação é equivalente a reversão e recompilar a função. Para preservar a possibilidade de reversão, quando o compilador JIT compila a versão original de uma função, ele considera somente as versões originais de seus chamados para decisões de inlining. Quando o compilador JIT recompila uma função, ele considera as versões atuais (recompiladas ou originais) do seus receptores de inlining.  
  
 Um criador de perfil chama normalmente `RequestReJIT` em resposta à entrada do usuário solicitando que o criador de perfil instrumentar um ou mais métodos. `RequestReJIT` Normalmente, suspende o tempo de execução para fazer parte de seu trabalho e podem, potencialmente, uma coleta de lixo do gatilho. Como tal, o criador de perfil deve chamar `RequestReJIT` de um thread ele criou anteriormente e não de um thread criado pelo CLR que está executando um retorno de chamada do criador de perfil.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
