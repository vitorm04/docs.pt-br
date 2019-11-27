---
title: Criando perfil de funções estáticas globais
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: d1d9b0a4c61ce7c3f8f9792046fb4bddf0fdfa05
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447436"
---
# <a name="profiling-global-static-functions"></a>Criando perfil de funções estáticas globais
Esta seção descreve as funções de API não gerenciadas que a API de criação de perfil usa.  
  
## <a name="in-this-section"></a>Nesta seção  
  
## <a name="net-framework-version-1-profiling-functions"></a>Funções de criação de perfil .NET Framework versão 1  
 [Função FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função. Preterido no .NET Framework 2,0.  
  
 [Função FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Notifica o criador de perfil de que uma função está prestes a retornar ao chamador. Preterido no .NET Framework 2,0.  
  
 [Função FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função. Preterido no .NET Framework 2,0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Funções de criação de perfil .NET Framework versão 2  
 [Função FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) para essa função. Também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função  
  
 [Função FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função e fornece informações sobre o quadro de pilha e os argumentos de função. Preterido no .NET Framework 4.  
  
 [Função FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Notifica o criador de perfil de que uma função está prestes a retornar ao chamador e fornece informações sobre o quadro de pilha e o valor de retorno da função. Preterido no .NET Framework 4.  
  
 [Função FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função e fornece informações sobre o registro de ativação. Preterido no .NET Framework 4.  
  
 [Função StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Fornece ao criador de perfil informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante uma movimentação de pilha, que é iniciada pelo método [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .  
  
## <a name="net-framework-version-4-profiling-functions"></a>Funções de criação de perfil .NET Framework versão 4  
 [Função FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Notifica o criador de perfil de que o identificador fornecido de uma função pode ser remapeado para uma ID alternativa a ser usada nos retornos de chamada [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) para essa função. Também permite que o criador de perfil indique se deseja receber retornos de chamada para essa função.  
  
 `FunctionIDMapper2` estende a função [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) com um parâmetro `clientData`, que os profileres podem usar para fazer a ambiguidade entre os tempos de execução.  
  
 [Função FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função.  
  
 [Função FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função e fornece um identificador que pode ser passado para [ICorProfilerInfo3:: GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) para recuperar o quadro de pilha e os argumentos de função.  
  
 [Função FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Notifica o criador de perfil que o controle está sendo retornado de uma função.  
  
 [Função FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Notifica o criador de perfil que o controle está sendo retornado de uma função e fornece um identificador que pode ser passado para [ICorProfilerInfo3:: GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) para recuperar o quadro de pilha e o valor de retorno.  
  
 [Função FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função.  
  
 [Função FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Notifica o criador de perfil de que a função atualmente em execução está prestes a executar uma chamada tail para outra função e fornece um identificador que pode ser passado para [ICorProfilerInfo3:: GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para recuperar o quadro de pilha.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Visão geral da criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
