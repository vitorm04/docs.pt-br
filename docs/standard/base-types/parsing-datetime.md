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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6e3ef01abdb615b2850b5a9d07e1208ee22eda95
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="parsing-date-and-time-strings-in-net"></a>Analisando Cadeias de Caracteres de Data e Hora no .NET
Os métodos de análise convertem a representação em cadeia de caracteres de data e hora em um objeto <xref:System.DateTime> equivalente. Os métodos <xref:System.DateTime.Parse%2A> e <xref:System.DateTime.TryParse%2A> convertem qualquer uma das várias representações comuns de data e hora. Os métodos <xref:System.DateTime.ParseExact%2A> e <xref:System.DateTime.TryParseExact%2A> convertem uma representação em cadeia de caracteres que cumpra o padrão especificado por uma cadeia de caracteres de formato de data e hora. (Consulte os tópicos sobre [cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) e [cadeias de caracteres de formato de data e hora personalizadas](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).)  
  
 A análise é influenciada pelas propriedades de um provedor de formato que fornece informações como as cadeias de caracteres usadas para separadores de data e hora, além dos nomes dos meses, dias e eras. O provedor de formato é o objeto <xref:System.Globalization.DateTimeFormatInfo> atual, que é fornecido implicitamente pela cultura de thread atual ou explicitamente pelo parâmetro <xref:System.IFormatProvider> de um método de análise. Para o parâmetro <xref:System.IFormatProvider>, especifique um objeto <xref:System.Globalization.CultureInfo>, o qual representa uma cultura ou um objeto <xref:System.Globalization.DateTimeFormatInfo>.  
  
 A representação de cadeia de caracteres de uma data a ser analisada deve incluir o mês e, pelo menos, um dia ou ano. A representação de cadeia de caracteres de um horário deve incluir a hora e, pelo menos, os minutos ou o designador AM/PM. No entanto, análise fornece valores padrão para componentes omitidos, se possível. O padrão de data ausente é a data atual; o padrão de ano ausente é o ano atual; o padrão de dia do mês ausente é o primeiro dia do mês; o padrão de horário ausente é meia-noite.  
  
 Se a representação de cadeia de caracteres especifica somente um horário, a análise retorna um objeto <xref:System.DateTime> com as propriedades <xref:System.DateTime.Year%2A>, <xref:System.DateTime.Month%2A> e <xref:System.DateTime.Day%2A> definidas para os valores correspondentes da propriedade <xref:System.DateTime.Today%2A>. No entanto, se a constante <xref:System.Globalization.DateTimeStyles.NoCurrentDateDefault> estiver especificada no método de análise, as propriedades resultantes de ano, mês e dia serão definidas com o valor `1`.  
  
 Além de um componente de data e hora, a representação de cadeia de caracteres de data e hora pode incluir um deslocamento que indique a diferença de tempo em relação ao UTC (Tempo Universal Coordenado). Por exemplo, a cadeia de caracteres “2/14/2007 5:32:00 -7:00” define um horário sete horas antes do UTC. Se um deslocamento for omitido da representação de cadeia de caracteres de um horário, a análise retornará um <xref:System.DateTime> do objeto com a propriedade <xref:System.DateTime.Kind%2A> definida como <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>. Se um deslocamento for especificado, a análise retorna um objeto <xref:System.DateTime> com a propriedade <xref:System.DateTime.Kind%2A> definida como <xref:System.DateTimeKind.Local> e seu valor ajustado de acordo com o fuso horário local do seu computador. É possível modificar esse comportamento usando uma constante <xref:System.Globalization.DateTimeStyles> com o método de análise.  
  
 O provedor de formato também é usado para interpretar uma data numérica ambígua. Por exemplo, não está claro quais componentes da data representada pela cadeia de caracteres “02/03/04” são o mês, o dia e o ano. Nesse caso, os componentes são interpretados de acordo com a ordem dos formatos de data semelhantes no provedor de formato.  
  
