---
title: Método ICorProfilerInfo4::InitializeCurrentThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 39882a554f9d47040bef00ff320d15b56abea533
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445720"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>Método ICorProfilerInfo4::InitializeCurrentThread
Inicializa o thread atual antes das chamadas de API do criador de perfil subsequentes no mesmo thread, para que o deadlock possa ser evitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Comentários  
 É recomendável chamar `InitializeCurrentThread` em qualquer thread que chamará uma API do profiler enquanto houver threads suspensos. Esse método é normalmente usado por infilers de amostragem que criam seu próprio thread para chamar o método [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) para executar movimentações de pilha enquanto o thread-alvo é suspenso. Ao chamar `InitializeCurrentThread` uma vez em que o criador de perfil cria pela primeira vez o thread de amostragem, os profileres podem garantir que a inicialização lenta por thread que o CLR executaria, de outra forma, durante a primeira chamada para `DoStackSnapshot` possa ocorrer com segurança quando nenhum outro thread for suspenso.  
  
> [!NOTE]
> `InitializeCurrentThread` faz a inicialização com antecedência para concluir as tarefas que usam bloqueios e pode travar. Chame `InitializeCurrentThread` somente quando não houver threads suspensos.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
