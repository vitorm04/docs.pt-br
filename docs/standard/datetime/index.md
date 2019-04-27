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
ms.openlocfilehash: 5355666b95d75fc18d0188c978c186690ee9ccca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819698"
---
# <a name="dates-times-and-time-zones"></a>Datas, horas e fusos horários

Além da estrutura <xref:System.DateTime> básica, o .NET fornece as seguintes classes que dão suporte para trabalhar com fusos horários:

* <xref:System.TimeZone>

  Use esta classe para trabalhar com o fuso horário local do sistema e com o UTC (Tempo Universal Coordenado). A funcionalidade da classe <xref:System.TimeZone> é amplamente substituída pela classe <xref:System.TimeZoneInfo>.

* <xref:System.TimeZoneInfo>

  Use essa classe para trabalhar com qualquer fuso horário que esteja predefinido em um sistema, para criar novos fusos horários e para converter facilmente datas e horas de um fuso horário para outro. Para novos desenvolvimentos, use a classe <xref:System.TimeZoneInfo> em vez da classe <xref:System.TimeZone>.

* <xref:System.DateTimeOffset>

  Use essa estrutura para trabalhar com datas e horas cujo deslocamento (ou diferença) em relação ao horário UTC é conhecido. A estrutura <xref:System.DateTimeOffset> combina um valor de data e hora com o deslocamento desse horário em relação ao UTC. Devido à sua relação com o UTC, um valor individual de data e hora identifica, sem ambiguidade um único ponto no tempo. Isso aumenta a portabilidade de um computador para outro de um valor de <xref:System.DateTimeOffset> em relação a um valor de <xref:System.DateTime>.

Esta seção da documentação fornece as informações de que você precisa para trabalhar com fusos horários e para criar aplicativos com reconhecimento de fuso horário que podem converter datas e horas de um fuso horário para outro.

## <a name="in-this-section"></a>Nesta seção

[Visão geral sobre fuso horário](../../../docs/standard/datetime/time-zone-overview.md) Discute a terminologia, os conceitos e os problemas envolvidos na criação de aplicativos com reconhecimento de fuso horário.

[Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discute quando usar os tipos <xref:System.DateTime>, <xref:System.DateTimeOffset> e <xref:System.TimeZoneInfo> ao trabalhar com os dados de data e hora.

[Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Descreve como enumerar os fusos horários encontrados em um sistema local.

[Como: Enumerar os fusos horários presentes em um computador](../../../docs/standard/datetime/enumerate-time-zones.md) fornece exemplos que enumeram os fusos horários definidos no registro de um computador e que permitem aos usuários selecionar um fuso horário predefinido em uma lista.

[Como: Acessar os objetos de fuso horário UTC e local predefinidos](../../../docs/standard/datetime/access-utc-and-local.md) descreve como acessar o tempo Universal Coordenado e o fuso horário local.

[Como: Criar uma instância de um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) descreve como criar uma instância de um <xref:System.TimeZoneInfo> objeto do registro do sistema local.

[Criando uma instância de um objeto DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discute as maneiras de criar uma instância de um objeto <xref:System.DateTimeOffset> e maneiras de converter um valor <xref:System.DateTime> em um valor <xref:System.DateTimeOffset>.

[Como: Criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) descreve como criar um fuso horário personalizado que não oferece suporte a transição do horário de verão.

[Como: Criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) descreve como criar um fuso horário personalizado que dá suporte a um ou mais transições de / para horário de verão.

[Salvando e restaurando fusos horários](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Descreve o suporte de <xref:System.TimeZoneInfo> para serialização e desserialização dos dados de fuso horário e ilustra alguns dos cenários nos quais esses recursos podem ser usados.

[Como: Salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) descreve como criar um fuso horário personalizado e salvar suas informações em um arquivo de recurso.

[Como: Restaurar fusos horários de um recurso inserido](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) descreve como instanciar fusos horários personalizados que foram salvos em um arquivo de recurso inserido.

[Executando operações aritméticas com datas e horas](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discute os problemas envolvidos ao adicionar, subtrair e comparar valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.

[Como: Usar fusos horários de data e hora aritmética](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) aborda como realizar a data e hora que reflete as regras de ajuste de um fuso horário.

[Convertendo entre DateTime e DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Descreve como converter entre valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.

[Convertendo horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md) Descreve como converter horários de um fuso horário para outro.

[Como: Resolver horários ambíguos](../../../docs/standard/datetime/resolve-ambiguous-times.md) descreve como resolver um horário ambíguo, mapeando-o para o horário de padrão do fuso horário.

[Como: Permitir que os usuários resolvam horários ambíguos](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) descreve como permitir que um usuário determine o mapeamento entre um hora local ambígua e o tempo Universal Coordenado.

## <a name="reference"></a>Referência

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
