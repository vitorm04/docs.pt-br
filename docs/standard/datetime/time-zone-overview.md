---
title: "Visão geral do fuso horário"
description: "Visão geral do fuso horário"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e3a10f62-d403-4441-8621-adc964e32c07
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 67d77b80c2517da1c553094689eaf08c0c29078b

---

# <a name="time-zone-overview"></a>Visão geral do fuso horário

A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) simplifica a criação de aplicativos com reconhecimento de fuso horário. A classe [TimeZoneInfo](xref:System.TimeZoneInfo) oferece suporte para trabalhar com o fuso horário local e o Tempo Universal Coordenado (UTC), além de qualquer outro fuso horário cujas informações sejam predefinidas no Registro. Você também pode usar a [TimeZoneInfo](xref:System.TimeZoneInfo) para definir fusos horários personalizados dos quais o sistema não tenha nenhuma informação.

## <a name="time-zone-essentials"></a>Informações gerais sobre fuso horário

Um fuso horário é uma região geográfica na qual o mesmo horário é usado. Normalmente, mas nem sempre, os fusos horários adjacentes diferem em uma hora. A hora em cada um dos fusos horários do mundo pode ser expressa como uma diferença do Tempo Universal Coordenado (UTC).

Muitos dos fusos horários do mundo permitem horário de verão. O horário de verão tenta maximizar as horas do dia com sol adiantando o horário em uma hora na primavera ou no começo do verão e retornando ao horário normal (ou padrão) no final do verão ou no outono. Essas alterações de/para o horário padrão são conhecidas como regras de ajuste.

A transição de/para o horário de verão em um determinado fuso horário pode ser definida por uma regra de ajuste fixa ou flutuante. Uma regra de ajuste fixa define uma data específica na qual a transição de/para o horário de verão ocorre todos os anos. Por exemplo, uma transição do horário de verão para o horário padrão que ocorre todos os anos em 25 de outubro segue uma regra de ajuste fixa. Muito mais comuns são as regras de ajuste flutuante, que definem um dia específico de uma semana específica de um mês específico para a transição de/para o horário de verão. Por exemplo, uma transição do horário padrão para o horário de verão que ocorre no terceiro domingo de março segue uma regra de ajuste flutuante.

Para os fusos horários que oferecem suporte às regras de ajuste, a transição de/para o horário de verão cria dois tipos de horários anômalos: horários inválidos e horários ambíguos. Um horário inválido é um horário inexistente criado pela transição do horário padrão para o horário de verão. Por exemplo, se essa transição ocorrer em um determinado dia às 2h e fizer com que o horário mude para 3h, cada intervalo de tempo entre 2h e 2h59min99 será inválido. Um horário ambíguo é aquele que pode ser mapeado para dois horários diferentes em um único fuso horário. Ele é criado pela transição do horário de verão para o horário padrão. Por exemplo, se essa transição ocorrer em um determinado dia às 2h e fizer com que o horário mude para 1h, cada intervalo de tempo entre 1h e 1h59min99 poderá ser interpretado como horário padrão ou horário de verão. 

## <a name="time-zone-terminology"></a>Terminologia de fuso horário

A tabela a seguir define os termos que geralmente são usados ao trabalhar com fusos horários e ao desenvolver aplicativos com reconhecimento de fuso horário.

Termo | Definição
---- | ----------
Regra de ajuste | Uma regra que define quando ocorre a transição do horário padrão para o horário de verão e o retorno do horário de verão para o horário padrão. Cada regra de ajuste tem uma data de início e uma de término que definem quando a regra está em vigor (por exemplo, a regra de ajuste está em vigor de 1 de janeiro de 1986 a 31 de dezembro de 2020), um delta (o período de tempo de mudança do horário padrão como resultado da aplicação da regra de ajuste) e informações sobre a data e a hora específicas em que as transições devem ocorrer durante o período de ajuste. As transições podem seguir uma regra fixa ou uma regra flutuante.
Horário ambíguo | Um horário que pode ser mapeado para dois horários diferentes em um único fuso horário. Ocorre quando o horário do relógio é atrasado, como durante a transição do horário de verão de um fuso horário para seu horário padrão. Por exemplo, se essa transição ocorrer em um determinado dia às 2h e fizer com que o horário mude para 1h, cada intervalo de tempo entre 1h e 1h59min99 poderá ser interpretado como horário padrão ou horário de verão. 
Regra fixa | Uma regra de ajuste que define uma data específica para a transição de/para o horário de verão. Por exemplo, uma transição do horário de verão para o horário padrão que ocorre todos os anos em 25 de outubro segue uma regra de ajuste fixa.
Regra flutuante | Uma regra de ajuste que define um dia específico de uma semana específica de um mês específico para a transição de/para o horário de verão. Por exemplo, uma transição do horário padrão para o horário de verão que ocorre no terceiro domingo de março segue uma regra de ajuste flutuante.
Horário inválido | Um horário inexistente que é um artefato da transição do horário padrão para o horário de verão. Ocorre quando o horário do relógio é adiantado, como durante a transição do horário padrão de um fuso horário para seu horário de verão. Por exemplo, se essa transição ocorrer em um determinado dia às 2h e fizer com que o horário mude para 3h, cada intervalo de tempo entre 2h e 2h59min99 será inválido.
Horário de transição | Informações sobre uma mudança de horário específica, como a mudança do horário de verão para o horário padrão ou vice-versa, em um determinado fuso horário.

## <a name="time-zones-and-the-timezoneinfo-class"></a>Fusos horários e a classe TimeZoneInfo

No .NET, um objeto [System.TimeZoneInfo](xref:System.TimeZoneInfo) representa um fuso horário, com base nas informações fornecidas pelo sistema operacional. A dependência da classe [TimeZoneInfo](xref:System.TimeZoneInfo) no sistema operacional significa que um aplicativo com reconhecimento de fuso horário não pode ter certeza de que um determinado fuso horário esteja definido em todos os sistemas operacionais. Como resultado, a tentativa de criar uma instância de um fuso horário específico (que não seja o fuso horário local ou o fuso horário que representa o UTC) deve usar tratamento de exceção. Ela também deve fornecer algum método para permitir que o aplicativo continue caso não seja possível criar uma instância de um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) necessário.

Como cada fuso horário é caracterizado por uma diferença base do UTC, bem como por uma diferença do UTC que reflete as regras de ajuste existentes, um horário em um fuso horário pode ser facilmente convertido no horário em outro fuso horário. Para essa finalidade, o objeto [TimeZoneInfo](xref:System.TimeZoneInfo) inclui vários métodos de conversão, como:

* [ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)), que converte um [System.DateTime](xref:System.DateTime) no horário em um fuso horário específico.

* [ConvertTime(DateTime, TimeZoneInfo, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo,System.TimeZoneInfo)), que converte um [DateTime](xref:System.DateTime) de um fuso horário para outro.

* [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)), que converte um [System.DateTimeOffset](xref:System.DateTimeOffset) no horário em um determinado fuso horário. 

Para obter detalhes de como converter horários entre fusos horários, consulte [Convertendo horários entre fusos horários](converting-between-time-zones.md).

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)


<!--HONumber=Nov16_HO3-->


