---
title: Método ICorProfilerInfo4::RequestRevert
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444829"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>Método ICorProfilerInfo4::RequestRevert
Reverte todas as instâncias das funções especificadas para suas versões originais.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 no O número de funções a serem revertidas.  
  
 `moduleIds`  
 no Especifica a parte `moduleId` dos pares (`module`, `methodDef`) que identificam as funções a serem revertidas.  
  
 `methodIds`  
 no Especifica a parte `methodId` dos pares (`module`, `methodDef`) que identificam as funções a serem revertidas.  
  
 `status`  
 fora Uma matriz de HRESULTs listada na seção "status HRESULTs" mais adiante neste tópico. Cada HRESULT indica o êxito ou a falha ao tentar reverter cada função especificada nas matrizes paralelas `moduleIds` e `methodIds`.  
  
## <a name="return-value"></a>Valor retornado  
 Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|Foi feita uma tentativa de reverter todas as solicitações; no entanto, a matriz de status retornada deve ser verificada para determinar quais funções foram revertidas com êxito.|  
|CORPROF_E_CALLBACK4_REQUIRED|O criador de perfil deve implementar a interface [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) para que essa chamada seja suportada.|  
|CORPROF_E_REJIT_NOT_ENABLED|A recompilação JIT não foi habilitada. Você deve habilitar a recompilação JIT durante a inicialização usando o método [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) para definir o sinalizador de `COR_PRF_ENABLE_REJIT`.|  
|{1&gt;E_INVALIDARG&lt;1}|`cFunctions` é 0, ou `moduleIds` ou `methodIds` é `NULL`.|  
|E_OUTOFMEMORY|O CLR não pôde concluir a solicitação porque ficou sem memória.|  
  
## <a name="status-hresults"></a>Status HRESULTs  
  
|Matriz de status HRESULT|Descrição|  
|--------------------------|-----------------|  
|S_OK|A função correspondente foi revertida com êxito.|  
|{1&gt;E_INVALIDARG&lt;1}|O parâmetro `moduleID` ou `methodDef` é `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|O módulo ainda não está totalmente carregado ou está em processo de descarregamento.|  
|CORPROF_E_MODULE_IS_DYNAMIC|O módulo especificado foi gerado dinamicamente (por exemplo, por `Reflection.Emit`). Portanto, esse método não dá suporte a ele.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|O CLR não pôde reverter a função especificada porque uma solicitação de recompilação ativa correspondente não foi encontrada. Ou a recompilação nunca foi solicitada ou a função já foi revertida.|  
|Outros|O sistema operacional retornou uma falha fora do controle do CLR. Por exemplo, se uma chamada do sistema para alterar a proteção de acesso de uma página de memória falhar, o erro do sistema operacional será exibido.|  
  
## <a name="remarks"></a>Comentários  
 Na próxima vez que qualquer uma das instâncias de função revereted forem chamadas, as versões originais das funções serão executadas. Se uma função já estiver em execução, ela concluirá a execução da versão que está em execução.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
