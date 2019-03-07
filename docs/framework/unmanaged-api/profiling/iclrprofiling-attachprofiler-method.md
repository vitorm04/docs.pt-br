---
title: Método ICLRProfiling::AttachProfiler
ms.date: 03/30/2017
api_name:
- IClrProfiling.AttachProfiler Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- IClrProfiling::AttachProfiler
helpviewer_keywords:
- AttachProfiler method [.NET Framework profiling]
- IClrProfiling::AttachProfiler method [.NET Framework profiling]
ms.assetid: 535a6839-c443-405b-a6f4-e2af90725d5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fcbc75d17f0c154671d5997d7e6cbb59ef8440e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468995"
---
# <a name="iclrprofilingattachprofiler-method"></a>Método ICLRProfiling::AttachProfiler
Anexa o criador de perfil especificado para o processo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT AttachProfiler(  
  [in] DWORD dwProfileeProcessID,  
  [in] DWORD dwMillisecondsMax,                     // optional  
  [in] const CLSID * pClsidProfiler,  
  [in] LPCWSTR wszProfilerPath,                     // optional  
  [in] size_is(cbClientData)] void * pvClientData,  // optional  
  [in] UINT cbClientData);                          // optional  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwProfileeProcessID`  
 [in] A ID do processo do processo ao qual o criador de perfil deve ser anexado. Em um computador de 64 bits, número de bits do processo de criação de perfil deve corresponder ao número de bits do processo de gatilho que está chamando `AttachProfiler`. Se a conta de usuário sob a qual `AttachProfiler` é chamado tem privilégios administrativos, o processo de destino pode ser qualquer processo no sistema. Caso contrário, o processo de destino deve ser de propriedade da mesma conta de usuário.  
  
 `dwMillisecondsMax`  
 [in] A duração de tempo, em milissegundos, para `AttachProfiler` para ser concluída. O processo de gatilho deve passar um tempo limite que é conhecido por ser suficiente para o criador de perfil específica concluir sua inicialização.  
  
 `pClsidProfiler`  
 [in] Um ponteiro para o CLSID do criador de perfil a ser carregado. O processo de gatilho pode reutilizar essa memória após `AttachProfiler` retorna.  
  
 `wszProfilerPath`  
 [in] O caminho completo para o arquivo DLL do criador de perfil a ser carregado. Essa cadeia de caracteres deve conter não mais do que 260 caracteres, incluindo o terminador nulo. Se `wszProfilerPath` é nulo ou uma cadeia de caracteres vazia, o common language runtime (CLR) tenta encontrar o local do arquivo DLL do criador de perfil ao procurar no Registro CLSID que `pClsidProfiler` aponta.  
  
 `pvClientData`  
 [in] Um ponteiro para dados a serem passados para o criador de perfil, o [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) método. O processo de gatilho pode reutilizar essa memória após `AttachProfiler` retorna. Se `pvClientData` for nulo, `cbClientData` deve ser 0 (zero).  
  
 `cbClientData`  
 [in] O tamanho, em bytes, dos dados que `pvClientData` aponta.  
  
## <a name="return-value"></a>Valor de retorno  
 Esse método retorna os HRESULTs a seguir.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|S_OK|O criador de perfil especificado foi anexado com êxito o processo de destino.|  
|CORPROF_E_PROFILER_ALREADY_ACTIVE|Já existe um criador de perfil ativas ou anexando ao processo de destino.|  
|CORPROF_E_PROFILER_NOT_ATTACHABLE|O criador de perfil especificado não oferece suporte para o anexo. O processo de gatilho pode tentar anexar um criador de perfil diferente.|  
|CORPROF_E_PROFILEE_INCOMPATIBLE_WITH_TRIGGER|Não é possível solicitar um anexo do criador de perfil, porque a versão do processo de destino é incompatível com o processo atual que está chamando `AttachProfiler`.|  
|HRESULT_FROM_WIN32(ERROR_ACCESS_DENIED)|O usuário do processo de gatilho não tem acesso ao processo de destino.|  
|HRESULT_FROM_WIN32(ERROR_PRIVILEGE_NOT_HELD)|O usuário do processo de gatilho não tem os privilégios necessários para anexar um criador de perfil ao processo de destino fornecido. O log de eventos do aplicativo pode conter mais informações.|  
|CORPROF_E_IPC_FAILED|Ocorreu uma falha ao se comunicar com o processo de destino. Isso normalmente acontece se o processo de destino estava sendo desligado.|  
|HRESULT_FROM_WIN32(ERROR_FILE_NOT_FOUND)|O processo de destino não existe ou não está em execução um CLR que dá suporte ao anexo. Isso pode indicar que o CLR foi descarregado desde a chamada para o método de enumeração de tempo de execução.|  
|HRESULT_FROM_WIN32(ERROR_TIMEOUT)|O tempo limite expirou sem início para carregar o criador de perfil. Você pode repetir a operação de anexação. Tempos limite ocorre quando um finalizador no processo de destino é executado por um período maior que o valor de tempo limite.|  
|E_INVALIDARG|Um ou mais parâmetros possuem valores inválidos.|  
|E_FAIL|Ocorreu falha de alguns outra, não especificada.|  
|Outros códigos de erro|Se o criador de perfil [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) método retorna um HRESULT que indica falha, `AttachProfiler` Retorna ou mesmo HRESULT. Nesse caso, E_NOTIMPL é convertido em CORPROF_E_PROFILER_NOT_ATTACHABLE.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="memory-management"></a>Gerenciamento de memória  
 Manter com as convenções de COM, o chamador de `AttachProfiler` (por exemplo, o código do gatilho criado pelo desenvolvedor do criador de perfil) é responsável por alocar e desalocar a memória para os dados que o `pvClientData` parâmetro aponta. Quando o CLR executa o `AttachProfiler` chamada, ele faz uma cópia da memória que `pvClientData` aponta para e a transmite para o processo de destino. Quando o CLR dentro do processo de destino recebe sua própria cópia da `pvClientData` bloco, ele passa o bloco para o criador de perfil por meio de `InitializeForAttach` método e, em seguida, desaloca sua cópia do `pvClientData` bloco do processo de destino.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
