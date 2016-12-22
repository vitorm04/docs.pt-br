---
title: "Fun&#231;&#245;es de convers&#227;o do tipo (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.CUShort"
  - "vb.csng"
  - "vb.CDate"
  - "CByte"
  - "CSng"
  - "vb.CDec"
  - "CBool"
  - "CStr"
  - "vb.CULng"
  - "CDec"
  - "CVErr"
  - "CDbl"
  - "CShort"
  - "vb.CObj"
  - "vb.CVErr"
  - "CULng"
  - "vb.cdbl"
  - "vb.cbool"
  - "CObj"
  - "CDate"
  - "CLng"
  - "vb.cstr"
  - "vb.cbyte"
  - "vb.clng"
  - "vb.CChar"
  - "CUShort"
  - "vb.CUInt"
  - "vb.cint"
  - "vb.CShort"
  - "CInt"
  - "CUInt"
  - "CChar"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arredondamento bancário"
  - "tipo de dados Booliano, convertendo"
  - "tipo de dados Byte, convertendo"
  - "Função CBool"
  - "Função CByte"
  - "Função CChar"
  - "Função CDate"
  - "Função CDbl"
  - "Função CDec"
  - "tipo de dados Char, convertendo"
  - "Função CInt"
  - "Função CLng"
  - "conversões, funções de conversão de tipo"
  - "Função CSByte"
  - "Função CSng"
  - "Função CStr"
  - "Função CUInt"
  - "Função CULng"
  - "tipo de dados Currency, funções de conversão"
  - "Função CUShort"
  - "conversão de tipo de dados, funções para"
  - "tipos de dados [Visual Basic], convertendo"
  - "tipo de dados de data, convertendo"
  - "datas, convertendo"
  - "tipo de dados Decimal, convertendo"
  - "tipo de dados Double, convertendo"
  - "números de precisão dupla"
  - "frações"
  - "tipo de dados Integer, convertendo"
  - "números inteiros, funções de conversão de tipo"
  - "tipo de dados Long, convertendo"
  - "números, convertendo"
  - "números, arredondamento"
  - "valores de retorno, tipos de dados"
  - "arredondando números, arredondamento bancário"
  - "arredondando números, conversão de tipo"
  - "tipo de dados Short, convertendo"
  - "tipo de dados Single, convertendo"
  - "números de precisão única, convertendo"
  - "conversão de cadeia de caracteres, funções de conversão"
  - "tipo de dados String, convertendo"
  - "texto, convertendo"
  - "horas, convertendo"
  - "conversão de tipo, funções para"
  - "conversão de tipo, Visual Basic x .NET Framework"
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fun&#231;&#245;es de convers&#227;o do tipo (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.  Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.  Each function coerces an expression to a specific data type.  
  
## Sintaxe  
  
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
  
## Parte  
 `expression`  
 Obrigatório.  Any expression of the source data type.  
  
## Return Value Data Type  
 The function name determines the data type of the value it returns, as shown in the following table.  
  
