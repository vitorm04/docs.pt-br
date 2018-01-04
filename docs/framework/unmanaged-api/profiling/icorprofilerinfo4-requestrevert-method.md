---
title: "Método ICorProfilerInfo4::RequestRevert"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.RequestRevert
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f0bf926bc6ba458745231bc17ce20dbe5cdbd1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4requestrevert-method"></a>Método ICorProfilerInfo4::RequestRevert
Reverte todas as instâncias das funções especificadas para suas versões originais.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cFunctions`  
 [in] O número de funções para reverter.  
  
 `moduleIds`  
 [in] Especifica o `moduleId` parte das (`module`, `methodDef`) pares que identificam as funções para ser revertido.  
  
 `methodIds`  
 [in] Especifica o `methodId` parte das (`module`, `methodDef`) pares que identificam as funções para ser revertido.  
  
 `status`  
 [out] Uma matriz de HRESULTs listadas na seção "Status HRESULTs" mais adiante neste tópico. Cada HRESULT indica o êxito ou falha da tentativa de reverter a cada função especificada nas matrizes paralelas `moduleIds` e `methodIds`.  
  
## <a name="return-value"></a>Valor de retorno  
 Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|Foi feita uma tentativa para reverter todas as solicitações; No entanto, a matriz de status retornado deve ser verificada para determinar quais funções foram revertidas com êxito.|  
|CORPROF_E_CALLBACK4_REQUIRED|O criador de perfil deve implementar o [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface para a chamada com suporte.|  
|CORPROF_E_REJIT_NOT_ENABLED|Recompilação de JIT não foi habilitada. Você deve habilitar recompilação JIT durante a inicialização por meio de [: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) método para definir o `COR_PRF_ENABLE_REJIT` sinalizador.|  
|E_INVALIDARG|`cFunctions`é 0, ou `moduleIds` ou `methodIds` é `NULL`.|  
|E_OUTOFMEMORY|O CLR não pôde concluir a solicitação porque ele ficou sem memória.|  
  
## <a name="status-hresults"></a>Status HRESULTS  
  
|Matriz de status de HRESULT|Descrição|  
|--------------------------|-----------------|  
|S_OK|A função correspondente foi revertida com êxito.|  
|E_INVALIDARG|O parâmetro `moduleID` ou `methodDef` é `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|O módulo ainda não foi totalmente carregado ou ele está sendo descarregado.|  
|CORPROF_E_MODULE_IS_DYNAMIC|O módulo especificado foi gerado dinamicamente (por exemplo, `Reflection.Emit`). Portanto, ele não é suportado por este método.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|O CLR não foi possível reverter a função especificada, pois uma solicitação de recompilação active correspondente não foi encontrada. Ou a recompilação nunca foi solicitada ou a função já foi revertida.|  
|Outros|O sistema operacional retornou uma falha de fora do controle do CLR. Por exemplo, se uma chamada do sistema para alterar a proteção de acesso de uma página de memória falhar, será exibido o erro do sistema operacional.|  
  
## <a name="remarks"></a>Comentários  
 Na próxima vez que nenhuma das instâncias de função revereted são chamadas, as versões originais das funções serão executadas. Se uma função estiver sendo executado, ele terminará executando a versão que está sendo executado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
