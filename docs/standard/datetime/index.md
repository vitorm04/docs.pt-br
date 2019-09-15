---
title: Datas, horas e fusos horários
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a5594b689a52b641ecece0f9a92fb6cdfe5735
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991281"
---
# <a name="dates-times-and-time-zones"></a>Datas, horas e fusos horários

Além da estrutura <xref:System.DateTime> básica, o .NET fornece as seguintes classes que dão suporte para trabalhar com fusos horários:

* <xref:System.TimeZone>

  Use esta classe para trabalhar com o fuso horário local do sistema e a zona UTC (Tempo Universal Coordenado). A funcionalidade da <xref:System.TimeZone> classe é amplamente substituída <xref:System.TimeZoneInfo> pela classe.

* <xref:System.TimeZoneInfo>

  Use essa classe para trabalhar com qualquer fuso horário que esteja predefinido em um sistema, para criar novos fusos horários e para converter facilmente datas e horas de um fuso horário para outro. Para novos desenvolvimentos, use a classe <xref:System.TimeZoneInfo> em vez da classe <xref:System.TimeZone>.

* <xref:System.DateTimeOffset>

  Use essa estrutura para trabalhar com datas e horas cujo deslocamento (ou diferença) em relação ao horário UTC é conhecido. A estrutura <xref:System.DateTimeOffset> combina um valor de data e hora com o deslocamento desse horário em relação ao UTC. Devido à sua relação com o UTC, um valor individual de data e hora identifica, sem ambiguidade um único ponto no tempo. Isso aumenta a portabilidade de um computador para outro de um valor de <xref:System.DateTimeOffset> em relação a um valor de <xref:System.DateTime>.

Esta seção da documentação fornece as informações de que você precisa para trabalhar com fusos horários e para criar aplicativos com reconhecimento de fuso horário que podem converter datas e horas de um fuso horário para outro.

## <a name="in-this-section"></a>Nesta seção

[Visão geral sobre fuso horário](../../../docs/standard/datetime/time-zone-overview.md) Discute a terminologia, os conceitos e os problemas envolvidos na criação de aplicativos com reconhecimento de fuso horário.

[Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discute quando usar os tipos <xref:System.DateTime>, <xref:System.DateTimeOffset> e <xref:System.TimeZoneInfo> ao trabalhar com os dados de data e hora.

[Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Descreve como enumerar os fusos horários encontrados em um sistema local.

[Como: Enumerar os fusos horários presentes](../../../docs/standard/datetime/enumerate-time-zones.md) em um computador fornece exemplos que enumeram os fusos horários definidos no registro de um computador e que permitem que os usuários selecionem um fuso horário predefinido de uma lista.

[Como: Acessar os objetos](../../../docs/standard/datetime/access-utc-and-local.md) de fuso horário local e UTC predefinidos descreve como acessar o tempo universal coordenado e o fuso horário local.

[Como: Instanciar um objeto](../../../docs/standard/datetime/instantiate-time-zone-info.md) TimeZoneInfo descreve como criar uma <xref:System.TimeZoneInfo> instância de um objeto do registro do sistema local.

[Criando uma instância de um objeto DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discute as maneiras de criar uma instância de um objeto <xref:System.DateTimeOffset> e maneiras de converter um valor <xref:System.DateTime> em um valor <xref:System.DateTimeOffset>.

[Como: Criar fusos horários sem regras](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) de ajuste descreve como criar um fuso horário personalizado que não dá suporte à transição de e para o horário de verão.

[Como: Criar fusos horários com regras](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) de ajuste descreve como criar um fuso horário personalizado que dá suporte a uma ou mais transições de e para o horário de verão.

[Salvando e restaurando fusos horários](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Descreve o suporte de <xref:System.TimeZoneInfo> para serialização e desserialização dos dados de fuso horário e ilustra alguns dos cenários nos quais esses recursos podem ser usados.

[Como: Salvar fusos horários em um recurso](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) inserido descreve como criar um fuso horário personalizado e salvar suas informações em um arquivo de recurso.

[Como: Restaurar fusos horários de um recurso](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) inserido descreve como criar uma instância de fusos horários personalizados que foram salvos em um arquivo de recurso inserido.

[Executando operações aritméticas com datas e horas](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discute os problemas envolvidos ao adicionar, subtrair e comparar valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.

[Como: Usar fusos horários na aritmética](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) de data e hora discute como executar aritmética de data e hora que reflete as regras de ajuste de um fuso horário.

[Convertendo entre DateTime e DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Descreve como converter entre valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.

[Convertendo horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md) Descreve como converter horários de um fuso horário para outro.

[Como: Resolver tempos](../../../docs/standard/datetime/resolve-ambiguous-times.md) ambíguos descreve como resolver um tempo ambíguo mapeando-o para o horário padrão do fuso horário.

[Como: Permitir que os usuários resolvam tempos](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) ambíguos descreve como permitir que um usuário determine o mapeamento entre uma hora local ambígua e o tempo universal coordenado.

## <a name="reference"></a>Referência

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
