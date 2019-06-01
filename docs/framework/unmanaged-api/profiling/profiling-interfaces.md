---
title: Criação de perfil de interfaces
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457469"
---
# <a name="profiling-interfaces"></a>Criação de perfil de interfaces
Esta seção descreve as interfaces não gerenciadas que permitem criar o perfil de um programa que está sendo executado no CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Interface ICLRProfiling](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Fornece o [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) método, que permite que um criador de perfil anexar a um processo em execução.  
  
 [Interface ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Permite que o criador de perfil informe ao CLR de referências de assembly que o criador de perfil será adicionado a [ICorProfilerCallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) retorno de chamada.  
  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Fornece métodos usados pelo CLR para notificar um criador de perfis de código quando ocorrerem os eventos assinados pelo criador de perfis.  
  
 [Interface ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Estende a interface `ICorProfilerCallback` com retornos de chamadas com suporte no .NET Framework 2.0 e versões posteriores.  
  
 [Interface ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Fornece métodos de retorno de chamada que o CLR usa para comunicar anexação e desanexação de informações de estado ao criador de perfis.  
  
 [Interface ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Fornece métodos de retorno de chamada que o CLR usa para comunicar informações ao criador de perfis.  
  
 [Interface ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Fornece um método que identifica o fechamento transitivo de objetos referenciados por raízes de coleta de lixo.  
  
 [Interface ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Fornece um método de retorno de chamada que o CLR usa para notificar um criador de perfis de que um assembly está carregando.  
  
 [Interface ICorProfilerCallback7](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Fornece um método de retorno de chamada que o common language runtime usa para notificar o criador de perfil que o fluxo de símbolo associado a um módulo na memória é atualizado.  

[Interface ICorProfilerCallback8](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Fornece métodos de retorno de chamada que o common language runtime usa para notificar o criador de perfil que a compilação JIT de um método dinâmico foi iniciado e concluído.

[Interface ICorProfilerCallback9](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Fornece um método de retorno de chamada que o common language runtime usa para notificar o criador de perfil um método dinâmico é lixo coletado e, subsequentemente, foi descarregado.

 [Interface ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Fornece métodos que permitem um criador de perfis de código se comunicar com o CLR para controlar como o compilador JIT deve gerar código ao recompilar um método específico.  
  
 [Interface ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Fornece métodos para iterar de forma sequencial por meio de uma coleção de funções no CLR.  
  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Fornece métodos para uso por criadores de perfis de código para se comunicar com o CLR para controlar o monitoramento de eventos e solicitar informações.  
  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Estende a interface de `ICorProfilerInfo` com métodos que têm suporte no .NET Framework 2.0 e em versões posteriores.  
  
 [Interface ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Estende o `ICorProfilerInfo2` interface com métodos com suporte no .NET Framework 4 e versões posteriores.  
  
 [Interface ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Fornece métodos que os criadores de perfis de código usam para se comunicar com o CLR para controlar o monitoramento de eventos e solicitar informações.  
  
 [Interface ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Fornece métodos para uso por criadores de perfis de código para se comunicar com o CLR para controlar o monitoramento de eventos.  
  
 [Interface ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Fornece um enumerador para todos os métodos que pertencem a um determinado módulo do NGen e que são embutidos no corpo de um determinado método.  
  
 [Interface ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Fornece um método para aplicar recentemente definido metadados para um módulo e que fornece acesso a um fluxo de símbolo na memória.  
  
 [Interface ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Fornece métodos para iterar de forma sequencial por meio de uma coleção de módulos carregados pelo aplicativo ou pelo criador de perfis.  
  
 [Interface ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Fornece métodos para iterar de forma sequencial por meio de uma coleção de objetos congelados que são gerados pelo [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [Interface ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Fornece métodos para iterar de forma sequencial por meio de uma coleção de threads no CLR.  
  
 [Interface IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Fornece o [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) método alocar memória para um novo corpo de função do Microsoft intermediate language (MSIL).  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Visão geral da criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
