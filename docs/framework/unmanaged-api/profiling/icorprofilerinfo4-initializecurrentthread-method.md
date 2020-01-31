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
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868428"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>Método ICorProfilerInfo4::InitializeCurrentThread
Inicializa o thread atual antes das chamadas de API do criador de perfil subsequentes no mesmo thread, para que o deadlock possa ser evitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Comentários  
 É recomendável chamar `InitializeCurrentThread` em qualquer thread que chamará uma API do profiler enquanto houver threads suspensos. Esse método é normalmente usado por infilers de amostragem que criam seu próprio thread para chamar o método [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) para executar movimentações de pilha enquanto o thread-alvo é suspenso. Ao chamar `InitializeCurrentThread` uma vez em que o criador de perfil cria pela primeira vez o thread de amostragem, os profileres podem garantir que a inicialização lenta por thread que o CLR executaria, de outra forma, durante a primeira chamada para `DoStackSnapshot` possa ocorrer com segurança quando nenhum outro thread for suspenso.  
  
> [!NOTE]
> `InitializeCurrentThread` faz a inicialização com antecedência para concluir as tarefas que usam bloqueios e pode travar. Chame `InitializeCurrentThread` somente quando não houver threads suspensos.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo4](icorprofilerinfo4-interface.md)
- [Interfaces de criação de perfil](profiling-interfaces.md)
- [Criação de perfil](index.md)
