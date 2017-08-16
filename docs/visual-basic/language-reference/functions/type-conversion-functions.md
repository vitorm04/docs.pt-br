---
title: "Funções de conversão (Visual Basic) de tipo | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
dev_langs:
- VB
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type, converting
- string conversion, conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type, converting
- type conversion, functions for
- Single data type, converting
- numbers, rounding
- rounding numbers, type conversion
- CUShort function
- Long data type, converting
- return values, data types
- single-precision numbers, converting
- data type conversion, functions for
- CStr function
- times, converting
- CSng function
- conversions, type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type, conversion functions
- numbers, converting
- Double data type, converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type, converting
- Boolean data type, converting
- integers, type conversion functions
- dates, converting
- CULng function
- CInt function
- Date data type, converting
- Byte data type, converting
- String data type, converting
- CChar function
- banker's rounding
- Short data type, converting
- rounding numbers, banker's rounding
- type conversion, Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 276ecae4b722b0a80f81301a2e3d702a473ad14f
ms.lasthandoff: 03/13/2017

---
# <a name="type-conversion-functions-visual-basic"></a>Funções de conversão do tipo (Visual Basic)
Essas funções são compilados em linha, que significa que o código de conversão faz parte do código que avalia a expressão. Às vezes, não há nenhuma chamada para um procedimento para realizar a conversão, o que melhora o desempenho. Cada função impõe uma expressão para um tipo de dados específico.  
  
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
 O nome da função determina o tipo de dados do valor que ele retorna, conforme mostrado na tabela a seguir.  
  
