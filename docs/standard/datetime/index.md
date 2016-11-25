---
title: "Datas, horas e fusos horários"
description: "Datas, horas e fusos horários"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 76e6cacc-1c0c-4a71-8cb8-018c112385ba
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 74ba5a2e350db21cdb5a8c228c745ac3f54ed930

---

# <a name="dates-times-and-time-zones"></a>Datas, horas e fusos horários

Além da estrutura [DateTime](xref:System.DateTime) básica, o .NET fornece as seguintes classes que dão suporte ao trabalho com fusos horários:

* [System.TimeZoneInfo](xref:System.TimeZoneInfo)
    
  Use esta classe para trabalhar com o fuso horário local do sistema e a zona UTC (Tempo Universal Coordenado).
  
* [System.DateTimeOffset](xref:System.DateTimeOffset)  

  Use essa estrutura para trabalhar com datas e horas cujo deslocamento (ou diferença) em relação ao horário UTC é conhecido. A estrutura [DateTimeOffset](xref:System.DateTimeOffset)] combina um valor de data e hora com o deslocamento desse horário em relação ao UTC. Devido à sua relação com o UTC, um valor individual de data e hora identifica, sem ambiguidade um único ponto no tempo. Isso torna a portabilidade de um valor [DateTimeOffset](xref:System.DateTimeOffset)] de um computador para outro maior do que aquela de um valor [DateTime](xref:System.DateTime)]. 
  
Esta seção da documentação fornece as informações de que você precisa para trabalhar com fusos horários e para criar aplicativos com reconhecimento de fuso horário que podem converter datas e horas de um fuso horário para outro.

## <a name="in-this-section"></a>Nesta seção

[Visão geral do fuso horário](time-zone-overview.md) – aborda a terminologia, os conceitos e as questões envolvidas na criação de aplicativos com reconhecimento de fuso horário.
    
[Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](choosing-between-datetime.md) – descreve quando usar os tipos [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset) e [System.TimeZoneInfo](xref:System.TimeZoneInfo) ao trabalhar usando dados de data e hora.
    
[Encontrando os fusos horários definidos em um sistema local](finding-the-time-zones-on-local-system.md) –descreve como enumerar os fusos horários encontrados em um sistema local.

[Criando uma instância de um objeto DateTimeOffset](instantiating-a-datetimeoffset-object.md) – aborda as maneiras em que um objeto [System.DateTimeOffset](xref:System.DateTimeOffset) pode ser instanciado e as formas nas quais um valor [System.DateTime](xref:System.DateTime) pode ser convertido em um valor [System.DateTimeOffset](xref:System.DateTimeOffset).

[Executando operações aritméticas com datas e horas](performing-arithmetic-operations.md) – aborda as questões envolvidas na adição, subtração e comparação dos valores [System.DateTime](xref:System.DateTime) e [System.DateTimeOffset](xref:System.DateTimeOffset).

[Convertendo entre DateTime e DateTimeOffset](converting-between-datetime-and-offset.md) – descreve como converter entre os valores [System.DateTime](xref:System.DateTime) e [System.DateTimeOffset](xref:System.DateTimeOffset).

[Convertendo horários entre fusos horários](converting-between-time-zones.md) – descreve como converter horários de um fuso horário para outro.

[Como enumerar os fusos horários presentes em um computador](enumerate-time-zones.md) –fornece exemplos que enumeram os fusos horários definidos no Registro do computador e que permitem aos usuários selecionar um fuso horário predefinido de uma lista.

[Como acessar os objetos de fuso horário UTC e local predefinidos](access-utc-and-local.md) – descreve como acessar o Tempo Universal Coordenado e o fuso horário local.

[Como criar uma instância de um objeto TimeZoneInfo](instantiate-time-zone-info.md) – descreve como criar uma instância de um objeto [System.TimeZoneInfo](xref:System.TimeZoneInfo) do Registro do sistema local.

[Como usar fusos horários em aritmética de data e hora](use-time-zones-in-arithmetic.md) – descreve como realizar a aritmética de data e hora que reflete as regras de ajuste de um fuso horário.

[Como: resolver horários ambíguos](resolve-ambiguous-times.md) – descreve como resolver um horário ambíguo, mapeando-o para o horário padrão do fuso horário.

[Como permitir que os usuários resolvam horários ambíguos](let-users-resolve-ambiguous-times.md) –descreve como permitir que um usuário determine o mapeamento entre um hora local ambígua e o Tempo Universal Coordenado.

## <a name="reference"></a>Referência

[System.TimeZoneInfo](xref:System.TimeZoneInfo)

[System.DateTimeOffset](xref:System.DateTimeOffset)

[System.DateTime](xref:System.DateTime)



<!--HONumber=Nov16_HO3-->


