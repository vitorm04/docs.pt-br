---
title: Registro em log e rastreamento – .NET Core
description: Uma introdução ao rastreamento e registro em log do .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 06781c6a5c1d771b1fa772539705cd1e2b3ad2d4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "70234620"
---
# <a name="net-core-logging-and-tracing"></a>Log e rastreamento do .NET Core

O registro em log e o rastreamento são, na verdade, dois nomes para a mesma técnica. A técnica simples foi usada desde os primórdios dos computadores. Ele simplesmente envolve a instrumentação de um aplicativo para gravar a saída a ser consumida posteriormente.

## <a name="reasons-to-use-logging-and-tracing"></a>Motivos para usar o log e o rastreamento

Essa técnica simples é surpreendentemente poderosa. Ele pode ser usado em situações em que um depurador falha:

- Problemas que ocorrem por longos períodos de tempo podem ser difíceis de depurar com um depurador tradicional. Os logs permitem uma análise detalhada do post-mortem, abrangendo longos períodos de tempo. Por outro lado, os depuradores são restritos à análise em tempo real.
- Aplicativos multithread e aplicativos distribuídos costumam ser difíceis de depurar.  A anexação de um depurador tende a modificar comportamentos. Logs detalhados podem ser analisados conforme necessário para entender sistemas complexos.
- Problemas em aplicativos distribuídos podem surgir de uma interação complexa entre vários componentes e talvez não seja razoável conectar um depurador a todas as partes do sistema.
- Muitos serviços não devem ser interrompidos. A anexação de um depurador geralmente causa falhas de tempo limite.
- Os problemas nem sempre são previstoss. O registro em log e o rastreamento são projetados para baixa sobrecarga, para que os programas sempre possam ser gravados caso ocorra um problema.

## <a name="net-core-apis"></a>APIs do .NET Core

### <a name="print-style-apis"></a>APIs de estilo de impressão

As <xref:System.Console?displayProperty=nameWithType>classes <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, e<xref:System.Diagnostics.Debug?displayProperty=nameWithType> fornecem, cada uma, APIs semelhantes de estilo de impressão conveniente para o registro em log.

A escolha da API de estilo de impressão a ser usada cabe a você. As principais diferenças são:
- <xref:System.Console?displayProperty=nameWithType>
  - Sempre habilitado e sempre grava no console.
  - Útil para informações que seu cliente talvez precise ver na versão.
  - Por ser a abordagem mais simples, ela é frequentemente usada para depuração temporária ad hoc. Geralmente, esse código de depuração nunca é verificado no controle do código-fonte.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Habilitado somente quando `TRACE` é definido.
  - Grava em anexado <xref:System.Diagnostics.Trace.Listeners>, por padrão, <xref:System.Diagnostics.DefaultTraceListener>o.
  - Use essa API ao criar logs que serão habilitados na maioria das compilações.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Habilitado somente quando `DEBUG` é definido.
  - Grava em um depurador anexado.
  - Em `*nix` gravações em stderr, `COMPlus_DebugWriteToStdErr` se estiver definido.
  - Use essa API ao criar logs que serão habilitados somente em compilações de depuração.

### <a name="logging-events"></a>Eventos de log

As APIs a seguir são mais orientadas a eventos. Em vez de registrar cadeias de caracteres simples, eles registram objetos de evento.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource é a principal API de rastreamento do .NET Core raiz.
  - Disponível em todas as versões de .NET Standard.
  - Permite apenas rastrear objetos serializáveis.
  - Grava nos ouvintes de [eventos](xref:System.Diagnostics.Tracing.EventListener)anexados.
  - O .NET Core fornece ouvintes para:
    - EventPipe do .NET Core em todas as plataformas
    - [ETW (rastreamento de eventos para Windows)](/windows/win32/etw/event-tracing-portal)
    - [Estrutura de rastreamento do LTTng para Linux](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Incluído no .NET Core e como um [pacote NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) para .NET Framework.
  - Permite o rastreamento em processo de objetos não serializáveis.
  - Inclui uma ponte para permitir que os campos selecionados de objetos registrados sejam gravados <xref:System.Diagnostics.Tracing.EventSource>em um.

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Fornece uma maneira definitiva de identificar mensagens de log resultantes de uma atividade ou transação específica. Esse objeto pode ser usado para correlacionar logs entre diferentes serviços.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Somente Windows.
  - Grava mensagens no log de eventos do Windows.
  - Os administradores do sistema esperam que as mensagens de erro fatais do aplicativo apareçam no log de eventos do Windows.

## <a name="ilogger-and-logging-frameworks"></a>ILogger e estruturas de registro em log

As APIs de nível baixo podem não ser a escolha certa para suas necessidades de registro em log. Talvez você queira considerar uma estrutura de registro em log.

A <xref:Microsoft.Extensions.Logging.ILogger> interface foi usada para criar uma interface de log comum em que os agentes podem ser inseridos por meio da injeção de dependência.

Por exemplo, para permitir que você faça a melhor escolha para seu aplicativo `ASP.NET` oferece suporte para uma seleção de estruturas internas e de terceiros:
- [Provedores de log internos do ASP.NET](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [Provedores de log de terceiros do ASP.NET](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Referências relacionadas ao log

- [Como: compilar condicionalmente com Trace e Debug](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Como: Adicionar instruções de rastreamento ao código do aplicativo](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- O [log do ASP.net](/aspnet/core/fundamentals/logging) fornece uma visão geral das técnicas de log que ele suporta.

- A interpolação de cadeias de caracteres pode simplificar a gravação do código [ C# ](../../csharp/language-reference/tokens/interpolated.md)

- A <xref:System.Exception.Message?displayProperty=nameWithType> propriedade é útil para registrar exceções.

- A <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe pode ser útil para fornecer informações de pilha em seus logs.

## <a name="performance-considerations"></a>Considerações sobre o desempenho

A formatação da cadeia de caracteres pode levar tempo de processamento de CPU perceptível.

Em aplicativos de desempenho crítico, é recomendável que você:
- Evite muitos registros em log quando ninguém estiver ouvindo. Evite construir mensagens de registro em log dispendiosas verificando se o log está habilitado primeiro.
- Registre apenas o que é útil.
- Adie a formatação sofisticada para o estágio de análise.