|Nome da função|Tipo de dado retonado|Intervalo para `expression` argumento|  
|--------------------|---------------------------|-------------------------------------------|  
|`CBool`|[Tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Qualquer `Char` ou `String` ou expressão numérica.|  
|`CByte`|[Tipo de dados Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 through 255 \(unsigned\); fractional parts are rounded.<sup>1</sup>|  
|`CChar`|[Tipo de dados Char](../../../visual-basic/language-reference/data-types/char-data-type.md)|Qualquer `Char` ou `String` expressão; somente primeiro caractere de um `String` é convertida; valor pode ser 0 65535 até \(sem sinal\).|  
|`CDate`|[Tipo de dados Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|Any valid representation of a date and time.|  
|`CDbl`|[Tipo de dados double](../../../visual-basic/language-reference/data-types/double-data-type.md)|\-1.79769313486231570E\+308 through \-4.94065645841246544E\-324 for negative values; 4.94065645841246544E\-324 through 1.79769313486231570E\+308 for positive values.|  
|`CDec`|[Tipo de dados decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|\+\/\-79,228,162,514,264,337,593,543,950,335 for zero\-scaled numbers, that is, numbers with no decimal places.  For numbers with 28 decimal places, the range is \+\/\-7.9228162514264337593543950335.  The smallest possible non\-zero number is 0.0000000000000000000000000001 \(\+\/\-1E\-28\).|  
|`CInt`|[Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)|\-2,147,483,648 through 2,147,483,647; fractional parts are rounded.<sup>1</sup>|  
|`CLng`|[Tipo de dados Long](../../../visual-basic/language-reference/data-types/long-data-type.md)|\-9,223,372,036,854,775,808 through 9,223,372,036,854,775,807; fractional parts are rounded.<sup>1</sup>|  
|`CObj`|[Tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|Qualquer expressão válida.|  
|`CSByte`|[Tipo de dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|\-128 through 127; fractional parts are rounded.<sup>1</sup>|  
|`CShort`|[Tipo de dados curto](../../../visual-basic/language-reference/data-types/short-data-type.md)|\-32,768 through 32,767; fractional parts are rounded.<sup>1</sup>|  
|`CSng`|[Tipo de dados único](../../../visual-basic/language-reference/data-types/single-data-type.md)|\-3.402823E\+38 through \-1.401298E\-45 for negative values; 1.401298E\-45 through 3.402823E\+38 for positive values.|  
|`CStr`|[Tipo de dados da cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md)|Retorna para `CStr` dependem do `expression` argumento.  Consulte [Retornar valores para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 through 4,294,967,295 \(unsigned\); fractional parts are rounded.<sup>1</sup>|  
|`CULng`|[Tipo de dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 through 18,446,744,073,709,551,615 \(unsigned\); fractional parts are rounded.<sup>1</sup>|  
|`CUShort`|[Tipo de dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 through 65,535 \(unsigned\); fractional parts are rounded.<sup>1</sup>|  
  
 <sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.  See "Remarks" for more information.  
  
## Comentários  
 Como regra, você deve usar as funções de conversão de tipo de Visual Basic em preferência à.Métodos de NET Framework, como `ToString()`, ambos na <xref:System.Convert> classe ou em uma classe ou estrutura tipo individuais.  The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.  Além disso, o.Métodos de conversão do NET Framework não produzir os mesmos resultados que as funções Visual Basic, por exemplo, ao converter sempre `Boolean` para `Integer`.  Para obter mais informações, consulte [Solucionando problemas de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## Comportamento  
  
-   **Coercion.** In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.  Por exemplo, use `CDec` para forçar aritmética decimal em casos onde precisão simples, precisão dupla ou aritmética inteira normalmente demoraria local.  
  
-   **Failed Conversions.** Se a `expression` passado para a função está fora do intervalo do tipo de dados para a qual ele será convertido, um <xref:System.OverflowException> ocorre.  
  
-   **Fractional Parts.** Quando você converte um valor de nonintegral para uma integral digitar, as funções de conversão de inteiro \(`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, e `CUShort`\) removem a parte fracionária e arredondar o valor para o inteiro mais próximo.  
  
     If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.  Por exemplo, 0,5 é arredondado para 0 e 1.5 e 2.5 que sejam arredondados para 2.  Isso às vezes é chamado  *o arredondamento bancário*, e sua finalidade é compensar uma inclinação que pode acumular ao adicionar muitos esses números juntos.  
  
     `CInt`e `CLng` diferir do <xref:Microsoft.VisualBasic.Conversion.Int%2A> e <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funções, que truncar, ao invés de arredondar, a parte fracionária de um número.  Além disso, `Fix` e `Int` sempre retornam um valor do mesmo tipo de dados que você passe no.  
  
-   **Date\/Time Conversions.** Use o <xref:Microsoft.VisualBasic.Information.IsDate%2A> função para determinar se um valor pode ser convertido para uma data e hora.  `CDate`reconhece literais de data e literais de hora, mas valores não numéricos.  Para converter um 6.0 Visual Basic `Date` valor para um `Date` valor no Visual Basic 2005 ou versões posteriores, você pode usar o <xref:System.DateTime.FromOADate%2A?displayProperty=fullName> método.  
  
-   **Neutral Date\/Time Values.** O [Tipo de dados Data](../../../visual-basic/language-reference/data-types/date-data-type.md) sempre contém informações sobre a data e a hora.  For purposes of type conversion, Visual Basic considers 1\/1\/0001 \(January 1 of the year 1\) to be a *neutral value* for the date, and 00:00:00 \(midnight\) to be a neutral value for the time.  Se você converter um `Date` valor para uma seqüência de caracteres, `CStr` não inclui neutros valores na seqüência de caracteres resultante.  For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.  No entanto, as informações de data ainda estão presentes no original `Date` de valor e podem ser recuperados com funções como <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> função.  
  
-   **Culture Sensitivity.** The type conversion functions involving strings perform conversions based on the current culture settings for the application.  Por exemplo, `CDate` reconhece formatos de data de acordo com a configuração de localidade do sistema.  You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.  A long date format is not recognized if it contains a day\-of\-the\-week string, such as "Wednesday".  
  
     If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.  To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.  Por exemplo, use <xref:System.Double.Parse%2A?displayProperty=fullName> ao converter uma seqüência de caracteres para um `Double`e usar <xref:System.Double.ToString%2A?displayProperty=fullName> ao converter um valor do tipo `Double` para uma seqüência de caracteres.  
  
## CType Function  
 O  [Função CType](../../../visual-basic/language-reference/functions/ctype-function.md) usa um segundo argumento, `typename`e o converte no `expression` para `typename`, onde `typename` pode ser qualquer tipo de dados, estrutura, classe ou interface para o qual existe uma conversão válida.  
  
 Para uma comparação de `CType` com as outras conversão de tipos palavras\-chave, consulte [Operador DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) e [Operador TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## CBool Example  
 O exemplo a seguir usa a `CBool` função para converter expressões para `Boolean` valores.  Se uma expressão for avaliada como um valor diferente de zero, `CBool` retorna `True`; Caso contrário, ele retornará `False`.  
  
 [!CODE [VbVbalrFunctions#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#1)]  
  
## CByte Example  
 O exemplo a seguir usa a `CByte` função para converter uma expressão para um `Byte`.  
  
 [!CODE [VbVbalrFunctions#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#2)]  
  
## CChar Example  
 O exemplo a seguir usa a `CChar` função para converter o primeiro caractere de um `String` a expressão para um `Char` tipo.  
  
 [!CODE [VbVbalrFunctions#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#3)]  
  
 O argumento de entrada para `CChar` deve ser do tipo de dados `Char` ou `String`.  Não é possível usar `CChar` para converter um número para um caractere, como `CChar` não pode aceitar o tipo de dados numéricos.  The following example obtains a number representing a code point \(character code\) and converts it to the corresponding character.  Ele usa o <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> a função para obter a seqüência de dígitos, `CInt` para converter a seqüência de caracteres para digitar `Integer`, e `ChrW` para converter o número para digitar `Char`.  
  
 [!CODE [VbVbalrFunctions#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#4)]  
  
## CDate Example  
 O exemplo a seguir usa a `CDate` função para converter seqüências de caracteres para `Date` valores.  In general, hard\-coding dates and times as strings \(as shown in this example\) is not recommended.  Use date literals and time literals, such as \#Feb 12, 1969\# and \#4:45:23 PM\#, instead.  
  
 [!CODE [VbVbalrFunctions#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#5)]  
  
## CDbl Example  
 [!CODE [VbVbalrFunctions#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#6)]  
  
## CDec Example  
 O exemplo a seguir usa a `CDec` função para converter um valor numérico para `Decimal`.  
  
 [!CODE [VbVbalrFunctions#7](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#7)]  
  
## CInt Example  
 O exemplo a seguir usa a `CInt` função para converter um valor para `Integer`.  
  
 [!CODE [VbVbalrFunctions#8](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#8)]  
  
## CLng Example  
 O exemplo a seguir usa a `CLng` função para converter valores de `Long`.  
  
 [!CODE [VbVbalrFunctions#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#9)]  
  
## CObj Example  
 O exemplo a seguir usa a `CObj` função para converter um valor numérico para `Object`.  O `Object` própria variável contém apenas um ponteiro de quatro bytes, que aponta para o `Double` valor atribuído a ele.  
  
 [!CODE [VbVbalrFunctions#10](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#10)]  
  
## CSByte Example  
 O exemplo a seguir usa a `CSByte` função para converter um valor numérico para `SByte`.  
  
 [!CODE [VbVbalrFunctions#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#11)]  
  
## CShort Example  
 O exemplo a seguir usa a `CShort` função para converter um valor numérico para `Short`.  
  
 [!CODE [VbVbalrFunctions#12](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#12)]  
  
## CSng Example  
 O exemplo a seguir usa a `CSng` função para converter valores de `Single`.  
  
 [!CODE [VbVbalrFunctions#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#13)]  
  
## CStr Example  
 O exemplo a seguir usa a `CStr` função para converter um valor numérico para `String`.  
  
 [!CODE [VbVbalrFunctions#14](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#14)]  
  
 O exemplo a seguir usa a `CStr` função para converter `Date` valores a `String` valores.  
  
 [!CODE [VbVbalrFunctions#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#15)]  
  
 `CStr`sempre renderiza uma `Date` o valor no formato curto padrão para a localidade atual, por exemplo, "15\/6\/2003 4: 35: 47 PM".  No entanto, `CStr` suprime a  *valores neutras* de 1\/1\/0001 para a data e a 00: 00: 00 para o tempo.  
  
 Para obter mais detalhes sobre os valores retornados por `CStr`, consulte [Retornar valores para a função CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## CUInt Example  
 O exemplo a seguir usa a `CUInt` função para converter um valor numérico para `UInteger`.  
  
 [!CODE [VbVbalrFunctions#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#16)]  
  
## CULng Example  
 O exemplo a seguir usa a `CULng` função para converter um valor numérico para `ULong`.  
  
 [!CODE [VbVbalrFunctions#17](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#17)]  
  
## CUShort Example  
 O exemplo a seguir usa a `CUShort` função para converter um valor numérico para `UShort`.  
  
 [!CODE [VbVbalrFunctions#18](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#18)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 <xref:Microsoft.VisualBasic.Strings.Format%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>   
 [Funções de conversão](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)