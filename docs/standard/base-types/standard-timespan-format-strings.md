---
title: Cadeias de caracteres de formato TimeSpan padrão
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, standard time interval
- format strings
- standard time interval format strings
- standard format strings, time intervals
- format specifiers, time intervals
- time intervals [.NET Framework], formatting
- time [.NET Framework], formatting
- formatting [.NET Framework], time
- standard TimeSpan format strings
- formatting [.NET Framework], time intervals
ms.assetid: 9f6c95eb-63ae-4dcc-9c32-f81985c75794
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc2ca7a94ffb19f62f354bdfc3040490b57e2689
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968544"
---
# <a name="standard-timespan-format-strings"></a>Cadeias de caracteres de formato TimeSpan padrão
<a name="Top"></a> Uma cadeia de caracteres de formato padrão <xref:System.TimeSpan> usa um único especificador de formato para definir a representação de texto de um valor <xref:System.TimeSpan> que resulta de uma operação de formatação. Qualquer sequência de formato que contenha mais de um caractere, incluindo espaço em branco, é interpretada como uma sequência de formato <xref:System.TimeSpan> personalizada. Para saber mais, confira [Cadeias de caracteres de formato TimeSpan personalizadas](../../../docs/standard/base-types/custom-timespan-format-strings.md).  
  
 As representações de sequência de valores <xref:System.TimeSpan> são produzidas por chamadas para as sobrecargas do método <xref:System.TimeSpan.ToString%2A?displayProperty=nameWithType>, bem como por métodos que oferecem suporte à formatação composta, como <xref:System.String.Format%2A?displayProperty=nameWithType>. Para obter mais informações, consulte [Tipos de formatação](../../../docs/standard/base-types/formatting-types.md) e [Formatação de composição](../../../docs/standard/base-types/composite-formatting.md). O exemplo a seguir ilustra o uso de sequências de formato padrão em operações de formatação.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/formatexample1.cs#2)]
 [!code-vb[Conceptual.TimeSpan.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/formatexample1.vb#2)]  
  
 As sequências de formato <xref:System.TimeSpan> padrão são usadas também pelos métodos <xref:System.TimeSpan.ParseExact%2A?displayProperty=nameWithType> e <xref:System.TimeSpan.TryParseExact%2A?displayProperty=nameWithType> para definir o formato necessário de sequências de caracteres de entrada para análise de operações. (A análise converte a representação de sequência de um valor para esse valor). O exemplo a seguir ilustra o uso de sequências de formato padrão em operações de análise.  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/parseexample1.cs#3)]
 [!code-vb[Conceptual.TimeSpan.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/parseexample1.vb#3)]  
  
<a name="top"></a> A tabela a seguir lista os especificadores de formato de intervalo de tempo padrão.  
  
|Especificador de formato|Nome|DESCRIÇÃO|Exemplos|  
|----------------------|----------|-----------------|--------------|  
|"c"|Formato de constante (invariável)|Esse especificador não é sensível à cultura. Ele assume o formato `[-][d'.']hh':'mm':'ss['.'fffffff]`.<br /><br /> (As sequências de formato "t" e "T" produzem os mesmos resultados).<br /><br /> Para saber mais: [O especificador de formato de constante ("c")](#Constant).|`TimeSpan.Zero` -> 00:00:00<br /><br /> `New TimeSpan(0, 0, 30, 0)` -> 00:30:00<br /><br /> `New TimeSpan(3, 17, 25, 30, 500)` -> 3.17:25:30.5000000|  
|"g"|Formato curto geral|Esse especificador gera apenas o que é necessário. Ele é sensível à cultura e assume o formato `[-][d':']h':'mm':'ss[.FFFFFFF]`.<br /><br /> Para saber mais: [O especificador de formato curto geral ("g")](#GeneralShort).|`New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50.5 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 500)` -> 1:3:16:50,5 (fr-FR)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:50.599 (en-US)<br /><br /> `New TimeSpan(1, 3, 16, 50, 599)` -> 1:3:16:50,599 (fr-FR)|  
|"G"|Formato longo geral|Esse especificador sempre gera dias e sete dígitos de fração. Ele é sensível à cultura e assume o formato `[-]d':'hh':'mm':'ss.fffffff`.<br /><br /> Para saber mais: [O especificador de formato longo geral ("G")](#GeneralLong).|`New TimeSpan(18, 30, 0)` -> 0:18:30:00.0000000 (en-US)<br /><br /> `New TimeSpan(18, 30, 0)` -> 0:18:30:00,0000000 (fr-FR)|  
  
<a name="Constant"></a>   
## <a name="the-constant-c-format-specifier"></a>O especificador de formato de constante ("c")  
 O especificador de formato "c" retorna a representação de sequência de um valor <xref:System.TimeSpan> da seguinte forma:  
  
 [-][*d*.]*hh*:*mm*:*ss*[.*fffffff*]  
  
 Os elementos entre colchetes ([ e ]) são opcionais. O ponto (.) e os dois pontos (:) são símbolos literais. A tabela a seguir descreve os elementos restantes.  
  
|Elemento|DESCRIÇÃO|  
|-------------|-----------------|  
|*-*|Um sinal negativo opcional, que indica um intervalo de tempo negativo.|  
|*d*|O número opcional de dias, sem zeros à esquerda.|  
|*hh*|O número de horas, que varia de "00" a "23".|  
|*mm*|O número de minutos, que varia de "00" a "59".|  
|*ss*|O número de segundos, que varia de "00" a "59".|  
|*fffffff*|A parte de fração opcional de um segundo.  Seu valor pode variar de "0000001" (um pulso ou um décimo milionésimo de segundo) até "9999999" (9.999.999 dez milionésimos de segundo ou um segundo menos um pulso).|  
  
 Ao contrário dos especificadores de formato de "g" e "G", o especificador de formato "c" não é sensível à cultura. Ele produz a representação de cadeia de caracteres de um valor <xref:System.TimeSpan> que é invariável e é comum a todas as versões anteriores do .NET Framework, antes do .NET Framework 4. "c"é a cadeia de caracteres de formato <xref:System.TimeSpan> padrão, o método <xref:System.TimeSpan.ToString?displayProperty=nameWithType> formata um valor de intervalo de tempo usando a sequência de formato "c".  
  
> [!NOTE]
> <xref:System.TimeSpan> também oferece suporte às sequências de formato padrão "t" e "T", que são idênticas em comportamento à sequência de formato padrão "c".  
  
 O exemplo a seguir instancia dois objetos <xref:System.TimeSpan>, usa-os para executar operações aritméticas e exibe o resultado. Em cada caso, ele usa formatação composta para exibir o valor <xref:System.TimeSpan> usando o especificador de formato "c".  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardc1.cs#1)]
 [!code-vb[Conceptual.TimeSpan.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardc1.vb#1)]  
  
 [Voltar à tabela](#Top)  
  
<a name="GeneralShort"></a>   
## <a name="the-general-short-g-format-specifier"></a>O especificador de formato curto geral ("g")  
 O especificador de formato <xref:System.TimeSpan> de "g" retorna a representação de sequência de um valor <xref:System.TimeSpan> em um formato compacto, incluindo apenas os elementos que são necessários. Ele tem o seguinte formato:  
  
 [-][*d*:]*h*:*mm*:*ss*[.*FFFFFFF*]  
  
 Os elementos entre colchetes ([ e ]) são opcionais. Os dois pontos (:) são um símbolo literal. A tabela a seguir descreve os elementos restantes.  
  
|Elemento|DESCRIÇÃO|  
|-------------|-----------------|  
|*-*|Um sinal negativo opcional, que indica um intervalo de tempo negativo.|  
|*d*|O número opcional de dias, sem zeros à esquerda.|  
|*h*|O número de horas, que varia de "0" a "23", sem zeros à esquerda.|  
|*mm*|O número de minutos, que varia de "00" a "59".|  
|*ss*|O número de minutos, que varia de "00" a "59".|  
|*.*|O separador de fração de segundo. É equivalente à propriedade <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> da cultura especificada sem substituições pelo usuário.|  
|*FFFFFFF*|As frações de segundo. Uma vez que é exibido o mínimo de dígitos possível.|  
  
 Como o especificador de formato "G", o especificador de formato "g" é localizado. Seu separador de fração de segundo se baseia na cultura atual ou de uma propriedade <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> da cultura especificada.  
  
 O exemplo a seguir instancia dois objetos <xref:System.TimeSpan>, usa-os para executar operações aritméticas e exibe o resultado. Em cada caso, ele usa formatação composta para exibir o valor <xref:System.TimeSpan> usando o especificador de formato "g". Além disso, ele formata o valor <xref:System.TimeSpan> usando as convenções de formatação da cultura atual do sistema (que, nesse caso, é Inglês - Estados Unidos ou en-US) e da cultura francês - França (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardshort1.cs#4)]
 [!code-vb[Conceptual.TimeSpan.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardshort1.vb#4)]  
  
 [Voltar à tabela](#Top)  
  
<a name="GeneralLong"></a>   
## <a name="the-general-long-g-format-specifier"></a>O especificador de formato longo geral ("G")  
 O especificador de formato <xref:System.TimeSpan> de "G" retorna a representação de sequência de um valor <xref:System.TimeSpan> em um formato longo que sempre inclui dias e a fração de segundo. A sequência que resulta do especificador de formato padrão "G" tem o seguinte formato:  
  
 [-]*d*:*hh*:*mm*:*ss*.*fffffff*  
  
 Os elementos entre colchetes ([ e ]) são opcionais. Os dois pontos (:) são um símbolo literal. A tabela a seguir descreve os elementos restantes.  
  
|Elemento|DESCRIÇÃO|  
|-------------|-----------------|  
|*-*|Um sinal negativo opcional, que indica um intervalo de tempo negativo.|  
|*d*|O número de dias, sem zeros à esquerda.|  
|*hh*|O número de horas, que varia de "00" a "23".|  
|*mm*|O número de minutos, que varia de "00" a "59".|  
|*ss*|O número de segundos, que varia de "00" a "59".|  
|*.*|O separador de fração de segundo. É equivalente à propriedade <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> da cultura especificada sem substituições pelo usuário.|  
|*fffffff*|As frações de segundo.|  
  
 Como o especificador de formato "G", o especificador de formato "g" é localizado. Seu separador de fração de segundo se baseia na cultura atual ou de uma propriedade <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A> da cultura especificada.  
  
 O exemplo a seguir instancia dois objetos <xref:System.TimeSpan>, usa-os para executar operações aritméticas e exibe o resultado. Em cada caso, ele usa formatação composta para exibir o valor <xref:System.TimeSpan> usando o especificador de formato "G". Além disso, ele formata o valor <xref:System.TimeSpan> usando as convenções de formatação da cultura atual do sistema (que, nesse caso, é Inglês - Estados Unidos ou en-US) e da cultura francês - França (fr-FR).  
  
 [!code-csharp[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.timespan.standard/cs/standardlong1.cs#5)]
 [!code-vb[Conceptual.TimeSpan.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.timespan.standard/vb/standardlong1.vb#5)]  
  
 [Voltar à tabela](#Top)  
  
## <a name="see-also"></a>Consulte também

- [Formatando Tipos](../../../docs/standard/base-types/formatting-types.md)
- [Cadeias de caracteres de formato TimeSpan personalizado](../../../docs/standard/base-types/custom-timespan-format-strings.md)
- [Análise de cadeias de caracteres](../../../docs/standard/base-types/parsing-strings.md)
