---
title: "Datas, horas e fusos horários | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-4.6
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: c50b3e328998b65ec47efe6d7457b36116813c77
ms.openlocfilehash: 2445188fda029ddc0f673d4c81f99f7f46edb89b
ms.lasthandoff: 04/08/2017

---
# <a name="dates-times-and-time-zones"></a>Datas, horas e fusos horários
Além da estrutura básica <xref:System.DateTime>, o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fornece as seguintes classes que dão suporte ao trabalho com fusos horários:  
  
-   <xref:System.TimeZone>  
  
     Use esta classe para trabalhar com o fuso horário local do sistema e a zona UTC (Tempo Universal Coordenado).  A funcionalidade da classe <xref:System.TimeZone> é amplamente substituída pela classe <xref:System.TimeZoneInfo>.  
  
-   <xref:System.TimeZoneInfo>  
  
     Use essa classe para trabalhar com qualquer fuso horário que esteja predefinido em um sistema, para criar novos fusos horários e para converter facilmente datas e horas de um fuso horário para outro. Para novo desenvolvimento, use a classe <xref:System.TimeZoneInfo> em vez da classe <xref:System.TimeZone>.  
  
-   <xref:System.DateTimeOffset>  
  
     Use essa estrutura para trabalhar com datas e horas cujo deslocamento (ou diferença) em relação ao horário UTC é conhecido. A estrutura <xref:System.DateTimeOffset> combina um valor de data e hora com o deslocamento desse horário em relação ao UTC. Devido à sua relação com o UTC, um valor individual de data e hora identifica, sem ambiguidade um único ponto no tempo. Isso dá mais portabilidade a um valor <xref:System.DateTimeOffset> de um computador para outro do que um valor <xref:System.DateTime>.  
  
 Esta seção da documentação fornece as informações de que você precisa para trabalhar com fusos horários e para criar aplicativos com reconhecimento de fuso horário que podem converter datas e horas de um fuso horário para outro.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão geral de fuso horário](../../../docs/standard/datetime/time-zone-overview.md)  
 Aborda a terminologia, os conceitos e os problemas envolvidos na criação de aplicativos com reconhecimento de fuso horário.  
  
 [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
 Aborda quando usar os tipos <xref:System.DateTime>, <xref:System.DateTimeOffset> e <xref:System.TimeZoneInfo> ao trabalhar com dados de data e hora.  
  
 [Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)  
 Descreve como enumerar os fusos horários encontrados em um sistema local.  
  
 [Como enumerar os fusos horários presentes em um computador](../../../docs/standard/datetime/enumerate-time-zones.md)  
 Fornece exemplos que enumeram os fusos horários definidos no Registro de um computador e que permitem aos usuários selecionar um fuso horário predefinido em uma lista.  
  
 [Como acessar os objetos de fuso horário predefinidos UTC e local](../../../docs/standard/datetime/access-utc-and-local.md)  
 Descreve como acessar o fuso horário local e do Tempo Universal Coordenado.  
  
 [Como criar uma instância de um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)  
 Descreve como criar uma instância de um objeto <xref:System.TimeZoneInfo> no Registro do sistema local.  
  
 [Criando uma instância de um objeto DateTimeOffset](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md)  
 Aborda de que maneiras é possível criar uma instância de um objeto <xref:System.DateTimeOffset> e de que maneiras um valor <xref:System.DateTime> pode ser convertido em um valor <xref:System.DateTimeOffset>.  
  
 [Como criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)  
 Descreve como criar um fuso horário personalizado que não dê suporte à transição bidirecional do horário de verão.  
  
 [Como criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)  
 Descreve como criar um fuso horário personalizado que dê suporte a uma ou mais transições bidirecionais do horário de verão.  
  
 [Salvando e restaurando fusos horários](../../../docs/standard/datetime/saving-and-restoring-time-zones.md)  
 Descreve o suporte de <xref:System.TimeZoneInfo> para serialização e desserialização dos dados de fuso horário e ilustra alguns dos cenários nos quais esses recursos podem ser usados.  
  
 [Como salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)  
 Descreve como criar um fuso horário personalizado e salvar suas informações em um arquivo de recurso.  
  
 [Como restaurar fusos horários de um recurso inserido](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)  
 Descreve como criar uma instância de fusos horários personalizados que foram salvos em um arquivo de recurso inserido.  
  
 [Executando operações aritméticas com datas e horas](../../../docs/standard/datetime/performing-arithmetic-operations.md)  
 Aborda os problemas envolvidos na adição, subtração e comparação dos valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.  
  
 [Como usar fusos horários em aritmética de data e hora](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)  
 Aborda como realizar a aritmética de data e hora que reflete as regras de ajuste de um fuso horário.  
  
 [Convertendo entre DateTime e DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md)  
 Descreve como converter entre os valores <xref:System.DateTime> e <xref:System.DateTimeOffset>.  
  
 [Convertendo horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md)  
 Descreve como converter horários de um fuso horário para outro.  
  
 [Como resolver horários ambíguos](../../../docs/standard/datetime/resolve-ambiguous-times.md)  
 Descreve como resolver um horário ambíguo, mapeando-o para o horário padrão do fuso horário.  
  
 [Como permitir que os usuários resolvam horários ambíguos](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)  
 Descreve como permitir que um usuário determine o mapeamento entre um horário local ambíguo e o Tempo Universal Coordenado.  
  
## <a name="reference"></a>Referência  
 <xref:System.TimeZoneInfo?displayProperty=fullName>
