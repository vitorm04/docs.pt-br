---
title: Visão geral da criação de perfil
ms.date: 03/30/2017
helpviewer_keywords:
- managed code, profiling API support
- unmanaged code, combining with managed code in profiling
- notification threads [.NET Framework profiling]
- unmanaged code, profiling
- profiling API [.NET Framework], and COM
- profiling API [.NET Framework], unmanaged code profiling
- profilers, writing
- profiling API [.NET Framework], call stacks
- code profilers, writing
- profiling API [.NET Framework], security considerations
- profiling API [.NET Framework], managed code support
- common language runtime, profiling
- profiling API [.NET Framework], notification threads
- call stacks [.NET Framework profiling]
- profiling API [.NET Framework], stack depth
- common language runtime, writing a profiler
- profiling API [.NET Framework], information retrieval interfaces
- shadow stacks [.NET Framework profiling]
- COM, using in the profiling API
- stack snapshots [.NET Framework profiling]
- profiling API [.NET Framework], supported features
- profiling API [.NET Framework], overview
- security, profiling API considerations
- stack depth [.NET Framework profiling]
ms.assetid: 864c2344-71dc-46f9-96b2-ed59fb6427a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b38b64e1c86174bea11086e722ed86b0a0046e2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="profiling-overview"></a>Visão geral da criação de perfil
<a name="top"></a> Um criador de perfil é uma ferramenta que monitora a execução de outro aplicativo. Um criador de perfil de tempo de execução (CLR) de linguagem comum é uma biblioteca de vínculo dinâmico (DLL) que consiste em funções que recebem mensagens e enviam mensagens para o CLR usando a API de criação de perfil. O criador de perfil DLL é carregado pelo CLR em tempo de execução.  
  
 Ferramentas de criação de perfil tradicionais se concentram em avaliar a execução do aplicativo. Ou seja, eles medem o tempo gasto em cada função ou o uso de memória do aplicativo ao longo do tempo. A API de criação de perfil tem como alvo uma classe mais ampla de ferramentas de diagnóstico como utilitários de cobertura de código e até mesmo avançados recursos de depuração. Esses usos são todos os diagnóstico por natureza. A API de criação de perfil não mede apenas também monitora a execução de um aplicativo. Por esse motivo, a API de criação de perfil nunca deve ser usada pelo próprio aplicativo, e a execução do aplicativo não deve depender (ou ser afetado por) o criador de perfil.  
  
 Um aplicativo de CLR de criação de perfil requer suporte maior que a criação de perfil convencionalmente compilado código de máquina. Isso ocorre porque o CLR apresenta conceitos, como domínios de aplicativo, coleta de lixo, gerenciados manipulação de exceção, compilação just-in-time (JIT) do código (convertendo Microsoft intermediate language ou MSIL, o código para código de máquina nativo) e semelhante recursos. Convencionais mecanismos de criação de perfil não podem identificar ou fornecer informações úteis sobre esses recursos. A API de criação de perfil fornece essas informações ausentes com eficiência, com efeito mínimo sobre o desempenho do CLR e o aplicativo perfilado.  
  
 Compilação JIT em tempo de execução fornece boas oportunidades para criação de perfil. A API de criação de perfil permite que um criador de perfil alterar o fluxo de código MSIL na memória para uma rotina antes de ser compilado por JIT. Dessa maneira, o criador de perfil pode adicionar dinamicamente o código de instrumentação para rotinas específicas que precisam de mais investigação. Embora essa abordagem seja possível em cenários convencionais, é muito mais fácil de implementar para o CLR usando a API de criação de perfil.  
  
 Esta visão geral é composta pelas seguintes seções:  
  
