---
title: Funções de conversão do tipo
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 3924da6ccbfea00668370f2fbcf4baf289be80db
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349963"
---
# <a name="type-conversion-functions-visual-basic"></a>Funções de conversão do tipo (Visual Basic)

Essas funções são compiladas em linha, o que significa que o código de conversão faz parte do código que avalia a expressão. Às vezes, não há nenhuma chamada para um procedimento para realizar a conversão, o que melhora o desempenho. Cada função impõe uma expressão para um tipo de dados específico.

## <a name="syntax"></a>Sintaxe

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a>Parte

`expression`  
Necessário. Qualquer expressão do tipo de dados de origem.

## <a name="return-value-data-type"></a>Tipo de dados de valor de retorno

O nome da função determina o tipo de dados do valor que ele retorna, conforme mostrado na tabela a seguir.

|Nome da função|Tipo de dados de retorno|Intervalo para `expression` argumento|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer `Char` ou expressão numérica ou `String` válida.|
|`CByte`|[Tipo de Dados Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) por meio de <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup><br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho da conversão de ponto flutuante para byte com a função `CByte`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.|
|`CChar`|[Tipo de Dados de Caractere](../../../visual-basic/language-reference/data-types/char-data-type.md)|Qualquer expressão de `Char` ou `String` válida; somente o primeiro caractere de um `String` é convertido; o valor pode ser de 0 a 65535 (não assinado).|
|`CDate`|[Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|Qualquer representação válida de uma data e hora.|
|`CDbl`|[Tipo de Dados Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570 e + 308 a-4.94065645841246544 E-324 para valores negativos; 4.94065645841246544 e-324 a 1.79769313486231570 E + 308 para valores positivos.|
|`CDec`|[Tipo de Dados Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79228162514264337593543950335 para números com escala zero, ou seja, números sem casas decimais. Para números com 28 casas decimais, o intervalo é +/-7.9228162514264337593543950335. O menor número não zero possível é 0, 1 (+/-1E-28).|
|`CInt`|[Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648) por meio de <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); as partes fracionárias são arredondadas. <sup>1</sup> <br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho da conversão de ponto flutuante para inteiro com a função `CInt`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo. |
|`CLng`|[Tipo de Dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9.223.372.036.854.775.808) por meio de <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); as partes fracionárias são arredondadas. <sup>1</sup><br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiros de 64 bits com a função `CLng`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.|
|`CObj`|[Tipo de Dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer expressão válida.|
|`CSByte`|[Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) por meio de <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); as partes fracionárias são arredondadas. <sup>1</sup><br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho do ponto flutuante para conversão de bytes assinados com a função `CSByte`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.|
|`CShort`|[Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768) por meio de <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); as partes fracionárias são arredondadas. <sup>1</sup><br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiros de 16 bits com a função `CShort`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.|
|`CSng`|[Tipo de Dados Simples](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + 38 a-1.401298 E-45 para valores negativos; 1.401298 e-45 a 3.402823 E + 38 para valores positivos.|
|`CStr`|[Tipo de Dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)|Retorna para `CStr` dependem do argumento `expression`. Confira [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|
|`CUInt`|[Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) por meio de <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup><br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho do ponto flutuante para conversão de inteiros sem sinal com a função `CUInt`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.|
|`CULng`|[Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) a <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup><br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro longo sem sinal com a função `CULng`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.|
|`CUShort`|[Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) por meio de <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (não assinado); as partes fracionárias são arredondadas. <sup>1</sup><br/><br/>A partir do Visual Basic 15,8, Visual Basic otimiza o desempenho do ponto flutuante para conversão de inteiros de 16 bits sem sinal com a função `CUShort`; consulte a seção [comentários](#remarks) para obter mais informações. Consulte a seção [exemplo de CInt](#cint-example) para obter um exemplo.|

<sup>1</sup> partes fracionárias podem estar sujeitas a um tipo especial de arredondamento chamado de *arredondamento do Banker*. Consulte "Comentários" para obter mais informações.

## <a name="remarks"></a>Comentários

Como regra, você deve usar as funções de conversão de tipo Visual Basic em preferência aos métodos .NET Framework como `ToString()`, seja na classe <xref:System.Convert> ou em uma estrutura ou classe de tipo individual. As funções de Visual Basic são projetadas para uma interação ideal com código de Visual Basic e também tornam seu código-fonte mais curto e mais fácil de ler. Além disso, os métodos de conversão de .NET Framework nem sempre produzem os mesmos resultados que as funções de Visual Basic, por exemplo, ao converter `Boolean` em `Integer`. Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).

A partir do Visual Basic 15,8, o desempenho da conversão de ponto-a-inteiro flutuante é otimizado quando você passa o <xref:System.Single> ou <xref:System.Double> valor retornado pelos métodos a seguir para uma das funções de conversão de inteiro (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Essa otimização permite que um código que faz um grande número de conversões de inteiros seja executado até duas vezes mais rápido. O exemplo a seguir ilustra essas conversões otimizadas de ponto flutuante para inteiro:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>Comportamento

- **Coerção.** Em geral, você pode usar as funções de conversão de tipo de dados para forçar o resultado de uma operação para um tipo de dados específico em vez do tipo de dados padrão. Por exemplo, use `CDec` para forçar aritmética decimal nos casos em que a precisão única, a precisão dupla ou a aritmética de inteiro normalmente ocorreria.

- **Conversões com falha.** Se o `expression` passado para a função estiver fora do intervalo do tipo de dados para o qual será convertido, ocorrerá uma <xref:System.OverflowException>.

- **Partes fracionárias.** Quando você converte um valor não integral em um tipo integral, as funções de conversão de inteiro (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`e `CUShort`) removem a parte fracionária e arredondam o valor para o número inteiro mais próximo.

     Se a parte fracionária for exatamente 0,5, as funções de conversão de inteiros o arredondarão para o inteiro par mais próximo. Por exemplo, 0,5 arredonda para 0 e 1,5 e 2,5 são arredondados para 2. Isso às vezes é chamado de *arredondamento do Banker*, e sua finalidade é compensar uma tendência que poderia se acumular ao adicionar muitos desses números juntos.

     `CInt` e `CLng` diferem das funções <xref:Microsoft.VisualBasic.Conversion.Int%2A> e <xref:Microsoft.VisualBasic.Conversion.Fix%2A>, que truncam, em vez de arredondar, a parte fracionária de um número. Além disso, `Fix` e `Int` sempre retornam um valor do mesmo tipo de dados que você passa.

- **Conversões de data/hora.** Use a função <xref:Microsoft.VisualBasic.Information.IsDate%2A> para determinar se um valor pode ser convertido em uma data e hora. `CDate` reconhece literais de data e literais de tempo, mas não valores numéricos. Para converter um valor de `Date` Visual Basic 6,0 em um valor `Date` no Visual Basic 2005 ou em versões posteriores, você pode usar o método <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>.

- **Valores de data/hora neutros.** O [tipo de dados Date](../../../visual-basic/language-reference/data-types/date-data-type.md) sempre contém informações de data e hora. Para fins de conversão de tipo, Visual Basic considera 1/1/0001 (1º de Janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) para ser um valor neutro para o tempo. Se você converter um valor de `Date` em uma cadeia de caracteres, `CStr` não incluirá valores neutros na cadeia de caracteres resultante. Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas. No entanto, as informações de data ainda estão presentes no valor de `Date` original e podem ser recuperadas com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> função.

- **Sensibilidade de cultura.** As funções de conversão de tipo que envolvem cadeias de caracteres executam conversões com base nas configurações de cultura atuais para o aplicativo. Por exemplo, `CDate` reconhece formatos de data de acordo com a configuração de localidade do seu sistema. Você deve fornecer o dia, o mês e o ano na ordem correta para sua localidade, ou a data pode não ser interpretada corretamente. Um formato de data por extenso não será reconhecido se ele contiver uma cadeia de caracteres de dia da semana, como "quarta-feira".

     Se você precisar converter de ou para uma representação de cadeia de caracteres de um valor em um formato diferente daquele especificado por sua localidade, não será possível usar as funções de conversão de tipo Visual Basic. Para fazer isso, use os métodos `ToString(IFormatProvider)` e `Parse(String, IFormatProvider)` do tipo desse valor. Por exemplo, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> ao converter uma cadeia de caracteres em um `Double`e use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` em uma cadeia de caracteres.

## <a name="ctype-function"></a>Função CType

A [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) usa um segundo argumento, `typename`e impõe `expression` para `typename`, em que `typename` pode ser qualquer tipo de dados, estrutura, classe ou interface para o qual exista uma conversão válida.

Para obter uma comparação de `CType` com as outras palavras-chave de conversão de tipo, consulte operador [DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) e [Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).

## <a name="cbool-example"></a>Exemplo de CBool

O exemplo a seguir usa a função `CBool` para converter expressões em valores `Boolean`. Se uma expressão for avaliada como um valor diferente de zero, `CBool` retornará `True`; caso contrário, ele retornará `False`.

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a>Exemplo de CByte

O exemplo a seguir usa a função `CByte` para converter uma expressão em um `Byte`.

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a>Exemplo de CChar

O exemplo a seguir usa a função `CChar` para converter o primeiro caractere de uma expressão de `String` para um tipo de `Char`.

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

O argumento de entrada para `CChar` deve ser do tipo de dados `Char` ou `String`. Você não pode usar `CChar` para converter um número em um caractere, porque `CChar` não pode aceitar um tipo de dados numérico. O exemplo a seguir obtém um número que representa um ponto de código (código de caractere) e o converte no caractere correspondente. Ele usa a função <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> para obter a cadeia de caracteres de dígitos, `CInt` para converter a cadeia de caracteres para o tipo `Integer`e `ChrW` para converter o número em `Char`de tipo.

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a>Exemplo de CDate

O exemplo a seguir usa a função `CDate` para converter cadeias de caracteres em valores `Date`. Em geral, as datas e as horas de codificação rígida como cadeias de caracteres (como mostrado neste exemplo) não são recomendadas. Use literais de data e literais de tempo, como #Feb 12, 1969 # e #4:45:23 PM #, em vez disso.

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a>Exemplo de CDbl

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a>Exemplo de CDec

O exemplo a seguir usa a função `CDec` para converter um valor numérico em `Decimal`.

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a>Exemplo de CInt

O exemplo a seguir usa a função `CInt` para converter um valor em `Integer`.

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a>Exemplo de CLng

O exemplo a seguir usa a função `CLng` para converter valores em `Long`.

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a>Exemplo de CObj

O exemplo a seguir usa a função `CObj` para converter um valor numérico em `Object`. A variável `Object` em si contém apenas um ponteiro de quatro bytes, que aponta para o valor `Double` atribuído a ela.

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a>Exemplo de CSByte

O exemplo a seguir usa a função `CSByte` para converter um valor numérico em `SByte`.

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a>Exemplo de CShort

O exemplo a seguir usa a função `CShort` para converter um valor numérico em `Short`.

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a>Exemplo de CSng

O exemplo a seguir usa a função `CSng` para converter valores em `Single`.

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a>Exemplo de CStr

O exemplo a seguir usa a função `CStr` para converter um valor numérico em `String`.

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

O exemplo a seguir usa a função `CStr` para converter valores de `Date` em valores `String`.

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

`CStr` sempre renderiza um valor de `Date` no formato curto padrão para a localidade atual, por exemplo, "6/15/2003 4:35:47 PM". No entanto, `CStr` suprime os *valores neutros* de 1/1/0001 para a data e 00:00:00 para a hora.

Para obter mais detalhes sobre os valores retornados por `CStr`, consulte [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).

## <a name="cuint-example"></a>Exemplo de CUInt

O exemplo a seguir usa a função `CUInt` para converter um valor numérico em `UInteger`.

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a>Exemplo de CULng

O exemplo a seguir usa a função `CULng` para converter um valor numérico em `ULong`.

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a>Exemplo de CUShort

O exemplo a seguir usa a função `CUShort` para converter um valor numérico em `UShort`.

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Funções de Conversão](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