|Nome da função|Tipo de dados de retorno|Intervalo para `expression` argumento|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Tipo de Dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer `Char` ou `String` ou expressão numérica.|  
|`CByte`|[Tipo de Dados Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 a 255 (não assinado); partes fracionários são arredondados. <sup>1</sup>|  
|`CChar`|[Tipo de Dados de Caractere](../../../visual-basic/language-reference/data-types/char-data-type.md)|Qualquer `Char` ou `String` expressão; apenas primeiro caractere de um `String` é convertido; valor pode ser de 0 a 65535 (não assinado).|  
|`CDate`|[Tipo de Dados de Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|Qualquer representação válida de uma data e hora.|  
|`CDbl`|[Tipo de Dados Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1, 79769313486231570E + 308 até - 4.94065645841246544 e-324 para valores negativos; 4.94065645841246544 e-324 1.79769313486231570 e + 308 para valores positivos.|  
|`CDec`|[Tipo de Dados Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+ /-79.228.162.514.264.337.593.543.950.335 para números com escala de zero, ou seja, números sem casas decimais. Para números com 28 casas decimais, o intervalo é + /-7.9228162514264337593543950335. O menor número possível diferente de zero é 0,0000000000000000000000000001 (+ /-1E-28).|  
|`CInt`|[Tipo de Dados Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|-2.147.483.648 a 2.147.483.647; partes fracionários são arredondados. <sup>1</sup>|  
|`CLng`|[Tipo de Dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)|-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807; partes fracionários são arredondados. <sup>1</sup>|  
|`CObj`|[Tipo de Dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer expressão válida.|  
|`CSByte`|[Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|-128 a 127; partes fracionários são arredondados. <sup>1</sup>|  
|`CShort`|[Tipo de Dados Short](../../../visual-basic/language-reference/data-types/short-data-type.md)|-32.768 a 32.767; partes fracionários são arredondados. <sup>1</sup>|  
|`CSng`|[Tipo de Dados Simples](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823E + 38 a - 1, 401298E-45 para valores negativos; 1, 401298E-45 a 3.402823E + 38 para valores positivos.|  
|`CStr`|[Tipo de Dados String](../../../visual-basic/language-reference/data-types/string-data-type.md)|Retorna para `CStr` dependem de `expression` argumento. Consulte [valores de retorno para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 a 4.294.967.295 (não assinado); partes fracionários são arredondados. <sup>1</sup>|  
|`CULng`|[Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 e 18.446.744.073.709.551.615 (não assinado); partes fracionários são arredondados. <sup>1</sup>|  
|`CUShort`|[Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 a 65.535 (não assinado); partes fracionários são arredondados. <sup>1</sup>|  
  
 <sup>1</sup> partes fracionárias podem estar sujeitos a um tipo especial de arredondamento chamado *arredondamento bancário*. Consulte "Comentários" para obter mais informações.  
  
## <a name="remarks"></a>Comentários  
 Como regra, você deve usar as funções de conversão de tipo do Visual Basic em vez de métodos do .NET Framework como `ToString()`, no <xref:System.Convert>classe ou em uma estrutura de tipo individual ou a classe</xref:System.Convert> As funções do Visual Basic são projetadas para interação ideal com código do Visual Basic, e elas também tornam o código-fonte mais curto e fácil de ler. Além disso, os métodos de conversão do .NET Framework nem sempre produzem os mesmos resultados que as funções do Visual Basic, por exemplo, ao converter `Boolean` para `Integer`. Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="behavior"></a>Comportamento  
  
-   **Coerção.** Em geral, você pode usar as funções de conversão de tipo de dados para forçar o resultado de uma operação para um determinado tipo de dados em vez de um tipo de dados padrão. Por exemplo, use `CDec` para forçar aritmética decimal em casos onde precisão simples, precisão dupla ou aritmética de inteiros seria normalmente ocorrem.  
  
-   **Conversões com falha.** Se o `expression` passado para a função está fora do intervalo do tipo de dados para o qual ele deve ser convertido, um <xref:System.OverflowException>ocorre.</xref:System.OverflowException>  
  
-   **Partes fracionárias.** Quando você converter um valor não integral integral tipo, as funções de conversão de inteiro (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, e `CUShort`) removem a parte fracionária e arredondar o valor para o inteiro mais próximo.  
  
     Se a parte fracionária é exatamente 0,5, as funções de conversão de inteiro de ida e volta para o inteiro par mais próximo. Por exemplo, 0,5 é arredondado para 0 e 1.5 e 2.5 que sejam arredondados para 2. Isso às vezes é chamado *arredondamento bancário*, e sua finalidade é compensar uma tendência que pode se acumular ao somar muitos desses números.  
  
     `CInt`e `CLng` difere do <xref:Microsoft.VisualBasic.Conversion.Int%2A>e <xref:Microsoft.VisualBasic.Conversion.Fix%2A>funções, que truncam, ao invés de arredondar, a parte fracionária de um número.</xref:Microsoft.VisualBasic.Conversion.Fix%2A> </xref:Microsoft.VisualBasic.Conversion.Int%2A> Além disso, `Fix` e `Int` você passar sempre retornam um valor do mesmo tipo de dados.  
  
-   **Conversões de data/hora.** Use o <xref:Microsoft.VisualBasic.Information.IsDate%2A>função para determinar se um valor pode ser convertido em uma data e hora.</xref:Microsoft.VisualBasic.Information.IsDate%2A> `CDate`reconhece literais de data e hora literais, mas valores não numéricos. Para converter um Visual Basic 6.0 `Date` valor para um `Date` valor no Visual Basic 2005 ou versões posteriores, você pode usar o <xref:System.DateTime.FromOADate%2A?displayProperty=fullName>método.</xref:System.DateTime.FromOADate%2A?displayProperty=fullName>  
  
-   **Neutralidade de valores de data/hora.** O [tipo de dados data](../../../visual-basic/language-reference/data-types/date-data-type.md) sempre contém informações de data e hora. Para fins de conversão de tipos, Visual Basic considera 1/1/0001 (1 de janeiro do ano 1) como sendo um *valor neutro* para a data e 00:00:00 (meia-noite) como sendo um valor neutro para a hora. Se você converter um `Date` valor para uma cadeia de caracteres `CStr` não inclui valores neutros na cadeia de caracteres resultante. Por exemplo, se você converter `#January 1, 0001 9:30:00#` em uma cadeia de caracteres, o resultado será "9:30:00 AM"; as informações de data são suprimidas. No entanto, as informações de data ainda estão presentes no original `Date` valor e pode ser recuperada com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>função.</xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>  
  
-   **Diferenciação de cultura.** As funções de conversão de tipo que envolvem sequências de caracteres executam conversões com base nas configurações de cultura atual do aplicativo. Por exemplo, `CDate` reconhece formatos de data de acordo com a configuração de localidade do sistema. Você deve fornecer o dia, mês e ano na ordem correta para sua localidade, ou a data não pode ser interpretada corretamente. Um formato de data por extenso não é reconhecido se ele contém uma cadeia de caracteres de dia da semana, como "Quarta-feira".  
  
     Se você precisar converter para ou de uma representação de cadeia de caracteres de um valor em um formato diferente daquele especificado pela sua localidade, você não pode usar as funções de conversão de tipo do Visual Basic. Para fazer isso, use o `ToString(IFormatProvider)` e `Parse(String, IFormatProvider)` métodos de tipo do valor. Por exemplo, use <xref:System.Double.Parse%2A?displayProperty=fullName>ao converter uma cadeia de caracteres para um `Double`e usar <xref:System.Double.ToString%2A?displayProperty=fullName>ao converter um valor do tipo `Double` para uma cadeia de caracteres.</xref:System.Double.ToString%2A?displayProperty=fullName> </xref:System.Double.Parse%2A?displayProperty=fullName>  
  
## <a name="ctype-function"></a>Função CType  
 O [função CType](../../../visual-basic/language-reference/functions/ctype-function.md) leva um segundo argumento, `typename`e impõe `expression` para `typename`, onde `typename` pode ser qualquer tipo de dados, estrutura, classe ou interface para o qual há uma conversão válida.  
  
 Para obter uma comparação de `CType` com as outras keywords de conversão de tipo, consulte [operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) e [operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>Exemplo de CBool  
 O exemplo a seguir usa o `CBool` função converter expressões para `Boolean` valores. Se uma expressão é avaliada como um valor diferente de zero, `CBool` retorna `True`; caso contrário, retornará `False`.  
  
 [!code-vb[VbVbalrFunctions n º&1;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>Exemplo de CByte  
 O exemplo a seguir usa o `CByte` função para converter uma expressão para um `Byte`.  
  
 [!code-vb[VbVbalrFunctions n º&2;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>Exemplo de CChar  
 O exemplo a seguir usa o `CChar` função para converter o primeiro caractere de um `String` expressão para um `Char` tipo.  
  
 [!code-vb[VbVbalrFunctions n º&3;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 O argumento de entrada para `CChar` deve ser do tipo de dados `Char` ou `String`. Não é possível usar `CChar` para converter um número em um caractere, porque `CChar` não pode aceitar um tipo de dados numérico. O exemplo a seguir obtém um número que representa um ponto de código (código de caractere) e o converte em caractere correspondente. Ele usa o <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>função para obter a cadeia de caracteres de dígitos, `CInt` para converter a cadeia de caracteres para o tipo `Integer`, e `ChrW` para converter o número para o tipo `Char`.</xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
  
 [!code-vb[VbVbalrFunctions n º&4;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>Exemplo de CDate  
 O exemplo a seguir usa o `CDate` função para converter cadeias de caracteres para `Date` valores. Em geral, embutir datas e horas como cadeias de caracteres (como mostrado neste exemplo) não é recomendável. Usar literais de data e hora, como #Feb 12, &#1969; e # 4:45:23 PM #, em vez disso.  
  
 [!code-vb[VbVbalrFunctions n º&5;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>Exemplo de CDbl  
 [!code-vb[VbVbalrFunctions n º&6;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>Exemplo de CDec  
 O exemplo a seguir usa o `CDec` função para converter um valor numérico para `Decimal`.  
  
 [!code-vb[VbVbalrFunctions&#7;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>Exemplo de CInt  
 O exemplo a seguir usa o `CInt` função para converter um valor de `Integer`.  
  
 [!code-vb[VbVbalrFunctions n º&8;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a>Exemplo de CLng  
 O exemplo a seguir usa o `CLng` função para converter valores para `Long`.  
  
 [!code-vb[VbVbalrFunctions n º&9;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>Exemplo de CObj  
 O exemplo a seguir usa o `CObj` função para converter um valor numérico para `Object`. O `Object` variável contém apenas um ponteiro de quatro bytes, que aponta para o `Double` valor atribuído a ele.  
  
 [!code-vb[VbVbalrFunctions n º&10;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>Exemplo de CSByte  
 O exemplo a seguir usa o `CSByte` função para converter um valor numérico para `SByte`.  
  
 [!code-vb[VbVbalrFunctions n º&11;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>Exemplo de CShort  
 O exemplo a seguir usa o `CShort` função para converter um valor numérico para `Short`.  
  
 [!code-vb[VbVbalrFunctions&#12;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>Exemplo de CSng  
 O exemplo a seguir usa o `CSng` função para converter valores para `Single`.  
  
 [!code-vb[VbVbalrFunctions&13;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>Exemplo de CStr  
 O exemplo a seguir usa o `CStr` função para converter um valor numérico para `String`.  
  
 [!code-vb[VbVbalrFunctions&#14;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 O exemplo a seguir usa o `CStr` função para converter `Date` valores `String` valores.  
  
 [!code-vb[VbVbalrFunctions&#15;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr`sempre processa uma `Date` valor no formato curto padrão para a localidade atual, por exemplo, "6/15/2003 4:35:47 PM". No entanto, `CStr` suprime o *valores neutros* de 1/1/0001 para a data e 00:00:00 para a hora.  
  
 Para obter mais detalhes sobre os valores retornados por `CStr`, consulte [retornar valores para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Exemplo de CUInt  
 O exemplo a seguir usa o `CUInt` função para converter um valor numérico para `UInteger`.  
  
 [!code-vb[VbVbalrFunctions n º&16;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>Exemplo de CULng  
 O exemplo a seguir usa o `CULng` função para converter um valor numérico para `ULong`.  
  
 [!code-vb[17 VbVbalrFunctions](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>Exemplo de CUShort  
 O exemplo a seguir usa o `CUShort` função para converter um valor numérico para `UShort`.  
  
 [!code-vb[VbVbalrFunctions n º&18;](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Int%2A></xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A></xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 <xref:Microsoft.VisualBasic.Strings.Format%2A></xref:Microsoft.VisualBasic.Strings.Format%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A></xref:Microsoft.VisualBasic.Conversion.Hex%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A></xref:Microsoft.VisualBasic.Conversion.Oct%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Str%2A></xref:Microsoft.VisualBasic.Conversion.Str%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Val%2A></xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [Funções de conversão](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
