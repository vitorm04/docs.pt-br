---
title: "Encontrando os fusos horários definidos em um sistema local"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c86932455301d15621c03d4440a8a16e44575bac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Encontrando os fusos horários definidos em um sistema local

O <xref:System.TimeZoneInfo> classe expõe um construtor público. Como resultado, o `new` palavra-chave não pode ser usado para criar um novo <xref:System.TimeZoneInfo> objeto. Em vez disso, <xref:System.TimeZoneInfo> objetos são instanciados Recuperando informações sobre fusos horários predefinidos do registro ou por meio da criação de um fuso horário personalizado. Este tópico discute a instanciação de um fuso horário dos dados armazenados no registro. Além disso, `static` (`shared` no Visual Basic) propriedades da <xref:System.TimeZoneInfo> classe fornecer acesso ao tempo Universal Coordenado (UTC) e o fuso horário local.

> [!NOTE]
> Para o fuso horário que não estão definido no registro, você pode criar fusos horários personalizados chamando as sobrecargas do <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método. Criação de um fuso horário personalizado são discutidas no [como: criar fusos horários sem regras de ajuste](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) e [como: criar fusos horários com regras de ajuste](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) tópicos. Além disso, você pode instanciar uma <xref:System.TimeZoneInfo> objeto restaurando-o de uma cadeia de caracteres serializada com o <xref:System.TimeZoneInfo.FromSerializedString%2A> método. Serialização e desserialização de um <xref:System.TimeZoneInfo> objeto é abordado no [como: salvar fusos horários em um recurso incorporado](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) e [como: restaurar fusos horários de um recurso incorporado](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) tópicos.

## <a name="accessing-individual-time-zones"></a>Acessando fusos horários individuais

O <xref:System.TimeZoneInfo> classe fornece dois objetos de fuso horário predefinidos que representam a hora UTC e o fuso horário local. Estão disponíveis no <xref:System.TimeZoneInfo.Utc%2A> e <xref:System.TimeZoneInfo.Local%2A> propriedades, respectivamente. Para obter instruções sobre como acessar o UTC ou fusos horários locais, consulte [como: acessar os objetos de zona UTC e a hora local predefinidos](../../../docs/standard/datetime/access-utc-and-local.md).

Você também pode instanciar uma <xref:System.TimeZoneInfo> objeto que representa qualquer fuso horário definido no registro. Para obter instruções sobre como instanciar um objeto de fuso horário específico, consulte [como: instanciar um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identificadores de fuso horário

O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário. Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo. Na maioria dos casos, seu valor corresponde do <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> propriedade, que é usada para fornecer o nome do padrão de tempo do fuso horário. No entanto, há exceções. A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores associados.

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
[como: acessar os objetos de zona UTC e a hora local predefinidos](../../../docs/standard/datetime/access-utc-and-local.md)
[como: instanciar um objeto TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Convertendo horários entre fusos horários](../../../docs/standard/datetime/converting-between-time-zones.md)