-   [A API de criação de perfil](#profiling_api)  
  
-   [Recursos com suporte](#support)  
  
-   [Threads de notificação](#notification_threads)  
  
-   [Segurança](#security)  
  
-   [Combinando gerenciada e código em um criador de perfil de código não gerenciado](#combining_managed_unmanaged)  
  
-   [Criação de perfil de código não gerenciado](#unmanaged)  
  
-   [Usando COM](#com)  
  
-   [Pilhas de chamadas](#call_stacks)  
  
-   [Retornos de chamada e a profundidade da pilha](#callbacks)  
  
-   [Tópicos relacionados](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>A API de criação de perfil  
 Normalmente, a API de criação de perfil é usada para gravar um *criador de perfil de código*, que é um programa que monitora a execução de um aplicativo gerenciado.  
  
 A API de criação de perfil é usada por um criador de perfil DLL, que é carregado no mesmo processo que o aplicativo cujo perfil está sendo criado. O criador de perfil DLL implementa uma interface de retorno de chamada ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) no .NET Framework versão 1.0 e 1.1, [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) na versão 2.0 e posteriores). O CLR chama os métodos de interface para notificar o criador de perfil de eventos do processo com perfil. O criador de perfil pode chamar Voltar no tempo de execução, usando os métodos no [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) e [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfaces para obter informações sobre o estado do aplicativo perfilado.  
  
> [!NOTE]
>  Somente a parte da coleta de dados da solução de criador de perfil deve estar em execução no mesmo processo que o aplicativo perfilado. Todos os usuário interface e análise de dados deve ser executado em um processo separado.  
  
 A ilustração a seguir mostra como o criador de perfil DLL interage com o aplicativo cujo perfil está sendo criado e o CLR.  
  
 ![Arquitetura de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/media/profilingarch.png "ProfilingArch")  
Arquitetura de criação de perfil  
  
### <a name="the-notification-interfaces"></a>As Interfaces de notificação  
 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) podem ser consideradas como interfaces de notificação. Essas interfaces consistem em métodos como [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), e [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Cada vez que o CLR carrega ou descarrega uma classe, compila uma função, e assim por diante, ele chama o método correspondente do criador de perfil `ICorProfilerCallback` ou `ICorProfilerCallback2` interface.  
  
 Por exemplo, um criador de perfil pode medir o desempenho de código por meio de duas funções de notificação: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) e [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Ele apenas os carimbos de hora cada notificação, acumula os resultados e gera uma lista que indica quais funções consumiram mais tempo da CPU ou do relógio durante a execução do aplicativo.  
  
### <a name="the-information-retrieval-interfaces"></a>As Interfaces de recuperação de informações  
 As outras interfaces principais envolvidas na criação de perfil são [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) e [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). O criador de perfil chama essas interfaces conforme necessário para obter mais informações para ajudar a sua análise. Por exemplo, sempre que o CLR chama o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) função, ele fornece um identificador de função. O criador de perfil pode obter mais informações sobre essa função chamando o [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método para descobrir a classe do pai da função, seu nome e assim por diante.  
  
 [Voltar ao início](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Recursos compatíveis  
 A API de criação de perfil fornece informações sobre uma variedade de eventos e ações que ocorrem no common language runtime. Você pode usar essas informações para monitorar o funcionamento interno de processos e analisar o desempenho do seu aplicativo do .NET Framework.  
  
 A API de criação de perfil recupera informações sobre as ações e os eventos que ocorrem no CLR a seguir:  
  
-   Eventos de inicialização e desligamento do CLR.  
  
-   Domínio criação e desligamento eventos de aplicativo.  
  
-   Assembly Carregando e descarregando eventos.  
  
-   Módulo de carregamento e descarregamento de eventos.  
  
-   COM vtable criação e destruição de eventos.  
  
-   Just-in-time (JIT) compilação e eventos de densidade de código.  
  
-   Eventos de carregamento e descarregamento de classe.  
  
-   Eventos de criação e destruição de threads.  
  
-   Eventos de entrada e saída da função.  
  
-   Exceções.  
  
-   Faz a transição entre a execução de código gerenciado e não gerenciado.  
  
-   Faz a transição entre contextos diferentes de tempo de execução.  
  
-   Informações sobre a suspensão do tempo de execução.  
  
-   Informações sobre a atividade de coleta de tempo de execução memória heap e lixo.  
  
 A API de criação de perfil pode ser chamada em qualquer linguagem compatível COM o com (não gerenciado).  
  
 A API é eficiente em relação ao consumo de CPU e memória. Criação de perfil não envolve alterações para o aplicativo perfilado significativas de causar resultados incorretos.  
  
 A API de criação de perfil é útil para criadores de perfil de amostragem e não de amostragem. Um *criador de perfil de amostragem* inspeciona o perfil em tiques do relógio regular, digamos, a distância de 5 milissegundos. Um *criador de perfil de amostragem não* é informado de um evento de maneira síncrona com o thread que faz com que o evento.  
  
### <a name="unsupported-functionality"></a>Funcionalidade sem suporte  
 A API de criação de perfil não oferece suporte a seguinte funcionalidade:  
  
-   Código não gerenciado, que deve ser o perfil criado usando métodos convencionais do Win32. No entanto, o criador de perfil CLR inclui eventos de transição para determinar os limites entre código gerenciado e não gerenciado.  
  
-   Modificando automaticamente aplicativos que modificam o seu próprio código para fins como programação orientada a aspectos.  
  
-   Verificação de limites, porque a API de criação de perfil não fornecer essas informações. O CLR fornece suporte intrínseco para verificação de todo o código gerenciado de limites.  
  
-   Remoto de criação de perfil, que não é suportado pelos seguintes motivos:  
  
    -   Criação de perfil remota estende o tempo de execução. Quando você usa as interfaces de criação de perfil, você deve minimizar o tempo de execução para que os resultados de criação de perfil não serão indevidamente afetada. Isso é especialmente verdadeiro quando o desempenho de execução está sendo monitorado. No entanto, a criação de perfil remota não é uma limitação quando as interfaces de criação de perfil são usadas para monitorar o uso de memória ou para obter informações de tempo de execução sobre quadros de pilha, objetos e assim por diante.  
  
    -   O criador de perfil de código do CLR deve registrar uma ou mais interfaces de retorno de chamada com o tempo de execução no computador local em que o aplicativo perfilado está em execução. Isso limita a capacidade de criar um criador de perfil de código remota.  
  
-   Criação de perfil em ambientes de produção com requisitos de alta disponibilidade. A API de criação de perfil foi criada para dar suporte a diagnóstico de tempo de desenvolvimento. Ele não passou por testes rigorosos necessários para dar suporte a ambientes de produção.  
  
 [Voltar ao início](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Threads de notificação  
 Na maioria dos casos, o thread que gera um evento também executa as notificações. Essas notificações (por exemplo, [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) e [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) não é necessário fornecer o explícita `ThreadID`. Além disso, o criador de perfil pode decidir usar armazenamento de thread local para armazenar e atualizar seus blocos de análise, em vez de indexação os blocos de análise de armazenamento global, com base no `ThreadID` do thread afetado.  
  
 Observe que esses retornos de chamada não são serializados. Os usuários devem proteger seu código com a criação de estruturas de dados do thread-safe e bloqueando o código de criador de perfil, onde for necessário para impedir o acesso simultâneo de vários threads. Portanto, em certos casos, você pode receber uma sequência comum de retornos de chamada. Por exemplo, suponha que um aplicativo gerenciado é reproduzir dois threads que estão executando o código idêntico. Nesse caso, é possível receber um [: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) evento para alguma função de um thread e um `FunctionEnter` retorno de chamada do thread antes de receber o [ Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) retorno de chamada. Nesse caso, o usuário receberá uma `FunctionEnter` retorno de chamada para uma função que pode não ter sido totalmente just-in-time (JIT) compilado ainda.  
  
 [Voltar ao início](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Segurança  
 Um criador de perfil DLL é uma DLL não gerenciada que é executado como parte do mecanismo de execução do common language runtime. Como resultado, o código no criador de perfil de que dll não está sujeita às restrições gerenciados segurança de acesso ao código. As únicas limitações no criador de perfil DLL são aquelas impostas pelo sistema operacional no usuário que está executando o aplicativo perfilado.  
  
 Os autores do criador de perfil devem tomar precauções apropriadas para evitar problemas de segurança. Por exemplo, durante a instalação, um criador de perfil DLL deve ser adicionado a uma lista de controle de acesso (ACL) para que um usuário mal-intencionado não é possível modificá-lo.  
  
 [Voltar ao início](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Combinando gerenciada e código em um criador de perfil de código não gerenciado  
 Um criador de perfil escrito incorretamente pode causar referências circulares a mesmo, resultando em um comportamento imprevisível.  
  
 Crie a impressão de que você pode escrever um criador de perfil que contém os componentes gerenciados e não gerenciados que chamam uns aos outros por meio de chamadas de interoperabilidade ou indiretas COM uma revisão do CLR API de criação de perfil.  
  
 Embora seja possível a partir de uma perspectiva de design, a API de criação de perfil não oferece suporte a componentes gerenciados. Um criador de perfil CLR deve ser completamente não gerenciado. Tenta combinar código gerenciado e um criador de perfil CLR pode causar violações de acesso, a falha de programa ou deadlocks. Os componentes gerenciados do criador de perfil serão acionado eventos seus componentes não gerenciados, que chamam subsequentemente os componentes gerenciados novamente, resultando em referências circulares.  
  
 É o único local onde um criador de perfil CLR pode chamar código gerenciado com segurança no corpo Microsoft intermediate language (MSIL) de um método. A prática recomendada para modificar o corpo do MSIL é usar os métodos de recompilação de JIT no [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.  
  
 Também é possível usar os métodos de instrumentação anteriores para modificar MSIL. Antes que a compilação just-in-time (JIT) de uma função é concluída, o criador de perfil pode inserir chamadas gerenciadas no corpo de um método e, em seguida, a compilação JIT MSIL ele (consulte o [Getilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) método). Essa técnica pode ser usada com êxito para seletiva instrumentação de código gerenciado ou para reunir dados de desempenho e estatísticas sobre o JIT.  
  
 Como alternativa, um criador de perfil de código pode inserir ganchos nativo no corpo da MSIL de cada função gerenciada que chamam o código não gerenciado. Essa técnica pode ser usada para a instrumentação e a cobertura. Por exemplo, um criador de perfil de código foi possível inserir ganchos de instrumentação após cada bloco MSIL para garantir que o bloco foi executado. A modificação do corpo de um método MSIL é uma operação muito perfeita, e há muitos fatores que devem ser levadas em consideração.  
  
 [Voltar ao início](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Criação de perfil de código não gerenciado  
 O common language runtime (CLR) API de criação de perfil fornece suporte mínimo de criação de perfil de código não gerenciado. É fornecida a seguinte funcionalidade:  
  
-   Enumeração de cadeias de pilha. Esse recurso permite que um criador de perfil de código determinar o limite entre código gerenciado e o código não gerenciado.  
  
-   Determinar se uma cadeia de pilha corresponde ao código gerenciado ou código nativo.  
  
 Nas versões do .NET Framework 1.0 e 1.1, esses métodos estão disponíveis por meio do subconjunto no processo do CLR depuração da API. Elas são definidas no arquivo CorDebug.idl.  
  
 No .NET Framework 2.0 e posterior, você pode usar o [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método para essa funcionalidade.  
  
 [Voltar ao início](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>Usando COM  
 Embora as interfaces de criação de perfil são definidas como interfaces COM, o common language runtime (CLR) não realmente inicializar COM para usar essas interfaces. A razão é evitar ter que definir o modelo de threading, usando o [CoInitialize](http://msdn.microsoft.com/library/windows/desktop/ms678543\(v=vs.85\).aspx) função antes do aplicativo gerenciado tenha tido a oportunidade de especificar o modelo de threading desejado. Da mesma forma, o criador de perfil em si não deve chamar `CoInitialize`, pois ele pode escolher um modelo de threading é incompatível com o aplicativo que está sendo analisado e pode causar falha no aplicativo.  
  
 [Voltar ao início](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Pilhas de chamadas  
 A API de criação de perfil fornece duas maneiras de obter as pilhas de chamadas: um método de instantâneo de pilha, que permite a coleta esparsa de pilhas de chamadas, e um método de pilha de sombra, que controla a pilha de chamadas em todos os instantes.  
  
### <a name="stack-snapshot"></a>Instantâneo da pilha  
 Um instantâneo da pilha é um rastreamento da pilha de um thread em um momento no tempo. A API de criação de perfil dá suporte a rastreamento de funções gerenciadas na pilha, mas deixa o rastreamento de funções não gerenciadas para o movimentador de pilha do profiler.  
  
 Para obter mais informações sobre como programar o criador de perfil para movimentar pilhas gerenciadas, consulte o [Icorprofilerinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método neste conjunto de documentação, e [movimentação de pilhas do criador de perfil do .NET Framework 2.0: Noções básicas e além](http://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Pilha de sombra  
 Usando o método de instantâneo com muita frequência pode criar rapidamente um problema de desempenho. Se você quiser fazer rastreamentos de pilha com frequência, em vez disso, o criador de perfil deve criar uma pilha de sombra usando o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), e [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) retornos de chamada de exceção. A pilha de sombra é sempre atual e rapidamente pode ser copiada para o armazenamento, sempre que um instantâneo da pilha é necessária.  
  
 Uma pilha de sombra pode obter informações sobre instanciações genéricas, valores de retorno e argumentos de função. Essas informações estão disponíveis apenas por meio da pilha de sombra e podem ser obtidas quando o controle é entregue para uma função. No entanto, essas informações podem não estar disponíveis durante a execução da função.  
  
 [Voltar ao início](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Retornos de chamada e a profundidade da pilha  
 Retornos de chamada do criador de perfil podem ser emitidos em circunstâncias muito restritas a pilha e um estouro de pilha em um retorno de chamada do criador de perfil levará a uma saída de processo imediato. Um criador de perfil deve verificar se a ser usada como a pilha pequeno quanto possível em resposta a retornos de chamada. Se o criador de perfil se destina para uso em processos que são robustos em estouro de pilha, o criador de perfil em si também deve evitar estouro de pilha de disparo.  
  
 [Voltar ao início](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Configurando um ambiente de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Explica como inicializar um criador de perfil, defina as notificações de eventos e criar o perfil de um serviço do Windows.|  
|[Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Descreve as interfaces não gerenciadas que usa a API de criação de perfil.|  
|[Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Descreve as funções estáticas globais não gerenciadas que usa a API de criação de perfil.|  
|[Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Descreve as enumerações não gerenciadas que usa a API de criação de perfil.|  
|[Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Descreve as estruturas não gerenciadas que usa a API de criação de perfil.|
