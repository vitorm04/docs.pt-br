---
title: Funções de conversão do tipo (Visual Basic)
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
ms.openlocfilehash: 56dad921b2900061dbe2db0d8f1faaf759641f87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148129"
---
# <a name="type-conversion-functions-visual-basic"></a>Funções de conversão do tipo (Visual Basic)
Essas funções são compilado embutido, o que significa que o código de conversão faz parte do código que avalia a expressão. Às vezes, não há nenhuma chamada para um procedimento para realizar a conversão, o que melhora o desempenho. Cada função impõe uma expressão para um tipo de dados específico.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
  
## <a name="return-value-data-type"></a>Tipo de dados do valor de retorno  
 O nome da função determina o tipo de dados do valor retornado por ele, conforme mostrado na tabela a seguir.  
  
|Nome da função|Tipo de dados de retorno|Intervalo para `expression` argumento|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer `Char` ou `String` ou expressão numérica.|  
|`CByte`|[Tipo de dados Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) por meio <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup><br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de bytes com o `CByte` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.|  
|`CChar`|[Tipo de dados Char](../../../visual-basic/language-reference/data-types/char-data-type.md)|Qualquer `Char` ou `String` expressão; apenas primeiro caractere de um `String` é convertido; valor pode ser de 0 a 65535 (não assinado).|  
|`CDate`|[Tipo de dados Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|Qualquer representação válida de uma data e hora.|  
|`CDbl`|[Tipo de dados double](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1, 79769313486231570E + 308 a - 4.94065645841246544-324 para valores negativos; 4.94065645841246544-324 1.79769313486231570 + 308 para valores positivos.|  
|`CDec`|[Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+ /-79.228.162.514.264.337.593.543.950.335 para números de escala de zero, ou seja, os números sem casas decimais. Para números com 28 casas decimais, o intervalo é + /-7,9228162514264337593543950335. O menor número possível de diferente de zero é 0,0000000000000000000000000001 (+ /-1E-28).|  
|`CInt`|[Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2.147.483.648) por meio <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2.147.483.647); são arredondados para partes fracionárias.<sup> 1</sup> <br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de número inteiro com o `CInt` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo. |  
|`CLng`|[Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9.223.372.036.854.775.808) por meio <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9.223.372.036.854.775.807); são arredondados para partes fracionárias.<sup> 1</sup><br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro de 64 bits com o `CLng` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.|  
|`CObj`|[Tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer expressão válida.|  
|`CSByte`|[Tipo de dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (de -128) por meio <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); são arredondados para partes fracionárias.<sup> 1</sup><br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de byte assinado com o `CSByte` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.|  
|`CShort`|[Tipo de dados curto](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32.768) por meio <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32.767); são arredondados para partes fracionárias.<sup> 1</sup><br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro de 16 bits com o `CShort` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.|  
|`CSng`|[Tipo de dados único](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3,402823e+38 - 1,401298E-45 para valores negativos; 1,401298E-45 a 3,402823e+38 para valores positivos.|  
|`CStr`|[Tipo de dados da cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md)|Retorna para `CStr` dependem do `expression` argumento. Ver [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) por meio <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4.294.967.295) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup><br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro sem sinal com o `CUInt` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.|  
|`CULng`|[Tipo de dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) por meio <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18.446.744.073.709.551.615) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup><br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro longo sem sinal com o `CULng` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.|  
|`CUShort`|[Tipo de dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) por meio <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65.535) (não assinado); são arredondados para partes fracionárias.<sup> 1</sup><br/><br/>Começando com 15,8 do Visual Basic, Visual Basic otimiza o desempenho de ponto flutuante para conversão de inteiro sem sinal de 16 bits com o `CUShort` função; consulte a [comentários](#remarks) seção para obter mais informações. Consulte a [CInt exemplo](#cint-example) seção para obter um exemplo.|  
  
 <sup>1</sup> partes fracionárias podem estar sujeitos a um tipo especial de chamado de arredondamento *arredondamento bancário*. Consulte "Comentários" para obter mais informações.  
  
## <a name="remarks"></a>Comentários  
 Como regra, você deve usar as funções de conversão de tipo de Visual Basic em preferência as métodos do .NET Framework, como `ToString()`, seja no <xref:System.Convert> classe ou em uma classe ou estrutura de tipo individual. Funções do Visual Basic são projetadas para interação ideal com o código do Visual Basic, e elas também tornam o código-fonte mais curto e fácil de ler. Além disso, os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as funções do Visual Basic, por exemplo, ao converter `Boolean` para `Integer`. Para obter mais informações, consulte [solução de problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  

Começando com o Visual Basic 15,8, o desempenho da conversão flutuante-ponto para inteiro é otimizado quando você passa o <xref:System.Single> ou <xref:System.Double> valor retornado por métodos a seguir com uma das funções de conversão de número inteiro (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

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

Essa otimização permite que o código que faz um grande número de conversões de inteiro para ser executado até duas vezes mais rápido. O exemplo a seguir ilustra essas conversões flutuante-ponto-a-inteiro otimizadas:

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
  
-   **Coerção.** Em geral, você pode usar as funções de conversão de tipo de dados para forçar o resultado de uma operação para um determinado tipo de dados em vez de um tipo de dados padrão. Por exemplo, use `CDec` para forçar a aritmética decimal em casos onde precisão simples, precisão dupla ou aritmética de inteiros normalmente aconteceria.  
  
-   **Conversões com falha.** Se o `expression` passado para a função está fora do intervalo do tipo de dados para o qual ele deve ser convertido, um <xref:System.OverflowException> ocorre.  
  
-   **Partes fracionárias.** Quando você converter um valor não integral para integral tipo, as funções de conversão de número inteiro (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, e `CUShort`) remover o fracionários parte e arredondar o valor para o inteiro mais próximo.  
  
     Se a parte fracionária é exatamente 0,5, as funções de conversão de número inteiro de ida e volta para o inteiro par mais próximo. Por exemplo, 0,5 é arredondado para 0 e 1.5 e 2.5 que sejam arredondados para 2. Isso às vezes é chamado *arredondamento bancário*, e sua finalidade é compensar uma tendência que poderia criar acúmulos ao somar muitos esses números.  
  
     `CInt` e `CLng` difere de <xref:Microsoft.VisualBasic.Conversion.Int%2A> e <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funções, que truncam, ao invés de ida e volta, a parte fracionária de um número. Além disso, `Fix` e `Int` sempre retornam um valor do mesmo tipo de dados conforme você passa no.  
  
-   **Conversões de data/hora.** Use o <xref:Microsoft.VisualBasic.Information.IsDate%2A> função para determinar se um valor pode ser convertido em uma data e hora. `CDate` reconhece os literais de data e hora literais, mas valores não numéricos. Para converter um Visual Basic 6.0 `Date` de valor para um `Date` valor no Visual Basic 2005 ou versões posteriores, você pode usar o <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> método.  
  
-   **Neutro valores de data/hora.** O [tipo de dados Date](../../../visual-basic/language-reference/data-types/date-data-type.md) sempre contém informações de data e hora. Para fins de conversão de tipo, o Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como um *valor neutro* para a data e 00:00:00 (meia-noite) ser um valor neutro para a hora. Se você converter um `Date` valor em uma cadeia de caracteres `CStr` não inclui valores neutros na cadeia de caracteres resultante. Por exemplo, se você converter `#January 1, 0001 9:30:00#` como uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas. No entanto, as informações de data ainda estão presentes no original `Date` de valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> função.  
  
-   **Diferenciação de cultura.** As funções de conversão de tipo envolvendo cadeias de caracteres executam conversões com base nas configurações de cultura atual para o aplicativo. Por exemplo, `CDate` reconhece os formatos de data de acordo com a configuração de localidade do seu sistema. Você deve fornecer o dia, mês e ano na ordem correta para sua localidade ou a data não pode ser interpretada corretamente. Um formato de data por extenso não é reconhecido se ele contiver uma cadeia de caracteres de dia da semana, como "Quarta-feira".  
  
     Se você precisar converter de ou para uma representação de cadeia de caracteres de um valor em um formato diferente daquele especificado pela sua localidade, será possível usar as funções de conversão de tipo de Visual Basic. Para fazer isso, use o `ToString(IFormatProvider)` e `Parse(String, IFormatProvider)` métodos de tipo desse valor. Por exemplo, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> ao converter uma cadeia de caracteres para um `Double`e use <xref:System.Double.ToString%2A?displayProperty=nameWithType> ao converter um valor do tipo `Double` para uma cadeia de caracteres.  
  
## <a name="ctype-function"></a>Função CType  
 O [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) leva um segundo argumento, `typename`e impõe `expression` para `typename`, onde `typename` pode ser qualquer tipo de dados, estrutura, classe ou interface para o qual existe uma conversão válida.  
  
 Para obter uma comparação `CType` com o outro tipo conversão palavras-chave, consulte [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) e [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>Exemplo de CBool  
 O exemplo a seguir usa o `CBool` função para converter expressões para `Boolean` valores. Se uma expressão é avaliada como um valor diferente de zero, `CBool` retorna `True`; caso contrário, ele retorna `False`.  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a>Exemplo de CByte  
 O exemplo a seguir usa o `CByte` função para converter uma expressão para um `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a>Exemplo de CChar  
 O exemplo a seguir usa o `CChar` função para converter o primeiro caractere de um `String` expressão para um `Char` tipo.  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 O argumento de entrada para `CChar` deve ser do tipo de dados `Char` ou `String`. Não é possível usar `CChar` para converter um número em um caractere, porque `CChar` não pode aceitar o tipo de dados numéricos. O exemplo a seguir obtém um número que representa um ponto de código (código de caractere) e o converte em caractere correspondente. Ele usa o <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> função para obter a cadeia de caracteres de dígitos, `CInt` para converter a cadeia de caracteres para o tipo `Integer`, e `ChrW` converter o número para o tipo `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a>Exemplo de CDate  
 O exemplo a seguir usa o `CDate` função para converter cadeias de caracteres para `Date` valores. Em geral, embutir datas e horas como cadeias de caracteres (como mostrado neste exemplo) não é recomendável. Use literais de data e hora literais, como #Feb 12, 1969 # e # 4:45:23 PM #, em vez disso.  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a>Exemplo de CDbl  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a>Exemplo de CDec  
 O exemplo a seguir usa o `CDec` função para converter um valor numérico para `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a>Exemplo de CInt  
 O exemplo a seguir usa o `CInt` função para converter um valor de `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a>Exemplo de CLng
 O exemplo a seguir usa o `CLng` função para converter valores para `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a>Exemplo de CObj  
 O exemplo a seguir usa o `CObj` função para converter um valor numérico para `Object`. O `Object` própria variável contém apenas um ponteiro de quatro bytes, que aponta para o `Double` valor atribuído a ele.  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a>Exemplo de CSByte  
 O exemplo a seguir usa o `CSByte` função para converter um valor numérico para `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a>Exemplo de CShort  
 O exemplo a seguir usa o `CShort` função para converter um valor numérico para `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a>Exemplo de CSng  
 O exemplo a seguir usa o `CSng` função para converter valores para `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a>Exemplo de CStr  
 O exemplo a seguir usa o `CStr` função para converter um valor numérico para `String`.  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 O exemplo a seguir usa o `CStr` função para converter `Date` valores `String` valores.  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` sempre renderiza um `Date` valor no formato padrão curto para a localidade atual, por exemplo, "6/15/2003 4:35:47 PM". No entanto, `CStr` suprime a *valores neutros* de 1/1/0001 para a data e 00:00:00 para a hora.  
  
 Para obter mais detalhes sobre os valores retornados pelo `CStr`, consulte [retornar valores para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Exemplo de CUInt  
 O exemplo a seguir usa o `CUInt` função para converter um valor numérico para `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a>Exemplo de CULng  
 O exemplo a seguir usa o `CULng` função para converter um valor numérico para `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a>Exemplo de CUShort  
 O exemplo a seguir usa o `CUShort` função para converter um valor numérico para `UShort`.  
  
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
- [Funções de conversão](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
