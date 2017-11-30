---
title: "Analisando cadeias de caracteres numéricas no .NET"
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
- parsing strings, numeric strings
- numeric strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
ms.assetid: e39324ee-72e5-42d4-a80d-bf3ee7fc6c59
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c9bb58b0d7b45ca197653742844be01ac3bbe41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-numeric-strings-in-net"></a>Analisando cadeias de caracteres numéricas no NET
Todos os tipos numéricos têm dois métodos de análise estáticos, `Parse` e `TryParse`, que podem ser usados para converter a representação de cadeia de caracteres de um número em um tipo numérico. Esses métodos permitem analisar cadeias de caracteres que foram produzidas usando as cadeias de caracteres de formato documentadas em [Cadeias de caracteres de formato numérico padrão](../../../docs/standard/base-types/standard-numeric-format-strings.md) e [Cadeias de caracteres de formato numérico personalizadas](../../../docs/standard/base-types/custom-numeric-format-strings.md). Por padrão, os métodos `Parse` e `TryParse` conseguem converter cadeias de caracteres que contêm dígitos decimais integrais somente em valores inteiros. Podem converter cadeias de caracteres que contêm dígitos decimais integrais e dígitos fracionários, separadores de grupo e um separador decimal em valores de ponto flutuante. O método `Parse` lança uma exceção se a operação falhar, enquanto o método `TryParse` retorna `false`.  
  
## <a name="parsing-and-format-providers"></a>Provedores de análise e formato  
 Normalmente, as representações de cadeia de caracteres de valores numéricos diferem por cultura. Elementos de separadores de cadeias de caracteres numéricas, como símbolos de moeda, separadores de grupo (ou milhares) e separadores decimais, variam por cultura. Os métodos de análise usam, implícita ou explicitamente, um provedor de formato que reconhece essas variações específicas da cultura. Se nenhum provedor de formato é especificado em uma chamada para o `Parse` ou `TryParse` método, o provedor de formato associado com a cultura do thread atual (o <xref:System.Globalization.NumberFormatInfo> objeto retornado pelo <xref:System.Globalization.NumberFormatInfo.CurrentInfo%2A?displayProperty=nameWithType> propriedade) é usado.  
  
 Um provedor de formato é representado por um <xref:System.IFormatProvider> implementação. Essa interface possui um único membro, o <xref:System.IFormatProvider.GetFormat%2A> método, cujo único parâmetro é um <xref:System.Type> objeto que representa o tipo a ser formatado. Esse método retorna um objeto que fornece informações de formatação. .NET oferece suporte a dois <xref:System.IFormatProvider> implementações para analisar cadeias de caracteres numéricas:  
  
-   Um <xref:System.Globalization.CultureInfo> do objeto cuja <xref:System.Globalization.CultureInfo.GetFormat%2A?displayProperty=nameWithType> método retorna um <xref:System.Globalization.NumberFormatInfo> objeto que fornece informações de formatação específica da cultura.  
  
