---
title: Depuração, rastreamento e criação de perfil
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43927be83b8b2a9163656f8d6d54c2cf83a23e28
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052646"
---
# <a name="debugging-tracing-and-profiling"></a>Depuração, rastreamento e criação de perfil
Para depurar um aplicativo do .NET Framework, o compilador e o ambiente de tempo de execução devem ser configurados para habilitar um depurador a anexar ao aplicativo e gerar símbolos e mapas de linha, se possível, para o aplicativo a respectiva MSIL (Microsoft Intermediate Language) correspondente. Após um aplicativo gerenciado ter sido depurado, o perfil dele pode ser criado para aprimorar o desempenho. A criação de perfil avalia e descreve as linhas do código-fonte que geram o código executado com mais frequência e quanto tempo demora para executá-las.  
  
 Aplicativos do .NET framework são depurados facilmente usando o Visual Studio, que lida com muitos dos detalhes de configuração. Se o Visual Studio não estiver instalado, você poderá examinar e melhorar o desempenho de aplicativos do .NET Framework por meio das classes de depuração do namespace <xref:System.Diagnostics> do .NET Framework. Este namespace inclui as classes <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.TraceSource> para rastreamento de fluxo de execução e as classes <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog> e <xref:System.Diagnostics.PerformanceCounter> para criação de perfil de código.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Habilitando a depuração por anexação JIT](enabling-jit-attach-debugging.md)  
 Mostra como configurar o Registro para anexação JIT de um mecanismo de depuração para um aplicativo do .NET Framework.  
  
 [Facilitando a depuração de uma imagem](making-an-image-easier-to-debug.md)  
 Mostra como ligar o acompanhamento JIT e desligar a otimização para facilitar a depuração de um assembly.  
  
 [Rastreando e instrumentando aplicativos](tracing-and-instrumenting-applications.md)  
 Descreve como monitorar a execução de seu aplicativo enquanto ele está em execução e como instrumentá-lo para exibir quão bem ele está executando ou se algo deu errado.  
  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)  
 Descreve os MDAs (Assistentes de Depuração Gerenciados), que são recursos de depuração que trabalham com o CLR (Common Language Runtime) para fornecer informações sobre o estado do tempo de execução.  
  
 [Aprimorando a depuração com os atributos de exibição do depurador](enhancing-debugging-with-the-debugger-display-attributes.md)  
 Descreve como o desenvolvedor de um tipo pode especificar qual será a aparência desse tipo quando ele for exibido em um depurador.  
  
 [Contadores de desempenho](performance-counters.md)  
 Descreve os contadores que você pode usar para controlar o desempenho de um aplicativo.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Depurar aplicativos ASP.NET ou ASP.NET Core no Visual Studio](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 Fornece os pré-requisitos e as instruções sobre como depurar um aplicativo ASP.NET durante o desenvolvimento ou depois da implantação.  
  
 [Guia de desenvolvimento](../development-guide.md)  
 Fornece um guia para todas as principais áreas de tecnologia e tarefas para o desenvolvimento de aplicativos, incluindo a criação, a configuração, a depuração, a proteção e a implantação de seu aplicativo, bem como informações sobre programação dinâmica, interoperabilidade, extensibilidade, gerenciamento de memória e threading.
