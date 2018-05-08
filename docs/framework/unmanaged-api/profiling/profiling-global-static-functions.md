---
title: Criando perfil de funções estáticas globais
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bb5d93c91de857ebbee63009cad73fba7e1d284
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="profiling-global-static-functions"></a>Criando perfil de funções estáticas globais
Esta seção descreve as funções de API não gerenciadas que usa a API de criação de perfil.  
  
## <a name="in-this-section"></a>Nesta seção  
  
## <a name="net-framework-version-1-profiling-functions"></a>Funções de criação de perfil do .NET framework versão 1  
 [Função FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função. Obsoleto no .NET Framework 2.0.  
  
 [Função FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Notifica o criador de perfil que uma função está prestes a retornar ao chamador. Obsoleto no .NET Framework 2.0.  
  
 [Função FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função. Obsoleto no .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Funções de criação de perfil do .NET framework versão 2  
 [Função FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Notifica o criador de perfil que o identificador especificado de uma função pode ser mapeado novamente para uma ID alternativa a ser usado no [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), e [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) retornos de chamada para essa função. Também permite que o criador de perfil indicar se deseja receber retornos de chamada de função  
  
 [Função FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função e fornece informações sobre a pilha de argumentos de função e de quadro. Preterido no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Notifica o criador de perfil que uma função está prestes a retornar ao chamador e fornece informações sobre a pilha quadro e função de valor retornado. Preterido no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função e fornece informações sobre o quadro de pilhas. Preterido no [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Função StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Fornece o criador de perfil com informações sobre cada quadro gerenciado e cada execução de quadros não gerenciados na pilha durante um exame da pilha, que é iniciado com a [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método.  
  
## <a name="net-framework-version-4-profiling-functions"></a>Funções de criação de perfil do .NET framework versão 4  
 [Função FunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Notifica o criador de perfil que o identificador especificado de uma função pode ser mapeado novamente para uma ID alternativa a ser usado no [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), e [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), e [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) retornos de chamada para essa função. Também permite que o criador de perfil indicar se deseja receber retornos de chamada para essa função.  
  
 `FunctionIDMapper2` estende o [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funcionar com um `clientData` parâmetro, que criadores de perfil podem usar para resolver a ambiguidade entre os tempos de execução.  
  
 [Função FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função.  
  
 [Função FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Notifica o criador de perfil que o controle está sendo passado para uma função e fornece um identificador que pode ser passado para [ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) para recuperar os argumentos de quadro e função de pilha.  
  
 [Função FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Notifica o criador de perfil que o controle está sendo retornado de uma função.  
  
 [Função FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Notifica o criador de perfil que o controle está sendo retornado de uma função e fornece um identificador que pode ser passado para [ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) para recuperar o quadro de pilhas e o valor de retorno.  
  
 [Função FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função.  
  
 [Função FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Notifica o criador de perfil que a função atualmente em execução está prestes a realizar uma chamada tail para outra função e fornece um identificador que pode ser passado para [ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) para recuperar o quadro de pilhas.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Visão geral da criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
