---
title: Registro e rastreamento - .NET Core
description: Uma introdução ao .NET Core registrando e rastreando.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714418"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core registrando e rastreando

Registro e rastreamento são realmente dois nomes para a mesma técnica. A técnica simples tem sido usada desde os primórdios dos computadores. Ele simplesmente envolve instrumentar um aplicativo para gravar saída para ser consumido mais tarde.

## <a name="reasons-to-use-logging-and-tracing"></a>Razões para usar o registro e o rastreamento

Esta técnica simples é surpreendentemente poderosa. Ele pode ser usado em situações em que um depurador falha:

- Problemas que ocorrem por longos períodos de tempo, podem ser difíceis de depurar com um depurador tradicional. Os registros permitem uma revisão pós-morte detalhada que abrange longos períodos de tempo. Em contraste, os depuradores são limitados à análise em tempo real.
- Aplicativos multi-threaded e aplicativos distribuídos são muitas vezes difíceis de depurar.  Anexar um depurador tende a modificar comportamentos. Registros detalhados podem ser analisados conforme necessário para entender sistemas complexos.
- Problemas em aplicativos distribuídos podem surgir de uma interação complexa entre muitos componentes e pode não ser razoável conectar um depurador a cada parte do sistema.
- Muitos serviços não devem ser paralisados. Anexar um depurador muitas vezes causa falhas no tempo.
- Problemas nem sempre são previstos. O registro e o rastreamento são projetados para baixa sobrecarga para que os programas possam estar sempre gravando caso ocorra um problema.

## <a name="net-core-apis"></a>.NET Core APIs

### <a name="print-style-apis"></a>APIs de estilo de impressão

As <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> e as classes fornecem APIs de estilo de impressão semelhantes convenientes para o registro.

A escolha de qual API estilo de impressão usar depende de você. As principais diferenças são:

- <xref:System.Console?displayProperty=nameWithType>
  - Sempre habilitado e sempre escreve para o console.
  - Útil para informações que seu cliente pode precisar ver na versão.
  - Por ser a abordagem mais simples, é frequentemente usada para depuração temporária ad-hoc. Este código de depuração muitas vezes nunca é verificado no controle de origem.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Somente ativado `TRACE` quando definido.
  - Grava em <xref:System.Diagnostics.Trace.Listeners>anexo, por <xref:System.Diagnostics.DefaultTraceListener>padrão o .
  - Use esta API ao criar logs que serão ativados na maioria das compilações.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Somente ativado `DEBUG` quando definido.
  - Grava para um depurador anexado.
  - Em `*nix` gravações para `COMPlus_DebugWriteToStdErr` stderr se estiver definido.
  - Use esta API ao criar logs que serão ativados apenas em compilações de depuração.

### <a name="logging-events"></a>Eventos de registro

As APIs a seguir são mais orientadas para eventos. Em vez de registrar cadeias simples, eles registram objetos de evento.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource é a API de rastreamento principal do .NET Core.
  - Disponível em todas as versões .NET Standard.
  - Só permite rastrear objetos serializáveis.
  - Escreve para os [ouvintes](xref:System.Diagnostics.Tracing.EventListener)do evento anexado.
  - O .NET Core fornece aos ouvintes:
    - EventPipe da .NET Core em todas as plataformas
    - [ETW (Rastreamento de Eventos do Windows)](/windows/win32/etw/event-tracing-portal)
    - [Estrutura de rastreamento LTTng para Linux](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Incluído no .NET Core e como um [pacote NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) para .NET Framework.
  - Permite o rastreamento em processo de objetos não serializáveis.
  - Inclui uma ponte para permitir que campos selecionados <xref:System.Diagnostics.Tracing.EventSource>de objetos registrados sejam gravados em um .

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Fornece uma maneira definitiva de identificar mensagens de log resultantes de uma atividade ou transação específica. Este objeto pode ser usado para correlacionar registros em diferentes serviços.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Somente Windows.
  - Escreve mensagens no Registro de Eventos do Windows.
  - Os administradores do sistema esperam que mensagens fatais de erro de aplicativo apareçam no Registro de Eventos do Windows.

## <a name="ilogger-and-logging-frameworks"></a>Estruturas de ILogger e registro

As APIs de baixo nível podem não ser a escolha certa para suas necessidades de registro. Você pode querer considerar uma estrutura de registro.

A <xref:Microsoft.Extensions.Logging.ILogger> interface foi usada para criar uma interface de registro comum onde os madeireiros podem ser inseridos através de injeção de dependência.

Por exemplo, permitir que você faça a `ASP.NET` melhor escolha para o seu aplicativo oferece suporte para uma seleção de frameworks integrados e de terceiros:

- [ASP.NET construído em provedores de registro](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET provedores de registro de terceiros](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Referências relacionadas ao registro

- [Como compilar condicionalmente com Trace e Debug](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Como adicionar instruções de rastreamento ao código de um aplicativo](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.NET Logging](/aspnet/core/fundamentals/logging) fornece uma visão geral das técnicas de registro que suporta.

- [C# Interpolação de strings](../../csharp/language-reference/tokens/interpolated.md) pode simplificar a escrita do código de registro.

- A <xref:System.Exception.Message?displayProperty=nameWithType> propriedade é útil para registrar exceções.

- A <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe pode ser útil para fornecer informações de pilha em seus registros.

## <a name="performance-considerations"></a>Considerações sobre o desempenho

A formatação de strings pode levar um tempo perceptível de processamento da CPU.

Em aplicações críticas de desempenho, recomenda-se que você:

- Evite muitos registros quando ninguém estiver ouvindo. Evite construir mensagens de registro caras verificando se o registro está ativado primeiro.
- Só registre o que é útil.
- Adie a formatação extravagante para o estágio de análise.