-   Um <xref:System.Globalization.NumberFormatInfo> do objeto cuja <xref:System.Globalization.NumberFormatInfo.GetFormat%2A?displayProperty=nameWithType> método retorna ele mesmo.  
  
 O exemplo a seguir tenta converter cada cadeia de caracteres em uma matriz para um <xref:System.Double> valor. Em primeiro lugar, tenta analisar a cadeia de caracteres usando um provedor de formato que reflete as convenções da cultura do inglês (Estados Unidos). Se essa operação gera um <xref:System.FormatException>, ele tenta analisar a cadeia de caracteres usando um provedor de formato que reflete as convenções da cultura Francês (França).  
  
 [!code-csharp[Parsing.Numbers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/formatproviders1.cs#1)]
 [!code-vb[Parsing.Numbers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/formatproviders1.vb#1)]  
  
## <a name="parsing-and-numberstyles-values"></a>Análise e valores NumberStyles  
 Os elementos de estilo (como o espaço em branco, separadores de grupo e separador decimal) que pode manipular a operação de análise são definidos por um <xref:System.Globalization.NumberStyles> valor de enumeração. Por padrão, as cadeias de caracteres que representam valores inteiros são analisadas usando o <xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType> valor, que permite apenas dígitos numéricos, espaço em branco à esquerda e à direita e um sinal. Cadeias de caracteres que representam os valores de ponto flutuante são analisadas usando uma combinação da <xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType> e <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> valores; esse estilo composto permite casas decimais junto com à esquerda e à direita de espaço em branco, um sinal, um separador decimal, um grupo separador e um expoente. Chamando uma sobrecarga de `Parse` ou `TryParse` método que inclui um parâmetro de tipo <xref:System.Globalization.NumberStyles> e configuração de um ou mais <xref:System.Globalization.NumberStyles> sinalizadores, você pode controlar os elementos de estilo que podem estar presentes na cadeia de caracteres para a operação de análise êxito.  
  
 Por exemplo, uma cadeia de caracteres que contém um separador de grupo não pode ser convertida para um <xref:System.Int32> valor usando o <xref:System.Int32.Parse%28System.String%29?displayProperty=nameWithType> método. No entanto, a conversão for bem-sucedida se você usar o <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> sinalizador, como mostra o exemplo a seguir.  
  
 [!code-csharp[Parsing.Numbers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/styles1.cs#2)]
 [!code-vb[Parsing.Numbers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/styles1.vb#2)]  
  
> [!WARNING]
>  A operação de análise sempre usa as convenções de formatação de uma determinada cultura. Se você não especificar uma cultura passando um <xref:System.Globalization.CultureInfo> ou <xref:System.Globalization.NumberFormatInfo> do objeto, a cultura associada com o segmento atual é usada.  
  
 A tabela a seguir lista os membros do <xref:System.Globalization.NumberStyles> enumeração e descreve o efeito que elas têm sobre a operação de análise.  
  
|Valor NumberStyles|Efeito sobre a cadeia de caracteres a ser analisada|  
|------------------------|---------------------------------------|  
|<xref:System.Globalization.NumberStyles.None?displayProperty=nameWithType>|São permitidos apenas dígitos numéricos.|  
|<xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>|O separador decimal e dígitos fracionários são permitidos. Para valores inteiros, apenas zero é permitido como um dígito fracionário. Separadores decimais válidos são determinados pelo <xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A?displayProperty=nameWithType> ou <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A?displayProperty=nameWithType> propriedade.|  
|<xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType>|O caractere “e” ou “E” pode ser usado para indicar notação exponencial. Consulte <xref:System.Globalization.NumberStyles> para obter informações adicionais.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>|É permitido um espaço em branco à esquerda.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>|É permitido um espaço em branco à direita.|  
|<xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>|Um sinal positivo ou negativo pode anteceder dígitos numéricos.|  
|<xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>|Um sinal positivo ou negativo pode seguir dígitos numéricos.|  
|<xref:System.Globalization.NumberStyles.AllowParentheses?displayProperty=nameWithType>|Parênteses podem ser usados para indicar valores negativos.|  
|<xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType>|É permitido um separador de grupo. O caractere separador de grupo é determinado pelo <xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A?displayProperty=nameWithType> ou <xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A?displayProperty=nameWithType> propriedade.|  
|<xref:System.Globalization.NumberStyles.AllowCurrencySymbol?displayProperty=nameWithType>|É permitido o símbolo de moeda. O símbolo de moeda é definido pelo <xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A?displayProperty=nameWithType> propriedade.|  
|<xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>|A cadeia de caracteres a ser analisada é interpretada como um número hexadecimal. Pode incluir os dígitos decimais 0-9, A-F e a-f. Este sinalizador pode ser usado apenas para analisar valores inteiros.|  
  
 Além disso, o <xref:System.Globalization.NumberStyles> enumeração fornece os seguintes estilos compostos, que incluem vários <xref:System.Globalization.NumberStyles> sinalizadores.  
  
|Valor NumberStyles de composição|Inclui membros|  
|----------------------------------|----------------------|  
|<xref:System.Globalization.NumberStyles.Integer?displayProperty=nameWithType>|Inclui o <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, e <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType> estilos. É o estilo padrão usado para analisar valores inteiros.|  
|<xref:System.Globalization.NumberStyles.Number?displayProperty=nameWithType>|Inclui o <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, e <xref:System.Globalization.NumberStyles.AllowThousands?displayProperty=nameWithType> estilos.|  
|<xref:System.Globalization.NumberStyles.Float?displayProperty=nameWithType>|Inclui o <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowLeadingSign?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowDecimalPoint?displayProperty=nameWithType>, e <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> estilos.|  
|<xref:System.Globalization.NumberStyles.Currency?displayProperty=nameWithType>|Inclui todos os estilos exceto <xref:System.Globalization.NumberStyles.AllowExponent?displayProperty=nameWithType> e <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.Any?displayProperty=nameWithType>|Inclui todos os estilos exceto <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType>.|  
|<xref:System.Globalization.NumberStyles.HexNumber?displayProperty=nameWithType>|Inclui o <xref:System.Globalization.NumberStyles.AllowLeadingWhite?displayProperty=nameWithType>, <xref:System.Globalization.NumberStyles.AllowTrailingWhite?displayProperty=nameWithType>, e <xref:System.Globalization.NumberStyles.AllowHexSpecifier?displayProperty=nameWithType> estilos.|  
  
## <a name="parsing-and-unicode-digits"></a>Análise e dígitos Unicode  
 O padrão Unicode define pontos de código para dígitos em diversos sistemas de escrita. Por exemplo, os pontos de código de U+0030 a U+0039 representam os dígitos latinos básicos 0 a 9; os pontos de código de U+09E6 a U+09EF representam os dígitos bengali de 0 a 9; e os pontos de código de U+FF10 a U+FF19 representam os dígitos de largura inteira 0 a 9. No entanto, os únicos dígitos numéricos reconhecidos pelos métodos de análise são os dígitos latinos básicos 0-9 com os pontos de código de U+0030 a U+0039. Se um numérico análise do método é passado a uma cadeia de caracteres que contém os outros dígitos, o método gera uma <xref:System.FormatException>.  
  
 O exemplo a seguir usa o <xref:System.Int32.Parse%2A?displayProperty=nameWithType> método para analisar cadeias de caracteres que consistem em dígitos em diferentes sistemas de escrita. Como mostra a saída do exemplo, a tentativa de analisar os dígitos latinos básicos é bem-sucedida, mas a tentativa de analisar os dígitos de largura inteira, indo-arábicos e bengali.  
  
 [!code-csharp[Parsing.Numbers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/parsing.numbers/cs/unicode1.cs#3)]
 [!code-vb[Parsing.Numbers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/parsing.numbers/vb/unicode1.vb#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Globalization.NumberStyles>  
 [Análise de cadeias de caracteres](../../../docs/standard/base-types/parsing-strings.md)  
 [Formatando Tipos](../../../docs/standard/base-types/formatting-types.md)
