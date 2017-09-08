---
title: Desempenho do .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance [.NET Framework]
- reliability [.NET Framework]
ms.assetid: c1676cca-3f1a-41ec-b469-9029566074fc
caps.latest.revision: 20
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1d1e1de5637dbb955dd72ed0291da1f4f537ce28
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="net-framework-performance"></a>Desempenho do .NET Framework
Se você deseja criar aplicativos com ótimo desempenho, projete e planeje o desempenho da mesma forma como projetaria qualquer outro recurso do aplicativo. É possível usar as ferramentas fornecidas pela Microsoft para medir o desempenho do aplicativo e, se necessário, fazer melhorias no uso da memória, na produtividade de código e na capacidade de resposta. Este tópico lista as ferramentas de análise de desempenho que a Microsoft fornece, além de fornecer links a outros tópicos que abordam o desempenho em áreas específicas do desenvolvimento de aplicativo.  
  
## <a name="designing-and-planning-for-performance"></a>Projetando e planejando o desempenho  
 Se desejar um aplicativo de ótimo desempenho, projete o desempenho no aplicativo como projetaria qualquer outro recurso. Você deve determinar os cenários críticos para o desempenho do aplicativo, definir as metas de desempenho e medir o desempenho desses cenários de aplicativo cedo e com frequência. Como cada aplicativo é diferente e possui caminhos distintos de execução críticos para o desempenho, determinar esses caminhos cedo e focar os esforços permitem maximizar a produtividade.  
  
 Não é preciso estar totalmente familiarizado com a plataforma de destino para criar um aplicativo de alto desempenho. Porém, você deve desenvolver um entendimento de que partes da plataforma de destino são dispendiosas em termos de desempenho. É possível fazer isso medindo o desempenho cedo no processo de desenvolvimento.  
  
 Para determinar as áreas cruciais do desempenho e estabelecer as metas de desempenho, sempre considere a experiência do usuário. Tempo de inicialização e capacidade de resposta são duas áreas cruciais que afetarão a percepção do usuário do seu aplicativo. Se o aplicativo usar muita memória, ele pode parecer lento para o usuário ou afetar outros aplicativos que executam no sistema ou, em alguns casos, ser reprovado no processo de envio da Windows Store ou Windows Phone Store. Além disso, se você determinar quais partes do código são mais executadas, é possível garantir que elas sejam bem otimizadas.  
  
## <a name="analyzing-performance"></a>Analisando desempenho  
 Como parte do plano de desenvolvimento geral, defina os pontos durante o desenvolvimento em que você medirá o desempenho do aplicativo e comparará os resultados com as metas definidas anteriormente. Meça seu aplicativo no ambiente e no hardware que você espera que os usuários tenham. Analisando o desempenho do aplicativo cedo e com frequência, é possível alterar decisões de arquitetura que seriam caras e dispendiosas para corrigir mais tarde no ciclo de desenvolvimento. As seções a seguir descrevem as ferramentas de desempenho que você pode usar para analisar seus aplicativos e discutir o acompanhamento de eventos usado por essas ferramentas.  
  
### <a name="performance-tools"></a>Ferramentas de desempenho  
 Seguem algumas das ferramentas de desempenho que você pode usar com os aplicativos .NET Framework.  
  
