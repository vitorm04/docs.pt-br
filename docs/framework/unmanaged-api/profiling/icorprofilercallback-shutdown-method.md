---
title: Método ICorProfilerCallback::Shutdown
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1696cb49170ba245a657e5efb6c8ba4b694af32f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192635"
---
# <a name="icorprofilercallbackshutdown-method"></a>Método ICorProfilerCallback::Shutdown
Notifica o criador de perfil que o aplicativo está sendo desligado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Comentários  
 O código do criador de perfil com segurança não é possível chamar métodos do [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface após o `Shutdown` método é chamado. Todas as chamadas para `ICorProfilerInfo` métodos resultam em comportamento indefinido após a `Shutdown` retorno do método. Determinados eventos imutáveis ainda poderão ocorrer após o desligamento; o criador de perfil deve cuidar para retornar imediatamente quando isso ocorre.  
  
 O `Shutdown` método será chamado apenas se o aplicativo gerenciado que está sendo analisado começou como código gerenciado (ou seja, o quadro inicial na pilha de processo é gerenciado). Se o aplicativo de início do código não gerenciado, mas posteriormente entrou no código gerenciado, criando uma instância do common language runtime (CLR), em seguida, `Shutdown` não será chamado. Nesses casos, o criador de perfil deve incluir em sua biblioteca de um `DllMain` rotina que usa o DLL_PROCESS_DETACH valor para liberar todos os recursos e executar o processamento de limpar seus dados, como liberar os rastreamentos no disco e assim por diante.  
  
 Em geral, o criador de perfil deve lidar com desligamentos inesperados. Por exemplo, um processo pode ser interrompido por do Win32 `TerminateProcess` método (declarado em Winbase). Em outros casos, o CLR interromperá a determinados threads gerenciados (threads de segundo plano) sem a entrega de mensagens de destruição ordenada para eles.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf.idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
