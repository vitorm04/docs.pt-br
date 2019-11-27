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
ms.openlocfilehash: eb4d5e1c4efd67914df95868b67ec5cc3fe6139a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444823"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>Método ICorProfilerInfo4::RequestReJIT
Solicita uma recompilação JIT de todas as instâncias das funções especificadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 no O número de funções a serem recompiladas.  
  
 `moduleIds`  
 no Especifica a parte `moduleId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.  
  
 `methodIds`  
 no Especifica a parte `methodId` dos pares (`module`, `methodDef`) que identificam as funções a serem recompiladas.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|Foi feita uma tentativa de marcar todos os métodos para a recompilação JIT. O criador de perfil deve implementar o método [ICorProfilerCallback4:: ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) para determinar quais métodos foram marcados com êxito para recompilação JIT.|  
|CORPROF_E_CALLBACK4_REQUIRED|O criador de perfil deve implementar a interface [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) para que essa chamada seja suportada.|  
|CORPROF_E_REJIT_NOT_ENABLED|A recompilação JIT não foi habilitada. Você deve habilitar a recompilação JIT durante a inicialização usando o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir o sinalizador de `COR_PRF_ENABLE_REJIT`.|  
|{1&gt;E_INVALIDARG&lt;1}|`cFunctions` é 0, ou `moduleIds` ou `methodIds` é `NULL`.|  
|||  
|{1&gt;E_OUTOFMEMORY&lt;1}|O CLR não pôde concluir a solicitação porque ficou sem memória.|  
  
## <a name="remarks"></a>Comentários  
 Chame `RequestReJIT` para que o tempo de execução recompile um conjunto especificado de funções. Um criador de perfil de código pode usar a interface [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) para ajustar o código que é gerado quando as funções são recompiladas. Isso não afeta as funções atualmente em execução, apenas as invocações de função futuras. Se qualquer uma das funções especificadas tiver sido recompilada por JIT, a solicitação de uma recompilação será equivalente à reversão e à recompilação da função. Para preservar o inversão, quando o compilador JIT compila a versão original de uma função, ele considera apenas as versões originais dos seus chamadores para as decisões de inalinhamento. Quando o compilador JIT recompila uma função, ele considera as versões atuais (recompiladas ou originais) de seus chamadores para o inlining.  
  
 Um criador de perfil normalmente chama `RequestReJIT` em resposta à entrada do usuário solicitando que o criador de perfil tenha um ou mais métodos. o `RequestReJIT` normalmente suspende o tempo de execução para fazer parte de seu trabalho e pode potencialmente disparar uma coleta de lixo. Como tal, o criador de perfil deve chamar `RequestReJIT` de um thread criado anteriormente, e não de um thread criado pelo CLR que está atualmente executando um retorno de chamada do criador de perfil.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
