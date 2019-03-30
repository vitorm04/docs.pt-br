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
ms.openlocfilehash: 598722c44d8d20adab9ce7d624edb820f67c0fa4
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654088"
---
# <a name="profiling-overview"></a>Visão geral da criação de perfil
<a name="top"></a> Um criador de perfil é uma ferramenta que monitora a execução de outro aplicativo. Um criador de perfil de runtime (CLR) de linguagem comum é uma biblioteca de vínculo dinâmico (DLL) que consiste em funções que recebem mensagens de e enviam mensagens para o CLR usando a API de criação de perfil. A DLL do criador de perfil é carregada pelo CLR no tempo de execução.  
  
 Ferramentas de criação de perfil tradicionais se concentram em avaliar a execução do aplicativo. Ou seja, elas medem o tempo gasto em cada função ou o uso de memória do aplicativo ao longo do tempo. A API de criação de perfil tem como alvo uma classe mais ampla de ferramentas de diagnóstico, como utilitários de cobertura de código e até mesmo auxiliares de depuração avançada. Esses usos são todos de diagnóstico por natureza. A API de criação de perfil não apenas avalia, mas também monitora a execução de um aplicativo. Por esse motivo, a API de criação de perfil nunca deve ser usada pelo próprio aplicativo e a execução do aplicativo não deve depender (ou ser afetada) o criador de perfil.  
  
 Perfil de um aplicativo CLR requer mais suporte do que a criação de perfil convencionalmente compilou o código de máquina. Isso ocorre porque o CLR introduz conceitos como domínios de aplicativo, coleta de lixo gerenciada tratamento de exceções, compilação just-in-time (JIT) do código (convertendo Microsoft intermediate language ou MSIL, em código de máquina nativo) e outros semelhantes recursos. Mecanismos convencionais de criação de perfil não podem identificar ou fornecer informações úteis sobre esses recursos. A API de criação de perfil fornece essas informações perdidas de maneira eficiente, com efeito mínimo sobre o desempenho do CLR e aplicativo com perfil.  
  
 A compilação JIT em tempo de execução oferece boas oportunidades para criação de perfil. A API de criação de perfil permite que um criador de perfil alterar o fluxo de código MSIL na memória para uma rotina antes de ser compilado por JIT. Dessa forma, o criador de perfil pode dinamicamente adicionar código de instrumentação a rotinas específicas que precisam de mais investigação. Embora essa abordagem seja possível em cenários convencionais, é muito mais fácil de implementar para o CLR usando a API de criação de perfil.  
  
 Esta visão geral é composta pelas seguintes seções:  
  
