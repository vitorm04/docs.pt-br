---
title: "Método ICorProfilerCallback::Shutdown"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 42c9abc3c255f7ddda5e7934c495b073a7b1f6fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackshutdown-method"></a>Método ICorProfilerCallback::Shutdown
Notifica o criador de perfil que o aplicativo está sendo desligado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Comentários  
 O código de criador de perfil com segurança não é possível chamar métodos do [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface após o `Shutdown` método é chamado. Todas as chamadas para `ICorProfilerInfo` métodos resultam em comportamento indefinido após o `Shutdown` método retorna. Certos eventos imutáveis ainda podem ocorrer após o desligamento; o criador de perfil deve prestar atenção ao retornar imediatamente quando isso ocorre.  
  
 O `Shutdown` método será chamado apenas se o aplicativo gerenciado que está sendo criado o perfil de início do código gerenciado (ou seja, o quadro inicial na pilha de processo é gerenciado). Se o aplicativo foi iniciado como código não gerenciado, mas posteriormente entrou no código gerenciado, criando uma instância do common language runtime (CLR), em seguida, `Shutdown` não será chamado. Para esses casos, o criador de perfil deve incluir em sua biblioteca de um `DllMain` rotina que usa o DLL_PROCESS_DETACH valor para liberar os recursos e executar o processamento de limpar seus dados, como a eliminação de rastreamentos em disco e assim por diante.  
  
 Em geral, o criador de perfil deve lidar com desligamentos inesperados. Por exemplo, um processo pode ser interrompido por do Win32 `TerminateProcess` método (declarado em Winbase). Em outros casos, o CLR irá parar determinados threads gerenciados (threads em segundo plano) sem a entrega de mensagens de destruição ordenada para eles.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Método Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