|Ferramenta|Descrição|  
|----------|-----------------|  
|Análise de desempenho do Visual Studio|Use para analisar o uso de CPU dos aplicativos .NET Framework, que serão implantados em computadores que executam o sistema operacional Windows.<br /><br /> Essa ferramenta está disponível do menu **Depurar** no Visual Studio depois de você abrir um projeto. Para obter mais informações, consulte [Gerenciador de Desempenho](/visualstudio/profiling/performance-explorer). **Observação:** use a Análise de Aplicativo do Windows Phone (veja a próxima linha) ao focar um Windows Phone.|  
|Análise de Aplicativo do Windows Phone|Use para analisar a CPU e a memória, a taxa de transferência de dados de rede, a capacidade de resposta do aplicativo e o consumo de bateria nos aplicativos do Windows Phone.<br /><br /> Essa ferramenta está disponível do menu **Depurar** para um projeto do Windows Phone no Visual Studio depois de você instalar o [SDK do Windows Phone](http://go.microsoft.com/fwlink/?LinkId=265773). Para obter mais informações, consulte [Criação de perfil de aplicativo para Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/jj215908\(v=vs.105\).aspx).|  
|[PerfView](http://www.microsoft.com/download/details.aspx?id=28567)|Use para identificar problemas de desempenho relacionados a CPU e memória. Essa ferramenta usa APIs de criação de perfil Rastreamento de Eventos para Windows (ETW) e CLR para fornecer investigações avançadas de memória e CPU, além de informações sobre coleta de lixo e compilação JIT. Para obter mais informações sobre como usar o PerfView, consulte os arquivos de ajuda e o tutorial que estão incluídos com o aplicativo, os [tutoriais em vídeo do Channel 9](http://channel9.msdn.com/Series/PerfView-Tutorial) e as [postagens de blog](http://blogs.msdn.com/b/vancem/archive/tags/perfview/).<br /><br /> Para problemas específicos de memória, consulte [Usando PerfView para investigações de memória](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-9-NET-Memory-Investigation-Basics-of-GC-Heap-Snapshots).|  
|[Windows Performance Analyzer](http://www.microsoft.com/download/details.aspx?id=30652)|Use para determinar o desempenho geral do sistema, como uso de memória e armazenamento do aplicativo quando vários aplicativos estão em execução no mesmo computador. Essa ferramenta está disponível do centro de download como parte do ADK (Kit de Avaliação e Implantação) do Windows para [!INCLUDE[win8](../../../includes/win8-md.md)]. Para obter mais informações, consulte [Windows Performance Analyzer](http://msdn.microsoft.com/library/windows/desktop/hh448170.aspx).|  
  
### <a name="event-tracing-for-windows-etw"></a>ETW (Rastreamento de Eventos para Windows)  
 O ETW é uma técnica que permite obter informações de diagnóstico sobre o código em execução e é essencial para muitas das ferramentas de desempenho já mencionadas. O ETW cria logs quando eventos em particular são lançados pelos aplicativos .NET Framework e o Windows. Com o ETW, é possível habilitar e desabilitar o registro em log dinamicamente, de modo que você possa realizar acompanhamento detalhado em um ambiente de produção sem reiniciar o aplicativo. O .NET Framework oferece suporte a eventos do ETW, e o ETW é usado por muitas ferramentas de definição de perfil e desempenho para gerar dados de desempenho. Essas ferramentas habilitam e desabilitam com frequência eventos do ETW, então é útil ficar familiarizado com elas. É possível usar eventos específicos do ETW para coletar informações de desempenho sobre componentes especiais do seu aplicativo. Para obter mais informações sobre o suporte ETW no .NET Framework, consulte [Eventos ETW no Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md) e [Eventos ETW na biblioteca de tarefas paralelas e em PLINQ](../../../docs/framework/performance/etw-events-in-task-parallel-library-and-plinq.md).  
  
## <a name="performance-by-app-type"></a>Desempenho por tipo de aplicativo  
 Cada tipo de aplicativo .NET Framework tem as próprias melhores práticas, considerações e ferramentas para avaliar o desempenho. A tabela a seguir está vinculada a tópicos de desempenho para tipos de aplicativo .NET Framework específicos.  
  
|Tipo de aplicativo|Consulte |  
|--------------|---------|  
|Aplicativos .NET Framework para todas as plataformas|[Coleta de lixo e desempenho](../../../docs/standard/garbage-collection/performance.md)<br /><br /> [Dicas de desempenho](../../../docs/framework/performance/performance-tips.md)|  
|Aplicativos [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] gravados em C++, C# e Visual Basic|[Práticas recomendadas de desempenho para Aplicativos da Windows Store usando C++, C# e Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)|  
|Windows Phone|[Considerações sobre desempenho de aplicativo para Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/ff967560\(v=vs.105\).aspx)<br /><br /> [Análise de Aplicativo do Windows Phone](http://msdn.microsoft.com/library/windowsphone/develop/hh202934\(v=vs.105\).aspx)<br /><br /> [Coloque seus aplicativos para Windows Phone no Marketplace com mais rapidez](http://msdn.microsoft.com/magazine/hh781024.aspx)|  
|Windows Presentation Foundation (WPF)|[Pacote de desempenho WPF](http://msdn.microsoft.com/library/67cafaad-57ad-4ecb-9c08-57fac144393e)|  
|Silverlight|[Dicas de desempenho](http://msdn.microsoft.com/library/cc189071\(v=vs.95\).aspx)|  
|ASP.NET|[Visão geral do desempenho do ASP.NET](http://msdn.microsoft.com/library/f882bf1b-a009-4312-ac06-74370ffabc0b)|  
|Windows Forms|[Dicas práticas para aumentar o desempenho de aplicativos do Windows Forms](http://msdn.microsoft.com/magazine/cc163630.aspx)|  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Cache em aplicativos do .NET Framework](../../../docs/framework/performance/caching-in-net-framework-applications.md)|Descreve técnicas para armazenar dados em cache para melhorar o desempenho no aplicativo.|  
|[Inicialização lenta](../../../docs/framework/performance/lazy-initialization.md)|Descreve como inicializar objetos quando necessário para melhorar o desempenho, especialmente na inicialização do aplicativo.|  
|[Confiabilidade](../../../docs/framework/performance/reliability.md)|Fornece informações sobre evitar exceções assíncronas em um ambiente de servidor.|  
|[Escrevendo aplicativos .NET Framework grandes e dinâmicos](../../../docs/framework/performance/writing-large-responsive-apps.md)|Fornece dicas de desempenho coletadas para regravar os compiladores C# e Visual Basic em código gerenciado, e inclui vários exemplos reais do compilador C#.|

