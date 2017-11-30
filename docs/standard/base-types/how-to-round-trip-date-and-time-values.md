---
title: Como aplicar uma viagem de ida e volta a valores de data e hora
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a>Como aplicar uma viagem de ida e volta a valores de data e hora
Em muitos aplicativos, um valor de data e hora destina-se a identificar sem ambiguidade um único ponto no tempo. Este tópico mostra como salvar e restaurar um <xref:System.DateTime> valor, uma <xref:System.DateTimeOffset> informações de zona valor e um valor de data e hora com o tempo para que o valor restaurado identifique o mesmo tempo que o valor salvo.  
  
### <a name="to-round-trip-a-datetime-value"></a>Para fazer uma viagem de ida e volta de um valor DateTime  
  
1.  Converter o <xref:System.DateTime> valor em sua representação de cadeia de caracteres ao chamar o <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> método com o especificador de formato "o".  
  
2.  Salve a representação de cadeia de caracteres da <xref:System.DateTime> valor para um arquivo, ou passe-o por um processo, domínio de aplicativo ou fronteira de máquina.  
  
3.  Recuperar a cadeia de caracteres que representa o <xref:System.DateTime> valor.  
  
4.  Chamar o <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> método e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor da `styles` parâmetro.  
  
 O exemplo a seguir ilustra como viagem um <xref:System.DateTime> valor.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 Quando ciclo um <xref:System.DateTime> valor, essa técnica preserva com êxito a hora para todos os horários locais e universais. Por exemplo, se um local <xref:System.DateTime> valor é salvo em um sistema nos EUA. o fuso horário padrão do Pacífico será restaurado em um sistema no fuso horário padrão da região central dos EUA; a data e hora restauradas estarão duas horas à frente da hora original, o que reflete a diferença de hora entre os dois fusos horários. No entanto, essa técnica não é necessariamente exata para horários não especificados. Todos os <xref:System.DateTime> valores cujos <xref:System.DateTime.Kind%2A> é de propriedade <xref:System.DateTimeKind.Unspecified> são tratados como se eles fossem horas locais. Se não for o caso, o <xref:System.DateTime> não identificará com êxito o ponto correto no tempo. A solução alternativa para essa limitação é acoplar rigorosamente um valor de data e hora com seu fuso horário para salvar e restaurar a operação.  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a>Para fazer uma viagem de ida e volta de um valor DateTimeOffset  
  
1.  Converter o <xref:System.DateTimeOffset> valor em sua representação de cadeia de caracteres ao chamar o <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> método com o especificador de formato "o".  
  
2.  Salve a representação de cadeia de caracteres da <xref:System.DateTimeOffset> valor para um arquivo, ou passe-o por um processo, domínio de aplicativo ou fronteira de máquina.  
  
3.  Recuperar a cadeia de caracteres que representa o <xref:System.DateTimeOffset> valor.  
  
4.  Chamar o <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> método e passe <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> como o valor da `styles` parâmetro.  
  
 O exemplo a seguir ilustra como viagem um <xref:System.DateTimeOffset> valor.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 Essa técnica sempre identifica sem ambiguidade um <xref:System.DateTimeOffset> valor como um único ponto no tempo. O valor pode, em seguida, ser convertido para o tempo Universal Coordenado (UTC) chamando o <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> método, ou ele pode ser convertido para o tempo em um determinado fuso horário chamando o <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> método. A principal limitação dessa técnica é a data e hora aritmética, quando executada em um <xref:System.DateTimeOffset> valor que representa a hora em um determinado fuso horário, talvez não produza resultados precisos para esse fuso horário. Isso ocorre porque quando um <xref:System.DateTimeOffset> valor é instanciado, ele é dissociado do seu fuso horário. Portanto, as regras de ajuste do fuso horário não podem mais ser aplicadas quando você executa cálculos de data e hora. É possível solucionar esse problema definindo um tipo personalizado que inclui um valor de data e hora e o respectivo fuso horário.  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a>A viagem um valor de data e hora com seu fuso horário  
  
1.  Defina uma classe ou uma estrutura com dois campos. O primeiro campo é um <xref:System.DateTime> ou um <xref:System.DateTimeOffset> objeto e o segundo é um <xref:System.TimeZoneInfo> objeto. O exemplo a seguir é uma versão simple de tal tipo.  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  Marcar a classe com o <xref:System.SerializableAttribute> atributo.  
  
3.  Serialize o objeto usando o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> método.  
  
4.  Restaure o objeto usando o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> método.  
  
5.  Cast (em c#) ou converta (no Visual Basic) o objeto desserializado em um objeto do tipo apropriado.  
  
 O exemplo a seguir ilustra como a viagem um objeto que armazena informações de data e hora e fuso horário.  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 Essa técnica deve refletir sempre inequivocamente o ponto correto de tempo tanto antes e depois de ser salvo e restaurado, fornecido a implementação do objeto combinado de data e hora e fuso horário não permite que o valor de data fiquem fora de sincronia com o valor de fuso horário.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Esses exemplos precisam de:  
  
-   Se os seguintes namespaces importados com c# `using` instruções ou [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` instruções:  
  
    -   <xref:System>(Apenas c#).  
  
    -   <xref:System.Globalization?displayProperty=nameWithType>.  
  
    -   <xref:System.IO?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization?displayProperty=nameWithType>.  
  
    -   <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.  
  
-   Uma referência a System.Core.dll.  
  
-   Cada exemplo de código, que o `DateInTimeZone` classe deve ser incluído em uma classe ou um módulo do Visual Basic, empacotado em métodos e chamado a partir de `Main` método.  
  
## <a name="see-also"></a>Consulte também  
 [Executando operações de formatação](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [Escolhendo entre DateTime, DateTimeOffset, TimeSpan e TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [Cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