-   [A API de criação de perfil](#profiling_api)  
  
-   [Recursos com suporte](#support)  
  
-   [Threads de notificação](#notification_threads)  
  
-   [Segurança](#security)  
  
-   [Combinar o código gerenciado e em um código Profiler](#combining_managed_unmanaged)  
  
-   [Criação de perfil de código não gerenciado](#unmanaged)  
  
-   [Usando COM](#com)  
  
-   [Pilhas de chamadas](#call_stacks)  
  
-   [Retornos de chamada e profundidade da pilha](#callbacks)  
  
-   [Tópicos relacionados](#related_topics)  
  
<a name="profiling_api"></a>   
## <a name="the-profiling-api"></a>A API de criação de perfil  
 Normalmente, a API de criação de perfil é usada para gravar uma *criador de perfil de código*, que é um programa que monitora a execução de um aplicativo gerenciado.  
  
 A API de criação de perfil é usada por um criador de perfil DLL, que é carregado no mesmo processo que o aplicativo que está sendo analisado. A DLL do criador de perfil implementa uma interface de retorno de chamada ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) no .NET Framework versão 1.0 e 1.1, [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) na versão 2.0 e posterior). O CLR chama os métodos nessa interface para notificar o criador de perfil de eventos no processo de criação de perfil. O criador de perfil pode retornar a chamada em tempo de execução usando os métodos de [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) e [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interfaces para obter informações sobre o estado do aplicativo analisado.  
  
> [!NOTE]
>  Somente a parte da coleta de dados da solução do criador de perfil deve estar em execução no mesmo processo que o aplicativo analisado. Todas as análises de dados e interface do usuário devem ser executada em um processo separado.  
  
 A ilustração a seguir mostra como a DLL do criador de perfil interage com o aplicativo que está sendo analisado e o CLR.  
  
 ![Captura de tela que mostra a arquitetura de criação de perfil.](./media/profiling-overview/profiling-architecture.png)  
  
### <a name="the-notification-interfaces"></a>As Interfaces de notificação  
 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) e [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) podem ser consideradas interfaces de notificação. Essas interfaces consistem em métodos como [ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md), [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md), e [JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md). Cada vez que o CLR carrega ou descarrega uma classe, compila uma função, e assim por diante, ele chama o método correspondente no criador de perfil `ICorProfilerCallback` ou `ICorProfilerCallback2` interface.  
  
 Por exemplo, um criador de perfis pode medir o desempenho de código por meio de duas funções de notificação: [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) e [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md). Ele só carimbos de data / hora cada notificação, acumula resultados e gera uma lista que indica quais funções consumiram mais tempo da CPU ou relógio durante a execução do aplicativo.  
  
### <a name="the-information-retrieval-interfaces"></a>As Interfaces de recuperação de informações  
 As outras principais interfaces envolvidas na criação de perfil são [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) e [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md). O criador de perfis chama essas interfaces conforme necessário para obter mais informações para ajudar a sua análise. Por exemplo, sempre que o CLR chama o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) função, ele fornece um identificador de função. O criador de perfil pode obter mais informações sobre essa função chamando o [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) método para descobrir a classe pai da função, seu nome e assim por diante.  
  
 [Voltar ao início](#top)  
  
<a name="support"></a>   
## <a name="supported-features"></a>Recursos compatíveis  
 A API de criação de perfil fornece informações sobre uma variedade de eventos e ações que ocorrem no common language runtime. Você pode usar essas informações para monitorar o funcionamento interno dos processos e analisar o desempenho de seu aplicativo .NET Framework.  
  
 A API de criação de perfil recupera informações sobre as seguintes ações e eventos que ocorrem no CLR:  
  
-   Eventos de inicialização e desligamento do CLR.  
  
-   Aplicativo desligamento e criação eventos de domínio.  
  
-   Assembly de carregamento e descarregamento de eventos.  
  
-   Módulo de carregamento e descarregamento de eventos.  
  
-   Vtable criação e destruição eventos COM.  
  
-   Just-in-time (JIT) compilação e lançamento de eventos.  
  
-   Eventos de carregamento e descarregamento de classe.  
  
-   Eventos de criação e destruição de threads.  
  
-   Eventos de entrada e saída da função.  
  
-   Exceções.  
  
-   Faz a transição entre a execução de código gerenciado e não gerenciado.  
  
-   Faz a transição entre contextos de tempo de execução diferente.  
  
-   Informações sobre suspensões de tempo de execução.  
  
-   Informações sobre a atividade de coleta de tempo de execução memória heap e o lixo.  
  
 A API de criação de perfil pode ser chamada por qualquer linguagem de compatível COM (não gerenciados).  
  
 A API é eficiente em relação ao consumo de CPU e memória. Criação de perfil não envolve mudanças no aplicativo de criação de perfil que são significativas o suficiente para causar resultados falsos.  
  
 A API de criação de perfil é útil para criadores de perfis de amostragem e não amostragem. Um *criador de perfil de amostragem* inspeciona o perfil em marcações normais de relógio, digamos, em 5 milissegundos separados. Um *criador de perfil de amostragem não* é informado de um evento síncrono com o thread que faz com que o evento.  
  
### <a name="unsupported-functionality"></a>Funcionalidade sem suporte  
 A API de criação de perfil não oferece suporte a seguinte funcionalidade:  
  
-   Código não gerenciado, que deve ser o perfil criado usando os métodos Win32 convencionais. No entanto, o criador de perfil CLR inclui eventos de transição para determinar os limites entre código gerenciado e.  
  
-   Aplicativos automodificáveis que alteram seus próprios códigos para fins como programação orientada a aspecto.  
  
-   Limita a verificação, pois a API de criação de perfil não fornece essas informações. O CLR fornece suporte intrínseco para verificar os limites de todo o código gerenciado.  
  
-   Criação de perfil remota, que não é suportada pelos seguintes motivos:  
  
    -   Criação de perfil remota estende o tempo de execução. Quando você usa as interfaces de criação de perfil, você deve minimizar o tempo de execução para que os resultados de criação de perfil será não sejam afetada indevidamente. Isso é especialmente verdadeiro quando o desempenho de execução está sendo monitorado. No entanto, criação de perfil remota não é uma limitação quando as interfaces de criação de perfil são usadas para monitorar o uso de memória ou para obter informações de tempo de execução sobre quadros de pilha, objetos e assim por diante.  
  
    -   O criador de perfil de código do CLR deve registrar uma ou mais interfaces de retorno de chamada com o tempo de execução no computador local que está executando o aplicativo perfilado. Isso limita a capacidade de criar um criador de perfil remota de código.  
  
-   Criação de perfil em ambientes de produção com requisitos de alta disponibilidade. A API de criação de perfil foi criada para dar suporte a diagnóstico de tempo de desenvolvimento. Ele não passou por testes rigorosos necessários para dar suporte a ambientes de produção.  
  
 [Voltar ao início](#top)  
  
<a name="notification_threads"></a>   
## <a name="notification-threads"></a>Threads de notificação  
 Na maioria dos casos, o thread que gera um evento também executa notificações. Essas notificações (por exemplo, [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) e [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)) não é necessário fornecer o explícita `ThreadID`. Além disso, o criador de perfis pode decidir usar o armazenamento local de thread para armazenar e atualizar os blocos de análise em vez de indexar os blocos de análise de armazenamento global, com base no `ThreadID` do thread afetado.  
  
 Observe que esses retornos de chamada não são serializados. Os usuários devem proteger seu código criando estruturas de dados de thread-safe e bloqueando o código do criador de perfil, quando necessário para evitar acesso paralelo de vários threads. Portanto, em alguns casos, você pode receber uma sequência incomum de retornos de chamada. Por exemplo, suponha que um aplicativo gerenciado esteja reproduzindo dois segmentos que estão executando códigos idênticos. Nesse caso, é possível receber um [ICorProfilerCallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) eventos para qualquer função de um thread e uma `FunctionEnter` o retorno de chamada de outro segmento antes de receber o [ ICorProfilerCallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) retorno de chamada. Nesse caso, o usuário receberá um `FunctionEnter` retorno de chamada para uma função que pode não ter sido totalmente just-in-time (JIT) compilado ainda.  
  
 [Voltar ao início](#top)  
  
<a name="security"></a>   
## <a name="security"></a>Segurança  
 Um criador de perfil a DLL é uma DLL não gerenciada que é executado como parte do mecanismo de execução de tempo de execução do linguagem comum. Como resultado, o código na DLL não está sujeita às restrições do criador de perfil gerenciado segurança de acesso do código. As únicas limitações no criador de perfil DLL são aquelas impostas pelo sistema operacional no usuário que está executando o aplicativo com perfil.  
  
 Os autores do Profiler devem tomar precauções apropriadas para evitar problemas relacionados à segurança. Por exemplo, durante a instalação, uma DLL do criador de perfil deve ser adicionado a uma lista de controle de acesso (ACL) para que um usuário mal-intencionado não poderá ser modificado.  
  
 [Voltar ao início](#top)  
  
<a name="combining_managed_unmanaged"></a>   
## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Combinar o código gerenciado e em um código Profiler  
 Um criador de perfis gravado incorretamente pode causar referências circulares a mesmo, resultando em comportamento imprevisível.  
  
 Uma revisão de API de criação de perfil CLR pode criar a impressão de que você pode escrever um criador de perfil que contém os componentes gerenciados e não gerenciados que chamam uns aos outros por meio de chamadas de interoperabilidade ou indiretas COM.  
  
 Embora isso seja possível de uma perspectiva de design, a API de criação de perfil não suporta componentes gerenciados. Um criador de perfil do CLR deve ser completamente gerenciado. Tentativas de combinar código gerenciado e não gerenciado em um criador de perfil do CLR podem causar violações de acesso, falha do programa ou deadlocks. Os componentes gerenciados do criador de perfis acionarão eventos de volta aos seus componentes não gerenciados, que subsequentemente chamam os componentes gerenciados novamente, resultando em referências circulares.  
  
 É o único local onde um criador de perfil do CLR pode chamar código gerenciado com segurança no corpo Microsoft intermediate language (MSIL) de um método. A prática recomendada para modificar o corpo do MSIL é usar os métodos de recompilação JIT na [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.  
  
 Também é possível usar os métodos mais antigos de instrumentação para alterar o MSIL. Antes que a compilação just-in-time (JIT) de uma função é concluída, o criador de perfis poderá inserir chamadas gerenciadas no corpo do MSIL de um método e JIT-compilá-lo (consulte a [ICorProfilerInfo:: Getilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md) método). Essa técnica pode ser usada com êxito para instrumentação seletiva de código gerenciado ou para reunir dados de desempenho e estatísticas sobre o JIT.  
  
 Como alternativa, um criador de perfil de código pode inserir ganchos nativos no corpo do MSIL de cada função que chama código não gerenciado. Essa técnica pode ser usada para instrumentação e cobertura. Por exemplo, um criador de perfil de código pode inserir ganchos de instrumentação após cada bloco de MSIL para garantir que o bloco foi executado. A modificação do corpo do MSIL de um método é uma operação bastante delicada e há muitos fatores que devem ser levados em consideração.  
  
 [Voltar ao início](#top)  
  
<a name="unmanaged"></a>   
## <a name="profiling-unmanaged-code"></a>Criação de perfil de código não gerenciado  
 O common language runtime (CLR) API de criação de perfil fornece suporte mínimo para a criação de perfil de código não gerenciado. A seguinte funcionalidade é fornecida:  
  
-   Enumeração de cadeias de pilha. Esse recurso permite que um criador de perfil de código determinar o limite entre código gerenciado e código não gerenciado.  
  
-   Determinação se uma cadeia de pilha corresponde ao código gerenciado ou código nativo.  
  
 Nas versões do .NET Framework 1.0 e 1.1, esses métodos estão disponíveis por meio do subconjunto em processo de API de depuração CLR. Eles são definidos no arquivo Cordebug IDL.  
  
 No .NET Framework 2.0 e posterior, você pode usar o [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método para essa funcionalidade.  
  
 [Voltar ao início](#top)  
  
<a name="com"></a>   
## <a name="using-com"></a>Usando COM  
 Embora as interfaces de criação de perfil são definidas como interfaces COM, o common language runtime (CLR) não inicializa, na verdade, COM para usar essas interfaces. O motivo é evitar ter que definir o modelo de threading usando o [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) funcionar antes que o aplicativo gerenciado tenha tido a oportunidade de especificar seu modelo de threading desejado. Da mesma forma, o criador de perfil em si não deve chamar `CoInitialize`, pois ela pode escolher um modelo de threading é incompatível com o aplicativo que está sendo analisado e pode causar falha no aplicativo.  
  
 [Voltar ao início](#top)  
  
<a name="call_stacks"></a>   
## <a name="call-stacks"></a>Pilhas de chamadas  
 A API de criação de perfil fornece duas maneiras de obter pilhas de chamadas: um método de instantâneo de pilha, que permite coleta esparsa de pilhas de chamadas, e um método de pilha de sombra, que rastreia a pilha de chamadas a cada instante.  
  
### <a name="stack-snapshot"></a>Instantâneo de pilha  
 Um instantâneo de pilha é um rastreamento de pilha de um thread em um momento no tempo. A API de criação de perfil oferece suporte o rastreamento de funções gerenciadas na pilha, mas deixa o rastreamento de funções não gerenciadas para o caminhador de pilha do profiler.  
  
 Para obter mais informações sobre como programar o criador de perfil para movimentar pilhas gerenciadas, consulte o [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) método neste conjunto de documentação, e [movimentação de pilhas do Profiler no .NET Framework 2.0: Noções básicas e além](https://go.microsoft.com/fwlink/?LinkId=73638).
  
### <a name="shadow-stack"></a>Pilha de sombra  
 Usando o método de instantâneo com muita frequência pode criar rapidamente um problema de desempenho. Se você quiser fazer rastreamentos de pilha com frequência, seu criador de perfil em vez disso, deve criar uma pilha de sombra usando o [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md), e [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) retornos de chamada de exceção. A pilha de sombra está sempre atualizada e pode ser copiada rapidamente para o armazenamento sempre que um instantâneo de pilha é necessário.  
  
 Uma pilha de sombra pode obter informações sobre instanciações genéricas, valores de retorno e argumentos de função. Essa informação está disponível somente por meio da pilha de sombra e pode ser obtida quando o controle é passado para uma função. No entanto, essas informações não estejam disponíveis posteriormente durante a execução da função.  
  
 [Voltar ao início](#top)  
  
<a name="callbacks"></a>   
## <a name="callbacks-and-stack-depth"></a>Retornos de chamada e profundidade da pilha  
 Retornos de chamada do Profiler podem ser emitidos em circunstâncias muito restritas a pilha e um estouro de pilha em um retorno de chamada do criador de perfil nos leva a uma saída imediata do processo. Um criador de perfil assegure-se usar como pouca possível de pilha em resposta a retornos de chamada. Se o criador de perfil se destina para uso com os processos que são robustos em um estouro de pilha, o próprio criador de perfis deverá evitar acionar o estouro de pilha.  
  
 [Voltar ao início](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Configurando um ambiente de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|Explica como inicializar um criador de perfil, defina as notificações de eventos e analisar um serviço do Windows.|  
|[Interfaces de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|Descreve as interfaces não gerenciadas que usa a API de criação de perfil.|  
|[Criando perfil de funções estáticas globais](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|Descreve as funções estáticas globais não gerenciadas que usa a API de criação de perfil.|  
|[Criando perfil de enumerações](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|Descreve as enumerações não gerenciadas que usa a API de criação de perfil.|  
|[Estruturas de criação de perfil](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|Descreve as estruturas não gerenciadas que usa a API de criação de perfil.|
