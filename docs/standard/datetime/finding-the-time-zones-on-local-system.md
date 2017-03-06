---
title: "Encontrando os fusos horários definidos em um sistema local"
description: "Encontrando os fusos horários definidos em um sistema local"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: e61017e2a0e26295c3be7e8265674b1a5d2ae5a3
ms.lasthandoff: 03/02/2017

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Encontrando os fusos horários definidos em um sistema local

A classe [System.TimeZoneInfo](xref:System.TimeZoneInfo) não expõe um construtor público. Como resultado, a palavra-chave `new` não pode ser usada para criar um novo objeto [TimeZoneInfo](xref:System.TimeZoneInfo). Em vez disso, objetos [TimeZoneInfo](xref:System.TimeZoneInfo) são instanciados por meio da recuperação de informações sobre fusos horários predefinidos do sistema operacional. Este tópico discute a instanciação de um fuso horário dos dados armazenados pelo sistema operacional. Além disso, `static` (`Shared` no Visual Basic) propriedades da classe [TimeZoneInfo](xref:System.TimeZoneInfo) fornecem acesso ao UTC (Tempo Universal Coordenado) e ao fuso horário local.

## <a name="accessing-individual-time-zones"></a>Acessando fusos horários individuais

A classe [TimeZoneInfo](xref:System.TimeZoneInfo) fornece dois objetos de fuso horário predefinidos que representam o horário UTC e o fuso horário local. Eles estão disponíveis nas propriedades [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) e [TimeZoneInfo](xref:System.TimeZoneInfo.Local), respectivamente. Para obter instruções sobre como acessar o UTC ou fusos horários locais, veja [Como acessar os objetos de fuso horário UTC e local predefinidos](access-utc-and-local.md). 

Você também pode instanciar um objeto [TimeZoneInfo](xref:System.TimeZoneInfo) que representa qualquer fuso horário definido pelo sistema operacional. Para obter instruções sobre como instanciar um objeto de fuso horário específico, veja [Como criar uma instância de um objeto TimeZoneInfo](instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identificadores de fuso horário

O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário. Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo. Na maioria dos casos, seu valor corresponde ao da propriedade [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName), que é usada para fornecer o nome da hora padrão do fuso horário. No entanto, há exceções. A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores associados. Para obter instruções sobre como enumerar os fusos horários, veja [Como enumerar os fusos horários presentes em um computador](enumerate-time-zones.md).

## <a name="see-also"></a>Consulte também

[Datas, horas e fusos horários](index.md)

[Como acessar os objetos de fuso horário predefinidos UTC e local](access-utc-and-local.md)

[Como criar uma instância de um objeto TimeZoneInfo](instantiate-time-zone-info.md)

[Como enumerar os fusos horários presentes em um computador](enumerate-time-zones.md)

[Convertendo horários entre fusos horários](converting-between-time-zones.md)