## <a name="parse"></a>Parse  
 O exemplo de código a seguir ilustra o uso do método **Parse** para converter uma cadeia de caracteres em um **DateTime**. Este exemplo usa a cultura associada com o thread atual para realizar a análise. Se o <xref:System.Globalization.CultureInfo> associado à cultura atual não puder analisar a cadeia de caracteres de entrada, um <xref:System.FormatException> será gerado.  
  
 [!code-csharp[Parsing.DateAndTime#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example.cs#1)]
 [!code-vb[Parsing.DateAndTime#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example.vb#1)]  
  
 Também é possível especificar um **CultureInfo** definido como uma das culturas definidas por tal objeto ou especificar um dos objetos <xref:System.Globalization.DateTimeFormatInfo> padrão retornados pela propriedade <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. O exemplo de código a seguir usa um provedor de formato para analisar uma cadeia de caracteres em alemão em um **DateTime**. Um **CultureInfo** que representa a cultura de-DE é definido e passado com a cadeia de caracteres sendo analisada para assegurar uma análise bem-sucedida dessa cadeia de caracteres específica. Isso impede qualquer configuração que está no **CurrentCulture** de **CurrentThread**.  
  
 [!code-csharp[Parsing.DateAndTime#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example2.cs#2)]
 [!code-vb[Parsing.DateAndTime#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example2.vb#2)]  
  
 No entanto, apesar de ser possível usar sobrecargas do método <xref:System.DateTime.Parse%2A> para especificar os provedores de formato personalizado, o método não dá suporte ao uso de provedores de formato não padrão. Para analisar data e hora expressadas em um formato não padrão, use o método <xref:System.DateTime.ParseExact%2A>.  
  
 O exemplo de código a seguir usa a enumeração <xref:System.Globalization.DateTimeStyles> para especificar que as informações atuais de data e hora não devem ser adicionadas ao **DateTime** para campos que a cadeia de caracteres não define.  
  
 [!code-csharp[Parsing.DateAndTime#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example3.cs#3)]
 [!code-vb[Parsing.DateAndTime#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example3.vb#3)]  
  
## <a name="parseexact"></a>ParseExact  
 O método <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> converte uma cadeia de caracteres que está de acordo com um padrão de cadeia de caracteres especificada em um objeto **DateTime**. Quando uma cadeia de caracteres que não é da forma especificada é passada para esse método, é lançada uma <xref:System.FormatException>. Você pode especificar um dos especificadores de formato de data e hora padrão ou uma combinação limitada dos especificadores de formato de data e hora personalizados. Usando os especificadores de formato personalizados, é possível construir uma cadeia de caracteres de reconhecimento personalizada. Para ver uma explicação dos especificadores, consulte os tópicos [cadeias de caracteres de formato de data e hora padrão](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) e [cadeias de caracteres de formato de data e hora personalizadas](../../../docs/standard/base-types/custom-date-and-time-format-strings.md).  
  
 Cada sobrecarga do método <xref:System.DateTime.ParseExact%2A> também tem um parâmetro <xref:System.IFormatProvider> que normalmente oferece informações específicas da cultura sobre a formatação da cadeia de caracteres. Normalmente, esse objeto <xref:System.IFormatProvider> é um objeto <xref:System.Globalization.CultureInfo> que representa uma cultura padrão ou um objeto <xref:System.Globalization.DateTimeFormatInfo> que é retornado pela propriedade <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType>. Entretanto, ao contrário das outras funções de análise de data e hora, esse método também dá suporte a um <xref:System.IFormatProvider> que define um formato de data e hora não padrão.  
  
 No exemplo de código a seguir, o método **ParseExact** recebe um objeto de cadeia de caracteres para analisar, seguido por um O especificador de formato, seguido por um objeto **CultureInfo**. Esse método **ParseExact** só consegue analisar cadeias de caracteres que exibem o padrão de data por extenso na cultura en-US.  
  
 [!code-csharp[Parsing.DateAndTime#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Parsing.DateAndTime/cs/Example4.cs#4)]
 [!code-vb[Parsing.DateAndTime#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Parsing.DateAndTime/vb/Example4.vb#4)]  
  
## <a name="see-also"></a>Consulte também  
 [Análise de cadeias de caracteres](../../../docs/standard/base-types/parsing-strings.md)  
 [Formatando Tipos](../../../docs/standard/base-types/formatting-types.md)  
 [Conversão de tipo no .NET](../../../docs/standard/base-types/type-conversion.md)
