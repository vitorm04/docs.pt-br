---
title: "Método ICorProfilerInfo4::InitializeCurrentThread"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc19ae86c266c74097bd649aa96f532528df3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>Método ICorProfilerInfo4::InitializeCurrentThread
Inicializa o thread atual antes de criador de perfil subsequente chamadas à API no mesmo thread, portanto esse deadlock pode ser evitado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Comentários  
 É recomendável que você chamar `InitializeCurrentThread` em qualquer thread que chamará um criador de perfil API enquanto houver suspenso threads. Esse método é normalmente usado por criadores de perfil de amostragem que criar seu próprio thread para chamar o [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método executar pilha orienta enquanto o thread de destino está suspenso. Chamando `InitializeCurrentThread` depois quando o criador de perfil primeiro cria o thread de amostragem, criadores de perfil podem garantir que a inicialização lenta por thread que o CLR executaria caso contrário, durante a primeira chamada para `DoStackSnapshot` agora pode ocorrer com segurança quando nenhum outro thread está suspenso.  
  
> [!NOTE]
>  `InitializeCurrentThread`faz a inicialização com antecedência para concluir tarefas que usam bloqueios e podem fazer um deadlock. Chamar `InitializeCurrentThread` somente quando não há nenhum thread suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Criação de perfil](../../../../docs/framework/unmanaged-api/profiling/index.md)
