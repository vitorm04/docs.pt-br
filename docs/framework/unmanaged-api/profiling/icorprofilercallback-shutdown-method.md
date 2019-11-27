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
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446937"
---
# <a name="icorprofilercallbackshutdown-method"></a>Método ICorProfilerCallback::Shutdown
Notifica o criador de perfil de que o aplicativo está sendo desligado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Comentários  
 O código do criador de perfil não pode chamar com segurança os métodos da interface [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) depois que o método `Shutdown` é chamado. Todas as chamadas para os métodos de `ICorProfilerInfo` resultam em um comportamento indefinido após o retorno do método `Shutdown`. Determinados eventos imutáveis ainda podem ocorrer após o desligamento; o criador de perfil deve tomar cuidado para retornar imediatamente quando isso ocorrer.  
  
 O método `Shutdown` será chamado somente se o aplicativo gerenciado que está sendo criado com perfil for iniciado como código gerenciado (ou seja, o quadro inicial na pilha de processo é gerenciado). Se o aplicativo foi iniciado como código não gerenciado, mas posteriormente entrou em código gerenciado, criando, assim, uma instância do Common Language Runtime (CLR), `Shutdown` não será chamado. Nesses casos, o criador de perfil deve incluir em sua biblioteca um `DllMain` rotina que usa o valor de DLL_PROCESS_DETACH para liberar recursos e executar o processamento de limpeza de seus dados, como a liberação de rastreamentos para o disco e assim por diante.  
  
 Em geral, o criador de perfil deve lidar com desligamentos inesperados. Por exemplo, um processo pode ser interrompido por Win32's `TerminateProcess` método (declarado em Winbase. h). Em outros casos, o CLR irá parar determinados threads gerenciados (threads em segundo plano) sem fornecer mensagens de destruição ordenada para eles.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Método Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
