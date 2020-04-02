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
ms.openlocfilehash: 3836b562d969726a6587d702d3edf45abb147d10
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588501"
---
# <a name="profiling-overview"></a>Visão geral da criação de perfil

Um profiler é uma ferramenta que monitora a execução de outro aplicativo. Um profiler de tempo de execução de idioma comum (CLR) é uma biblioteca de links dinâmicos (DLL) que consiste em funções que recebem mensagens e enviam mensagens para a CLR usando a API de criação de perfil. O profiler DLL é carregado pela CLR em tempo de execução.

As ferramentas tradicionais de criação de perfil se concentram em medir a execução do aplicativo. Ou seja, eles medem o tempo que é gasto em cada função ou o uso da memória do aplicativo ao longo do tempo. A API de criação de perfil tem como alvo uma classe mais ampla de ferramentas de diagnóstico, como utilitários de cobertura de código e até mesmo auxiliares avançados de depuração. Esses usos são todos de diagnóstico por natureza. A API de perfil não só mede, mas também monitora a execução de um aplicativo. Por essa razão, a API de criação de perfil nunca deve ser usada pelo próprio aplicativo, e a execução do aplicativo não deve depender (ou ser afetada) pelo profiler.

A criação de perfil de um aplicativo CLR requer mais suporte do que o perfil de código da máquina compilado convencionalmente. Isso ocorre porque a CLR introduz conceitos como domínios de aplicativos, coleta de lixo, manipulação gerenciada de exceções, compilação de código just-in-time (JIT) (conversão de linguagem intermediária da Microsoft, ou MSIL, código em código de máquina nativa) e recursos semelhantes. Os mecanismos convencionais de criação de perfil não podem identificar ou fornecer informações úteis sobre esses recursos. A API de criação de perfil fornece essas informações ausentes de forma eficiente, com efeito mínimo sobre o desempenho da CLR e da aplicação perfilada.

A compilação JIT em tempo de execução oferece boas oportunidades para a criação de perfil. A API de criação de perfil permite que um profiler altere o fluxo de código MSIL na memória para uma rotina antes de ser compilado pelo JIT. Dessa forma, o profiler pode adicionar dinamicamente código de instrumentação a rotinas específicas que precisam de uma investigação mais profunda. Embora essa abordagem seja possível em cenários convencionais, é muito mais fácil de implementar para a CLR usando a API de perfil.

## <a name="the-profiling-api"></a>A API de criação de perfil

Normalmente, a API de criação de perfil é usada para escrever um *profiler de código*, que é um programa que monitora a execução de um aplicativo gerenciado.

A API de criação de perfil é usada por um profiler DLL, que é carregado no mesmo processo que o aplicativo que está sendo perfilado. O profiler DLL implementa uma interface de retorno de chamada ([ICorProfilerCallback](icorprofilercallback-interface.md) na versão .NET Framework versão 1.0 e 1.1, [ICorProfilerCallback2](icorprofilercallback2-interface.md) na versão 2.0 e posterior). O CLR chama os métodos nessa interface para notificar o profiler de eventos no processo perfilado. O profiler pode ligar de volta para o tempo de execução usando os métodos nas interfaces [ICorProfilerInfo](icorprofilerinfo-interface.md) e [ICorProfilerInfo2](icorprofilerinfo2-interface.md) para obter informações sobre o estado do aplicativo perfilado.

> [!NOTE]
> Apenas a parte de coleta de dados da solução profiler deve estar sendo realizada no mesmo processo que o aplicativo perfilado. Toda interface de usuário e análise de dados devem ser realizadas em um processo separado.

A ilustração a seguir mostra como o profiler DLL interage com o aplicativo que está sendo perfilado e com o CLR.

