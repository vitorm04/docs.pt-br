---
title: Analisando cadeias de caracteres de data e hora no .NET Framework
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
- parsing strings, date and time strings
- date and time strings
- ParseExact method
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- DateTime object
- time strings
ms.assetid: 43bae51e-9b1d-41a6-a187-772c0d096d90
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1beceb2b2d32c500e73cd7786c480fcd84c3001c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>Análise de data e hora de cadeias de caracteres no .NET
Métodos de análise convertem a representação de cadeia de caracteres de data e hora para um equivalente <xref:System.DateTime> objeto. O <xref:System.DateTime.Parse%2A> e <xref:System.DateTime.TryParse%2A> métodos convertem qualquer uma das várias representações comuns de data e hora. O <xref:System.DateTime.ParseExact%2A> e <xref:System.DateTime.TryParseExact%2A> métodos convertem uma representação de cadeia de caracteres que está de acordo com o padrão especificado por uma cadeia de formato de data e hora. (Consulte os tópicos sobre [cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) e [cadeias de caracteres de formato de data e hora personalizadas](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).)  
  
 A análise é influenciada pelas propriedades de um provedor de formato que fornece informações como as cadeias de caracteres usadas para separadores de data e hora, além dos nomes dos meses, dias e eras. O provedor de formato é o atual <xref:System.Globalization.DateTimeFormatInfo> objeto, que é fornecido implicitamente pela cultura de segmento atual ou explicitamente pelo <xref:System.IFormatProvider> parâmetro de método de análise. Para o <xref:System.IFormatProvider> parâmetro, especifique um <xref:System.Globalization.CultureInfo> objeto que representa uma cultura, ou um <xref:System.Globalization.DateTimeFormatInfo> objeto.  
  
 A representação de cadeia de caracteres de uma data a ser analisada deve incluir o mês e, pelo menos, um dia ou ano. A representação de cadeia de caracteres de um horário deve incluir a hora e, pelo menos, os minutos ou o designador AM/PM. No entanto, análise fornece valores padrão para componentes omitidos, se possível. O padrão de data ausente é a data atual; o padrão de ano ausente é o ano atual; o padrão de dia do mês ausente é o primeiro dia do mês; o padrão de horário ausente é meia-noite.  
  
 Se a representação de cadeia de caracteres especifica somente um horário, a análise retorna um <xref:System.DateTime> do objeto com seu <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A>, e <xref:System.DateTime.Day%2A> propriedades definidas para os valores correspondentes a <xref:System.DateTime.Today%2A> propriedade. No entanto, se o <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> constante for especificada no método de análise resultante de ano, mês e dia propriedades são definidas para o valor `1`.  
  
 Além de um componente de data e hora, a representação de cadeia de caracteres de data e hora pode incluir um deslocamento que indique a diferença de tempo em relação ao UTC (Tempo Universal Coordenado). Por exemplo, a cadeia de caracteres “2/14/2007 5:32:00 -7:00” define um horário sete horas antes do UTC. Se um deslocamento é omitido da representação de cadeia de caracteres de um tempo, a análise retorna um <xref:System.DateTime> do objeto com seu <xref:System.DateTime.Kind%2A> propriedade definida como <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Se um deslocamento for especificado, a análise retorna um <xref:System.DateTime> do objeto com seu <xref:System.DateTime.Kind%2A> propriedade definida como <xref:System.DateTimeKind.Local> e seu valor é ajustado para o fuso horário local do seu computador. Você pode modificar esse comportamento usando um <xref:System.Globalization.DateTimeStyles> constante com o método de análise.  
  
 O provedor de formato também é usado para interpretar uma data numérica ambígua. Por exemplo, não está claro quais componentes da data representada pela cadeia de caracteres “02/03/04” são o mês, o dia e o ano. Nesse caso, os componentes são interpretados de acordo com a ordem dos formatos de data semelhantes no provedor de formato.  
  
## <a name="parse"></a>Parse  
 O exemplo de código a seguir ilustra o uso do **analisar** método para converter uma cadeia de caracteres em uma **DateTime**. Este exemplo usa a cultura associada com o thread atual para realizar a análise. Se o <xref:System.Globalization.CultureInfo> associado atual cultura não é possível analisar a cadeia de caracteres de entrada, um <xref:System.FormatException> é gerada.  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 Você também pode especificar um **CultureInfo** definido como uma das culturas definidas por esse objeto, ou você pode especificar um padrão <xref:System.Globalization.DateTimeFormatInfo> objetos retornados pelo <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriedade. O exemplo de código a seguir usa um provedor de formato para analisar uma cadeia de caracteres alemão em uma **DateTime**. Um **CultureInfo** que representa a cultura de-DE é definido e transmitido com a cadeia de caracteres que está sendo analisada para garantir o sucesso da análise dessa cadeia de caracteres específica. Isso impede qualquer configuração que está na **CurrentCulture** do **CurrentThread**.  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 No entanto, embora você possa usar sobrecargas do <xref:System.DateTime.Parse%2A> método para especificar provedores de formato personalizado, o método não oferece suporte para o uso de provedores de formato não padrão. Para analisar uma data e hora expressada em um formato diferente do padrão, use o <xref:System.DateTime.ParseExact%2A> método em vez disso.  
  
 O seguinte exemplo de código usa o <xref:System.Globalization.DateTimeStyles> enumeração para especificar que as informações de data e hora atuais não devem ser adicionadas para o **DateTime** para os campos que não define a cadeia de caracteres.  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 O <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> método converte uma cadeia de caracteres que está de acordo com um padrão de cadeia de caracteres especificada para um **DateTime** objeto. Quando uma cadeia de caracteres que não é do formulário especificado é passada para este método, uma <xref:System.FormatException> é gerada. Você pode especificar um dos especificadores de formato de data e hora padrão ou uma combinação limitada dos especificadores de formato de data e hora personalizados. Usando os especificadores de formato personalizados, é possível construir uma cadeia de caracteres de reconhecimento personalizada. Para ver uma explicação dos especificadores, consulte os tópicos [cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) e [cadeias de caracteres de formato de data e hora personalizadas](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).  
  
 Cada sobrecarga do <xref:System.DateTime.ParseExact%2A> método também tem um <xref:System.IFormatProvider> parâmetro que normalmente fornece informações específicas da cultura sobre a formatação da cadeia de caracteres. Normalmente, isso <xref:System.IFormatProvider> objeto é um <xref:System.Globalization.CultureInfo> objeto que representa uma cultura padrão ou um <xref:System.Globalization.DateTimeFormatInfo> objeto que é retornado pelo <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> propriedade. No entanto, ao contrário de outros data e hora, funções de análise, esse método também oferece suporte a um <xref:System.IFormatProvider> que define um formato de hora e data não padrão.  
  
 No exemplo de código a seguir, o **ParseExact** método é passado um objeto de cadeia de caracteres para analisar, seguido por um especificador de formato, seguido por um **CultureInfo** objeto. Isso **ParseExact** método só é possível analisar cadeias de caracteres que apresentam o padrão de data por extenso da cultura en-US.  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Análise de cadeias de caracteres](../../../docs/standard/base-types/parsing-strings.md)  
 [Formatando Tipos](../../../docs/standard/base-types/formatting-types.md)  
 [Conversão de tipo no .NET](../../../docs/standard/base-types/type-conversion.md)
