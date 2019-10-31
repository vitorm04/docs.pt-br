---
title: Como criar uma instância de um objeto TimeZoneInfo
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
ms.openlocfilehash: 5975270dd6a166bb625278a97f4c60851cbe7942
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122291"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Como criar uma instância de um objeto TimeZoneInfo

A maneira mais comum de instanciar um objeto <xref:System.TimeZoneInfo> é recuperar informações sobre ele do registro. Este tópico discute como criar uma instância de um objeto de <xref:System.TimeZoneInfo> do registro do sistema local.

### <a name="to-instantiate-a-timezoneinfo-object"></a>Para criar uma instância de um objeto TimeZoneInfo

1. Declare um objeto <xref:System.TimeZoneInfo>.

2. Chame o método de <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> de `static` (`Shared` no Visual Basic).

3. Manipule quaisquer exceções geradas pelo método, especialmente a <xref:System.TimeZoneNotFoundException> que é gerada se o fuso horário não estiver definido no registro.

## <a name="example"></a>Exemplo

O código a seguir recupera um objeto <xref:System.TimeZoneInfo> que representa o fuso horário padrão do leste e exibe a hora padrão do leste que corresponde à hora local.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

O parâmetro único do método de <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> é o identificador do fuso horário que você deseja recuperar, que corresponde à propriedade <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> do objeto. O identificador do fuso horário é um campo de chave que identifica exclusivamente o fuso horário. Enquanto a maioria das chaves são relativamente curtas, o identificador de fuso horário é comparativamente longo. Na maioria dos casos, seu valor corresponde à propriedade <xref:System.TimeZoneInfo.StandardName%2A> de um objeto <xref:System.TimeZoneInfo>, que é usado para fornecer o nome do horário padrão do fuso horário. No entanto, há exceções. A melhor maneira de certificar-se de que você forneça um identificador válido é enumerar os fusos horários disponíveis no sistema e observar os identificadores dos fusos horários presentes nele. Para obter uma ilustração, consulte [como: enumerar fusos horários presentes em um computador](../../../docs/standard/datetime/enumerate-time-zones.md). O tópico [Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) também contém uma lista de identificadores de fuso horário selecionados.

Se o fuso horário for encontrado, o método retornará seu <xref:System.TimeZoneInfo> objeto. Se o fuso horário não for encontrado, o método lançará um <xref:System.TimeZoneNotFoundException>. Se o fuso horário for encontrado, mas seus dados estiverem corrompidos ou incompletos, o método lançará um <xref:System.InvalidTimeZoneException>.

Se seu aplicativo depende de um fuso horário que deve estar presente, primeiro você deve chamar o método <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> para recuperar as informações de fuso horário do registro. Se a chamada do método falhar, o manipulador de exceção deverá criar uma nova instância do fuso horário ou recriá-la desserializando um objeto de <xref:System.TimeZoneInfo> serializado. Consulte [como: restaurar fusos horários de um recurso inserido](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) para obter um exemplo.

## <a name="see-also"></a>Consulte também

- [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
- [Encontrando os fusos horários definidos em um sistema local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Como acessar os objetos de fuso horário predefinidos UTC e local](../../../docs/standard/datetime/access-utc-and-local.md)