![Captura de tela que mostra a arquitetura de criação de perfil.](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>As interfaces de notificação

[ICorProfilerCallback](icorprofilercallback-interface.md) e [ICorProfilerCallback2](icorprofilercallback2-interface.md) podem ser considerados interfaces de notificação. Essas interfaces consistem em métodos como [ClassLoadStarted,](icorprofilercallback-classloadstarted-method.md) [ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)e [JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md). Cada vez que o CLR carrega ou descarrega uma classe, compila uma função e, assim `ICorProfilerCallback` por `ICorProfilerCallback2` diante, ele chama o método correspondente no profiler ou interface.

Por exemplo, um profiler poderia medir o desempenho do código através de duas funções de notificação: [FunctionEnter2](functionenter2-function.md) e [FunctionLeave2](functionleave2-function.md). Ele apenas carimba cada notificação, acumula resultados e produz uma lista que indica quais funções consumiram mais cpu ou tempo de relógio de parede durante a execução do aplicativo.

### <a name="the-information-retrieval-interfaces"></a>As interfaces de recuperação de informações

As outras interfaces principais envolvidas na criação de perfil são [ICorProfilerInfo](icorprofilerinfo-interface.md) e [ICorProfilerInfo2](icorprofilerinfo2-interface.md). O profiler chama essas interfaces conforme necessário para obter mais informações para ajudar na sua análise. Por exemplo, sempre que o CLR chama a função [FunctionEnter2,](functionenter2-function.md) ele fornece um identificador de função. O profiler pode obter mais informações sobre essa função ligando para o método [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) para descobrir a classe pai da função, seu nome e assim por diante.

## <a name="supported-features"></a>Recursos com suporte

A API de criação de perfil fornece informações sobre uma variedade de eventos e ações que ocorrem no tempo de execução da linguagem comum. Você pode usar essas informações para monitorar o funcionamento interno dos processos e analisar o desempenho do seu aplicativo .NET Framework.

A API de criação de perfil recupera informações sobre as seguintes ações e eventos que ocorrem na CLR:

- Eventos de startup e desligamento da CLR.

- Criação de domínio de aplicativos e eventos de desligamento.

- Eventos de carga e descarga de montagem.

- Eventos de carga e descarga de módulos.

- Com vtable eventos de criação e destruição.

- Eventos de compilação e lançamento de códigos just-in-time (JIT).

- Eventos de carga e descarga de classe.

- Eventos de criação e destruição de linhas.

- Eventos de entrada e saída de função.

- Exceções.

- Transições entre execução de código gerenciada e não gerenciada.

- Transições entre diferentes contextos de tempo de execução.

- Informações sobre suspensões de tempo de execução.

- Informações sobre o monte de memória em tempo de execução e atividade de coleta de lixo.

A API de criação de perfil pode ser chamada de qualquer linguagem compatível com COM (não gerenciada).

A API é eficiente no que diz respeito ao consumo de CPU e memória. O perfil não envolve alterações no aplicativo perfilado que são significativas o suficiente para causar resultados enganosos.

A API de perfil é útil tanto para perfis de amostragem quanto de não amostragem. Um *profiler amostral* inspeciona o perfil em carrapatos de relógio regulares, digamos, a 5 milissegundos de diferença. Um *profiler sem amostragem* é informado de um evento sincronizadamente com o segmento que causa o evento.

### <a name="unsupported-functionality"></a>Funcionalidade sem-suporte

A API de criação de perfil não suporta a seguinte funcionalidade:

- Código não gerenciado, que deve ser perfilado usando métodos Win32 convencionais. No entanto, o profiler CLR inclui eventos de transição para determinar os limites entre código gerenciado e não gerenciado.

- Aplicativos auto-modificadores que modificam seu próprio código para fins como programação orientada a aspectos.

- A verificação de limites, porque a API de perfil não fornece essas informações. O CLR fornece suporte intrínseco para verificação de limites de todo o código gerenciado.

- Perfil remoto, que não é suportado pelas seguintes razões:

  - O perfil remoto amplia o tempo de execução. Ao usar as interfaces de criação de perfil, você deve minimizar o tempo de execução para que os resultados de criação de perfil não sejam afetados indevidamente. Isso é especialmente verdade quando o desempenho da execução está sendo monitorado. No entanto, o perfil remoto não é uma limitação quando as interfaces de criação de perfil são usadas para monitorar o uso da memória ou para obter informações em tempo de execução sobre quadros de pilha, objetos e assim por diante.

  - O perfil de código CLR deve registrar uma ou mais interfaces de retorno de chamada com o tempo de execução no computador local no qual o aplicativo perfilado está sendo executado. Isso limita a capacidade de criar um profiler de código remoto.

## <a name="notification-threads"></a>Segmentos de notificação

Na maioria dos casos, o segmento que gera um evento também executa notificações. Essas notificações (por exemplo, [FunctionEnter](functionenter-function.md) e [FunctionLeave)](functionleave-function.md)não precisam fornecer o explícito `ThreadID`. Além disso, o profiler pode decidir usar o armazenamento local de thread para armazenar e atualizar `ThreadID` seus blocos de análise em vez de indexar os blocos de análise no armazenamento global, com base no segmento afetado.

Observe que esses retornos não são serializados. Os usuários devem proteger seu código criando estruturas de dados seguras para segmentos e bloqueando o código do profiler quando necessário para impedir o acesso paralelo de vários segmentos. Portanto, em certos casos você pode receber uma seqüência incomum de retornos. Por exemplo, suponha que um aplicativo gerenciado esteja gerando dois threads que estão executando código idêntico. Neste caso, é possível receber um [evento ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) para alguma `FunctionEnter` função de um segmento e um retorno de chamada do outro segmento antes de receber o retorno de chamada [ICorProfilerCallback::JITCompilaçãoConcluída.](icorprofilercallback-jitcompilationfinished-method.md) Neste caso, o usuário `FunctionEnter` receberá um retorno de chamada para uma função que pode não ter sido totalmente just-in-time (JIT) compilada ainda.

## <a name="security"></a>Segurança

Um DLL de perfil é um DLL não gerenciado que funciona como parte do mecanismo de execução em tempo de execução em tempo de execução comum. Como resultado, o código no profiler DLL não está sujeito às restrições de segurança de acesso de código gerenciada. As únicas limitações no dLL do profiler são as impostas pelo sistema operacional ao usuário que está executando o aplicativo perfilado.

Os autores de profiler devem tomar as precauções apropriadas para evitar problemas relacionados à segurança. Por exemplo, durante a instalação, um DLL do profiler deve ser adicionado a uma lista de controle de acesso (ACL) para que um usuário mal-intencionado não possa modificá-la.

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>Combinando código gerenciado e não gerenciado em um profiler de código

Um profiler escrito incorretamente pode causar referências circulares a si mesmo, resultando em comportamento imprevisível.

Uma revisão da API de criação de perfil CLR pode criar a impressão de que você pode escrever um profiler que contenha componentes gerenciados e não gerenciados que se chamem através de interop COM ou chamadas indiretas.

Embora isso seja possível do ponto de vista do design, a API de criação de perfil não suporta componentes gerenciados. Um profiler CLR deve ser completamente desgerenciado. Tentativas de combinar código gerenciado e não gerenciado em um profiler CLR podem causar violações de acesso, falha de programa ou impasses. Os componentes gerenciados do profiler dispararão eventos de volta aos seus componentes não gerenciados, o que posteriormente chamará os componentes gerenciados novamente, resultando em referências circulares.

O único local onde um profiler CLR pode chamar código gerenciado com segurança é no corpo de linguagem intermediária da Microsoft (MSIL) de um método. A prática recomendada para modificar o corpo MSIL é usar os métodos de recompilação JIT na interface [ICorProfilerCallback4.](icorprofilercallback4-interface.md)

Também é possível usar os métodos de instrumentação mais antigos para modificar o MSIL. Antes que a compilação de just-in-time (JIT) de uma função seja concluída, o profiler pode inserir chamadas gerenciadas no corpo MSIL de um método e, em seguida, compilá-lo (consulte o método [ICorProfilerInfo::GetILFunctionBody).](icorprofilerinfo-getilfunctionbody-method.md) Esta técnica pode ser usada com sucesso para instrumentação seletiva de código gerenciado, ou para coletar estatísticas e dados de desempenho sobre o JIT.

Alternativamente, um profiler de código pode inserir ganchos nativos no corpo MSIL de cada função gerenciada que chama em código não gerenciado. Esta técnica pode ser utilizada para instrumentação e cobertura. Por exemplo, um profiler de código poderia inserir ganchos de instrumentação após cada bloco MSIL para garantir que o bloco foi executado. A modificação do corpo MSIL de um método é uma operação muito delicada, e há muitos fatores que devem ser levados em consideração.

## <a name="profiling-unmanaged-code"></a>Código não gerenciado de perfil

A API de criação de perfil de tempo de execução de idioma comum (CLR) fornece suporte mínimo para a criação de perfil de código não gerenciado. As seguintes funcionalidades são fornecidas:

- Enumeração de cadeias de pilhas. Esse recurso permite que um profiler de código determine o limite entre código gerenciado e código não gerenciado.

- Determinar se uma cadeia de pilha corresponde ao código gerenciado ou ao código nativo.

Nas versões .NET Framework 1.0 e 1.1, esses métodos estão disponíveis através do subconjunto em processo da API de depuração CLR. Eles são definidos no arquivo CorDebug.idl.

No .NET Framework 2.0 e posterior, você pode usar o método [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) para essa funcionalidade.

## <a name="using-com"></a>Usando com

Embora as interfaces de criação de perfil sejam definidas como interfaces COM, o tempo de execução de linguagem comum (CLR) não inicializa o COM para usar essas interfaces. A razão é evitar ter que definir o modelo de rosca usando a função [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize) antes que o aplicativo gerenciado tenha a chance de especificar seu modelo de rosca desejado. Da mesma forma, o profiler em si não deve chamar, `CoInitialize`porque ele pode escolher um modelo de threading que seja incompatível com o perfil do aplicativo e pode fazer com que o aplicativo falhe.

## <a name="call-stacks"></a>Pilhas de Chamadas

A API de criação de perfil fornece duas maneiras de obter pilhas de chamadas: um método de snapshot de pilha, que permite a coleta esparsa de pilhas de chamadas, e um método de pilha de sombras, que rastreia a pilha de chamadas a cada instante.

### <a name="stack-snapshot"></a>Instantâneo de pilha

Um instantâneo de pilha é um traço da pilha de um fio em um instante no tempo. A API de criação de perfil suporta o rastreamento de funções gerenciadas na pilha, mas deixa o rastreamento de funções não gerenciadas para o próprio andador de pilha do profiler.

Para obter mais informações sobre como programar o profiler para andar em pilhas gerenciadas, consulte o método [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) neste conjunto de documentação e [o Profiler Stack Walking no .NET Framework 2.0: Basics and Beyond](https://docs.microsoft.com/previous-versions/dotnet/articles/bb264782(v=msdn.10)).

### <a name="shadow-stack"></a>Shadow Stack

Usar o método snapshot com muita freqüência pode criar rapidamente um problema de desempenho. Se você quiser fazer rastreamentos de pilha com freqüência, o profiler deve, em vez disso, construir uma pilha de sombras usando os retornos de exceção [FunctionEnter2,](functionenter2-function.md) [FunctionLeave2,](functionleave2-function.md) [FunctionTailcall2](functiontailcall2-function.md)e [ICorProfilerCallback2.](icorprofilercallback2-interface.md) A pilha de sombras está sempre atual e pode ser rapidamente copiada para armazenamento sempre que um instantâneo de pilha for necessário.

Uma pilha de sombras pode obter argumentos de função, valores de retorno e informações sobre instanciações genéricas. Essas informações estão disponíveis apenas através da pilha de sombras e podem ser obtidas quando o controle é entregue a uma função. No entanto, essas informações podem não estar disponíveis mais tarde durante o execução da função.

## <a name="callbacks-and-stack-depth"></a>Retornos de chamada e profundidade de pilha

Os retornos de chamadas do profiler podem ser emitidos em circunstâncias muito restritas à pilha, e um estouro de pilha em um retorno de chamada do profiler levará a uma saída imediata do processo. Um profiler deve ter certeza de usar o mínimo de pilha possível em resposta a retornos de chamadas. Se o profiler for destinado a ser usado contra processos robustos contra o estouro da pilha, o próprio profiler também deve evitar desencadear o estouro da pilha.

## <a name="related-topics"></a>Tópicos Relacionados

|Title|Descrição|
|-----------|-----------------|
|[Configurando um ambiente de criação de perfil](setting-up-a-profiling-environment.md)|Explica como inicializar um profiler, definir notificações de eventos e traçar o perfil de um Serviço windows.|
|[Criação de perfil de interfaces](profiling-interfaces.md)|Descreve as interfaces não gerenciadas que a API de criação de perfil usa.|
|[Criando perfil de funções estáticas globais](profiling-global-static-functions.md)|Descreve as funções estáticas globais não gerenciadas que a API de criação de perfil usa.|
|[Criando perfil de enumerações](profiling-enumerations.md)|Descreve as enumerações não gerenciadas que a API de perfil usa.|
|[Estruturas de criação de perfil](profiling-structures.md)|Descreve as estruturas não gerenciadas que a API de perfil usa.|
