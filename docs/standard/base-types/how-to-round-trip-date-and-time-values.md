---
title: Como aplicar uma viagem de ida e volta a valores de data e hora
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26a1cafc7ed6e497e5aab9cd33654f3aa3d4d98c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573168"
---
# <a name="how-to-round-trip-date-and-time-values"></a>Como aplicar uma viagem de ida e volta a valores de data e hora
Em muitos aplicativos, um valor de data e hora destina-se a identificar sem ambiguidade um único ponto no tempo. Este tópico mostra como salvar e restaurar um valor <xref:System.DateTime> e um valor <xref:System.DateTimeOffset> para que o valor restaurado identifique o mesmo horário que o valor salvo.  
  
### <a name="to-round-trip-a-datetime-value"></a>Para fazer uma viagem de ida e volta de um valor DateTime  
  
1.  Converta o valor <xref:System.DateTime> em sua representação de cadeia de caracteres chamando o método <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> com o especificador de formato "o".  
  
2.  Salve a representação de cadeia de caracteres do valor <xref:System.DateTime> em um arquivo ou passe-a por um processo, domínio de aplicativo ou limite de computador.  
  
3.  Recupere a cadeia de caracteres que representa o valor <xref:System.DateTime>.  
  
4.  Chame o método <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor do parâmetro `styles`.  
  
 O exemplo a seguir mostra como fazer a viagem de ida e volta de um valor <xref:System.DateTime>.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Fazendo a viagem de ida e volta de um valor <xref:System.DateTime>, essa técnica consegue preservar o horário para todos os horários locais e universais. Por exemplo, se um valor <xref:System.DateTime> local for salvo em um sistema nos EUA, o fuso horário padrão do Pacífico será restaurado em um sistema no fuso horário padrão da região central dos EUA; a data e hora restauradas estarão duas horas à frente da hora original, o que reflete a diferença de hora entre os dois fusos horários. No entanto, essa técnica não é necessariamente exata para horários não especificados. Todos os valores <xref:System.DateTime> cuja propriedade <xref:System.DateTime.Kind%2A> é <xref:System.DateTimeKind.Unspecified> são tratados como se fossem horários locais. Se não for o caso, <xref:System.DateTime> não conseguirá identificar o momento correto. A solução alternativa para essa limitação é acoplar rigorosamente um valor de data e hora com seu fuso horário para salvar e restaurar a operação.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Para fazer uma viagem de ida e volta de um valor DateTimeOffset  
  
1.  Converta o valor <xref:System.DateTimeOffset> em sua representação de cadeia de caracteres chamando o método <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> com o especificador de formato "o".  
  
2.  Salve a representação de cadeia de caracteres do valor <xref:System.DateTimeOffset> em um arquivo ou passe-a por um processo, domínio de aplicativo ou limite de computador.  
  
3.  Recupere a cadeia de caracteres que representa o valor <xref:System.DateTimeOffset>.  
  
4.  Chame o método <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor do parâmetro `styles`.  
  
 O exemplo a seguir mostra como fazer a viagem de ida e volta de um valor <xref:System.DateTimeOffset>.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Essa técnica sempre identifica sem ambiguidade um valor <xref:System.DateTimeOffset> como um único momento. O valor pode ser convertido em UTC (Tempo Universal Coordenado) chamando o método <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> ou pode ser convertido em determinado fuso horário chamando o método <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>. A principal limitação dessa técnica é que a aritmética de data e hora, quando executada em um valor <xref:System.DateTimeOffset> que representa o horário em determinado fuso horário, talvez não produza resultados precisos para esse fuso horário. Isso ocorre porque, quando um valor <xref:System.DateTimeOffset> é instanciado, é dissociado do fuso horário. Portanto, as regras de ajuste do fuso horário não podem mais ser aplicadas quando você executa cálculos de data e hora. É possível solucionar esse problema definindo um tipo personalizado que inclui um valor de data e hora e o respectivo fuso horário.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>Para fazer a viagem de ida e volta de um valor de data e hora com seu fuso horário  
  
1.  Defina uma classe ou uma estrutura com dois campos. O primeiro campo é um objeto <xref:System.DateTime> ou <xref:System.DateTimeOffset>, e o segundo é um objeto <xref:System.TimeZoneInfo>. O exemplo a seguir é uma versão simples desse tipo.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Marcar a classe com o atributo <xref:System.SerializableAttribute>.  
  
3.  Serialize o objeto usando o método <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>.  
  
4.  Restaure o objeto usando o método <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A>.  
  
5.  Transmita (em C#) ou converta (em Visual Basic) o objeto desserializado em um objeto do tipo apropriado.  
  
 O exemplo a seguir ilustra como fazer a viagem de ida e volta de um objeto que armazena informações de data e hora e fuso horário.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Essa técnica deve refletir sempre inequivocamente o ponto no tempo correto, antes e depois de ser salvo e restaurado, desde que a implementação do objeto combinado de data e hora e fuso horário não permita que o valor de data fique fora de sincronia com o valor de fuso horário.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos precisam de:  
  
-   Os seguintes namespaces sejam importados com instruções `using` em C# ou instruções `Imports` em Visual Basic:  
  
    -   <xref:System> (apenas para C#).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   Uma referência a System.Core.dll.  
  
-   Cada exemplo de código, exceto a classe `DateInTimeZone`, deve ser incluído em uma classe ou um módulo do Visual Basic, empacotado em métodos e chamado do método `Main`.  
  
## <a name="see-also"></a>Consulte também  
 [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
