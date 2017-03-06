---
title: "Cadeias de caracteres de formato numérico personalizado"
description: "Cadeias de caracteres de formato numérico personalizado"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 7b1c16ee-956f-4e9c-8502-c3dd6598c51d
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 017ee2b6feb87841f31660fe6cb76ccbefd5c83b
ms.lasthandoff: 03/02/2017

---

# <a name="custom-numeric-format-strings"></a>Cadeias de caracteres de formato numérico personalizado

Você pode criar uma cadeia de caracteres de formato numérico personalizado, que consiste em um ou mais especificadores numéricos personalizados, para definir a formatação de dados numéricos. Uma cadeia de caracteres de formato numérico personalizado é qualquer cadeia de caracteres que é não uma [cadeia de caracteres de formato numérico padrão](standard-numeric.md). 

As cadeias de caracteres de formato numérico personalizado têm suporte de algumas sobrecargas do método `ToString` de todos os tipos numéricos. Por exemplo, você pode fornecer uma cadeia de caracteres de formato numérico aos métodos [ToString(String)](xref:System.Int32.ToString(System.String)) e [ToString(String, IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) do tipo [Int32](xref:System.Int32). As cadeias de caracteres de formato numérico personalizado também têm suporte do recurso de [formatação de composição](composite-format.md) do .NET Framework, que é usado por alguns métodos `Write` e `WriteLine` das classes [Console](xref:System.Console) e [StreamWriter](xref:System.IO.StreamWriter), do método [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) e do método [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)).

A tabela a seguir descreve os especificadores de formato numérico personalizado e exibe amostras de saída produzidas por cada especificador de formato. Consulte a seção [Notas](#notes) para obter informações adicionais sobre como usar cadeias de caracteres de formato numérico personalizado e a seção [Exemplo](#example) para obter uma ilustração abrangente de seu uso.

Especificador de formato | Nome | Descrição | Exemplos
---------------- | ---- | ----------- | --------
"0" | Espaço reservado de zero | Substitui o zero pelo dígito correspondente, se houver um presente. Caso contrário, o zero aparecerá na cadeia de caracteres de resultado. | `1234.5678 ("00000") -> 01235`; `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
"#" | Espaço reservado de dígito | Substitui o símbolo "#" pelo dígito correspondente, se houver um presente. Caso contrário, nenhum dígito aparecerá na cadeia de caracteres de resultado. Observe que nenhum dígito aparece na cadeia de caracteres de resultado se o dígito na cadeia de entrada correspondente for um 0 não significativo. Por exemplo, 0003 ("####") -> 3. | `1234.5678 ("#####") -> 1235`; `0.45678 ("#.##", en-US) -> .46`; `0.45678 ("#.##", fr-FR) -> ,46`
"." | Ponto decimal | Determina a posição do separador decimal na cadeia de caracteres de resultado. | `0.45678 ("0.00", en-US) -> 0.46`; `0.45678 ("0.00", fr-FR) -> 0,46`
",""," | Separador de grupo e escala numérica | Funciona tanto como um separador de grupo quanto como um especificador de escala numérica. Como separador de grupo, insere um caractere separador de grupo localizado entre cada grupo. Como especificador de escala numérica, divide um número por 1000 para cada vírgula especificada. | Especificador de separador de grupo: `2147483647 ("##,#", en-US) -> 2,147,483,647`; `2147483647 ("##,#", es-ES) -> 2.147.483.647`. Especificador de escala: `2147483647 ("#,#,,", en-US) -> 2,147`; `2147483647 ("#,#,,", es-ES) -> 2.147`
"%" | Espaço reservado percentual | Multiplica um número por 100 e insere um símbolo percentual localizado na cadeia de caracteres de resultado. | `0.3697 ("%#0.00", en-US) -> %36.97`; `0.3697 ("%#0.00", el-GR) -> %36,97`; `0.3697 ("##.0 %", en-US) -> 37.0 %`; `0.3697 ("##.0 %", el-GR) -> 37,0 %`
"‰" | Espaço reservado por milhar | Multiplica um número por 1000 e insere um símbolo de por milhar localizado na cadeia de caracteres de resultado. | `0.03697 ("#0.00‰", en-US) -> 36.97‰`; `0.03697 ("#0.00‰", ru-RU) -> 36,97‰`
"E0", "E+0", "E-0", "e0", "e+0", "e-0" | Notação exponencial | Se seguida por pelo menos um 0 (zero), formata o resultado usando notação exponencial. A caixa de “E” ou “e” indica a caixa do símbolo do expoente na cadeia de caracteres de resultado. O número de zero depois do caractere “E” ou “e” determina o número mínimo de dígitos do expoente. Um sinal de positivo (+) indica que um caractere de sinal sempre precede o expoente. Um sinal de negativo (-) indica que um caractere de sinal precede apenas expoentes negativos. | `987654 ("#0.0e0") -> 98.8e4`; `1503.92311 ("0.0##e+00") -> 1.504e+03`; `1.8901385E-16 ("0.0e+00") -> 1.9e-16`
\ | Caractere de escape | Faz com que o próximo caractere seja interpretado como um literal em vez de como um especificador de formato personalizado. | `987654 ("\###00\#") -> #987654#`
'string', "string" | Delimitador de cadeia de caracteres literal | Indica que os caracteres delimitados devem ser copiados para a cadeia de caracteres de resultado sem sofrerem alterações. | `68 ("# ' degrees'") -> 68 degrees`
; | Separador de seção | Define seções com cadeias de caracteres de formato separadas para números positivos, negativos e zero. | `12.345 ("#0.0#;(#0.0#);-\0-") -> 12.35`; `0 ("#0.0#;(#0.0#);-\0-") -> -0-`; `-12.345 ("#0.0#;(#0.0#);-\0-") -> (12.35)`; `12.345 ("#0.0#;(#0.0#)") -> 12.35`; `0 ("#0.0#;(#0.0#)") -> 0.0 ; -12.345 ("#0.0#;(#0.0#)") -> (12.35)`
Outros | Todos os outros caracteres | O caractere é copiado, inalterado, para a cadeia de caracteres de resultado. | `68 ("# °") -> 68 °`

As seções a seguir fornecem informações detalhadas sobre cada um dos especificadores de formato numérico personalizado.

## <a name="the-0-custom-specifier"></a>Especificador personalizado "0"

O especificador de formato personalizado “0 " funciona como um símbolo de espaço reservado de zero. Se o valor que está sendo formatado tiver um dígito na posição em que o zero aparece na cadeia de caracteres de formato, esse dígito será copiado para a cadeia de caracteres de resultado; caso contrário, um zero aparecerá na cadeia de caracteres de resultado. A posição do zero mais à esquerda antes do ponto decimal e o zero mais à direita após o ponto decimal determina o intervalo de dígitos que estão sempre presentes na cadeia de caracteres de resultado. 

O especificador "00" faz com que o valor seja arredondado para o dígito mais próximo anterior ao decimal, no qual o arredondamento para cima sempre é usado. Por exemplo, a formatação de 34,5 com "00" resultaria no valor 35.

O exemplo a seguir mostra vários valores formatados com cadeias de caracteres de formato personalizado que incluem espaços reservados de zero.

```csharp
double value;

value = 123;
Console.WriteLine(value.ToString("00000"));
Console.WriteLine(String.Format("{0:00000}", value));
// Displays 00123

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

CultureInfo daDK = CultureInfo.CreateSpecificCulture("da-DK");
Console.WriteLine(value.ToString("00.00", daDK)); 
Console.WriteLine(String.Format(daDK, "{0:00.00}", value));
// Displays 01,20

value = .56;
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value));
// Displays 0.6

value = 1234567890;
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture));    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value));    
// Displays 1,234,567,890      

CultureInfo elGR = CultureInfo.CreateSpecificCulture("el-GR");
Console.WriteLine(value.ToString("0,0", elGR));    
Console.WriteLine(String.Format(elGR, "{0:0,0}", value));    
// Displays 1.234.567.890

value = 1234567890.123456;
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture));    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value));    
// Displays 1,234,567,890.1  

value = 1234.567890;
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture));    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value));    
// Displays 1,234.57
```

```vb
Dim value As Double

value = 123
Console.WriteLine(value.ToString("00000"))
Console.WriteLine(String.Format("{0:00000}", value))
' Displays 00123

value = 1.2
Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                  "{0:0.00}", value))
' Displays 1.20
Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value))
' Displays 01.20
Dim daDK As CultureInfo = CultureInfo.CreateSpecificCulture("da-DK")
Console.WriteLine(value.ToString("00.00", daDK))
Console.WriteLine(String.Format(daDK, "{0:00.00}", value))
' Displays 01,20

value = .56
Console.WriteLine(value.ToString("0.0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.0}", value))
' Displays 0.6

value = 1234567890
Console.WriteLine(value.ToString("0,0", CultureInfo.InvariantCulture))    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0}", value))    
' Displays 1,234,567,890      
Dim elGR As CultureInfo = CultureInfo.CreateSpecificCulture("el-GR")
Console.WriteLine(value.ToString("0,0", elGR))
Console.WriteLine(String.Format(elGR, "{0:0,0}", value))    
' Displays 1.234.567.890

value = 1234567890.123456
Console.WriteLine(value.ToString("0,0.0", CultureInfo.InvariantCulture))    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.0}", value))    
' Displays 1,234,567,890.1  

value = 1234.567890
Console.WriteLine(value.ToString("0,0.00", CultureInfo.InvariantCulture))    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0,0.00}", value))    
' Displays 1,234.57
```

## <a name="the--custom-specifier"></a>Especificador personalizado "#"

O especificador de formato personalizado “# " funciona como um símbolo de espaço reservado de dígito. Se o valor que está sendo formatado tem um dígito na posição onde o símbolo "#" aparece na cadeia de caracteres de formato, esse dígito é copiado para a cadeia de caracteres de resultado. Caso contrário, nada é armazenado nessa posição na cadeia de caracteres de resultado. 

Observe que esse especificador nunca exibe um zero que não seja um dígito significativo, mesmo se o zero é o único dígito na cadeia de caracteres. Ele exibirá zero somente se ele for um dígito significativo no número que está sendo exibido. 

A cadeia de caracteres de formato "##" faz com que o valor seja arredondado para o dígito mais próximo anterior ao decimal, no qual o arredondamento para cima sempre é usado. Por exemplo, a formatação de 34,5 com "##" resultaria no valor 35.

O exemplo a seguir mostra vários valores formatados com cadeias de caracteres de formato personalizado que incluem espaços reservados de dígito.

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value));
// Displays 1.2

value = 123;
Console.WriteLine(value.ToString("#####"));
Console.WriteLine(String.Format("{0:#####}", value));
// Displays 123

value = 123456;
Console.WriteLine(value.ToString("[##-##-##]"));      
Console.WriteLine(String.Format("{0:[##-##-##]}", value));      
// Displays [12-34-56]

value = 1234567890;
Console.WriteLine(value.ToString("#"));
Console.WriteLine(String.Format("{0:#}", value));
// Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"));
Console.WriteLine(String.Format("{0:(###) ###-####}", value));
// Displays (123) 456-7890
```

```vb
Dim value As Double

value = 1.2
Console.WriteLine(value.ToString("#.##", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#.##}", value))
' Displays 1.2

value = 123
Console.WriteLine(value.ToString("#####"))
Console.WriteLine(String.Format("{0:#####}", value))
' Displays 123

value = 123456
Console.WriteLine(value.ToString("[##-##-##]"))      
Console.WriteLine(String.Format("{0:[##-##-##]}", value))      
' Displays [12-34-56]

value = 1234567890
Console.WriteLine(value.ToString("#"))
Console.WriteLine(String.Format("{0:#}", value))
' Displays 1234567890

Console.WriteLine(value.ToString("(###) ###-####"))
Console.WriteLine(String.Format("{0:(###) ###-####}", value))
' Displays (123) 456-7890
```

Para retornar uma cadeia de caracteres de resultado em que dígitos ausentes ou zeros à esquerda são substituídos por espaços, use o recurso de [formatação de composição](composite-format.md) e especifique uma largura de campo, como mostra o exemplo a seguir.

```csharp
using System;

public class Example
{
   public static void Main()
   {
      Double value = .324;
      Console.WriteLine("The value is: '{0,5:#.###}'", value);
   }
}
// The example displays the following output if the current culture
// is en-US:
//      The value is: ' .324'
```

```vb
Module Example
   Public Sub Main()
      Dim value As Double = .324
      Console.WriteLine("The value is: '{0,5:#.###}'", value)
   End Sub
End Module
' The example displays the following output if the current culture
' is en-US:
'      The value is: ' .324'
```

## <a name="the--custom-specifier"></a>O "." Especificador Personalizado

O especificador de formato personalizado "." insere um separador decimal localizado na cadeia de caracteres resultante. O primeiro caractere de ponto na cadeia de caracteres de formato determina o local do separador decimal no valor formatado; quaisquer caracteres de ponto adicionais são ignorados. 

O caractere que é usado como separador decimal na cadeia de caracteres de resultado não é sempre um ponto, ele é determinado pela propriedade [NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que controla a formatação.

O exemplo a seguir usa o especificador de formato "." para definir a posição do ponto decimal em várias cadeias de caracteres de resultados.

```csharp
double value;

value = 1.2;
Console.WriteLine(value.ToString("0.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.00}", value));
// Displays 1.20

Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:00.00}", value));
// Displays 01.20

Console.WriteLine(value.ToString("00.00", 
                CultureInfo.CreateSpecificCulture("da-DK")));
Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                "{0:00.00}", value));
// Displays 01,20

value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)); 
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value)); 
// Displays 8.6%

value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                "{0:0.###E+0}", value));
// Displays 8.6E+4
```

```vb
Dim value As Double

  value = 1.2
  Console.Writeline(value.ToString("0.00", CultureInfo.InvariantCulture))
  Console.Writeline(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:0.00}", value))
  ' Displays 1.20

  Console.WriteLine(value.ToString("00.00", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:00.00}", value))
  ' Displays 01.20

  Console.WriteLine(value.ToString("00.00", _
                    CultureInfo.CreateSpecificCulture("da-DK")))
  Console.WriteLine(String.Format(CultureInfo.CreateSpecificCulture("da-DK"),
                    "{0:00.00}", value))
  ' Displays 01,20

  value = .086
  Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture)) 
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#0.##%}", value)) 
  ' Displays 8.6%

  value = 86000
  Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                    "{0:0.###E+0}", value))
' Displays 8.6E+4
```

## <a name="the--custom-specifier"></a>Especificador personalizado ","

O caractere "," funciona tanto como um separador de grupo quanto como um especificador de escala do número. 

* Separador de grupo: se uma ou mais vírgulas forem especificadas entre dois espaços reservados de dígito (0 ou #) que formatam os dígitos integrais de um número, um caractere separador de grupo será inserido entre cada grupo de números na parte integral da saída. 

  As propriedades [NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) e [NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual determinam o caractere usado como separador de número de grupo e o tamanho de cada grupo de números. Por exemplo, se a cadeia de caracteres "#,#" e a cultura invariável forem usadas para formatar o número 1000, a saída será "1.000".
  
* Especificador de escala numérica: se uma ou mais vírgulas forem especificadas imediatamente à esquerda do ponto decimal explícito ou implícito, o número a ser formatado será dividido por 1000 para cada vírgula. Por exemplo, se a cadeia de caracteres "0,," for usada para formatar o número 100 milhões, a saída será "100". 

Você pode usar os especificadores de separador de grupo e escala numérica na mesma cadeia de caracteres de formato. Por exemplo, se a cadeia de caracteres "#,&0;,," e a cultura invariante forem usadas para formatar o número um bilhão, a saída será "1.000". 

O exemplo a seguir ilustra o uso da vírgula como um separador de grupo.

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value));
// Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));
// Displays 1,235
```

```vb
Dim value As Double = 1234567890
Console.WriteLine(value.ToString("#,#", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,#}", value))
' Displays 1,234,567,890      

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value))
' Displays 1,235
```

O exemplo a seguir ilustra o uso da vírgula como um especificador de escala numérica.

```csharp
double value = 1234567890;
Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture));    
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,}", value));    
// Displays 1235   

Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,,,}", value));
// Displays 1  

Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture));       
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#,##0,,}", value));       
// Displays 1,235
```  

```vb
Dim value As Double = 1234567890
  Console.WriteLine(value.ToString("#,,", CultureInfo.InvariantCulture))    
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, "{0:#,,}", value))    
  ' Displays 1235   

  Console.WriteLine(value.ToString("#,,,", CultureInfo.InvariantCulture))
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,,,}", value))
' Displays 1  

  Console.WriteLine(value.ToString("#,##0,,", CultureInfo.InvariantCulture))       
  Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                  "{0:#,##0,,}", value))       
' Displays 1,235
```

## <a name="the--custom-specifier"></a>Especificador personalizado "%"

Um sinal de porcentagem (%) em uma cadeia de caracteres de formato faz com que um número seja multiplicado por 100 antes de ser formatado. O símbolo de porcentagem localizado é inserido no próprio número no local em que o % aparece na cadeia de caracteres de formato. O caractere de porcentagem usado é definido pela propriedade [PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) atual.

O exemplo a seguir define várias cadeias de caracteres de formato personalizado que incluem o especificador personalizado "%".

```csharp
double value = .086;
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value));
// Displays 8.6%     
```

```vb
Dim value As Double = .086
Console.WriteLine(value.ToString("#0.##%", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:#0.##%}", value))
' Displays 8.6% 
```

## <a name="the--custom-specifier"></a>Especificador personalizado "‰"

Um caractere de por mil sinal (‰ ou \u2030) em uma cadeia de caracteres de formato faz com que um número seja multiplicado por 1000 antes de ser formatado. O símbolo de por mil apropriado é inserido na cadeia de caracteres retornada no local em que o símbolo ‰ aparece na cadeia de caracteres de formato. O caractere de por mil usado é definido pela propriedade [NumberFormatInfo.PerMilleSymbol](xref:System.Globalization.NumberFormatInfo.PerMilleSymbol) do objeto que fornece informações de formatação específicas da cultura.

O exemplo a seguir define uma cadeia de caracteres de formato personalizado que inclui o especificador personalizado "‰".

```csharp
double value = .00354;
string perMilleFmt = "#0.## " + '\u2030';
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value));
// Displays 3.54‰   
```

```vb
Dim value As Double = .00354
Dim perMilleFmt As String = "#0.## " & ChrW(&h2030)
Console.WriteLine(value.ToString(perMilleFmt, CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:" + perMilleFmt + "}", value))
' Displays 3.54 ‰
```

## <a name="the-e-and-e-custom-specifiers"></a>Especificadores personalizados "E" e "e"

Se qualquer uma das cadeias de caracteres "E", " E + ", " E - ", "e", " e + " ou " e - " estiver presente na cadeia de caracteres de formato e for seguida imediatamente por pelo menos um caractere zero, então o número será formatado usando notação científica com um "E" ou "e" inserido entre o número e o expoente. O número de zeros após o indicador de notação científica determina o número mínimo de dígitos que serão enviados para o expoente. Os formatos "E+" e "e+" indicam que um caractere de positivo ou negativo sempre deve preceder o expoente. Os formatos "E", " E-", "e" ou "e-" indicam que um caractere de sinal só deve preceder os expoentes negativos.

O exemplo a seguir formata vários valores numéricos usando os especificadores para notação científica.

```csharp
double value = 86000;
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value));
// Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value));
// Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture));
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value));
// Displays 8.6E004
```

```vb
Dim value As Double = 86000
Console.WriteLine(value.ToString("0.###E+0", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+0}", value))
' Displays 8.6E+4

Console.WriteLine(value.ToString("0.###E+000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E+000}", value))
' Displays 8.6E+004

Console.WriteLine(value.ToString("0.###E-000", CultureInfo.InvariantCulture))
Console.WriteLine(String.Format(CultureInfo.InvariantCulture, 
                                "{0:0.###E-000}", value))
' Displays 8.6E004
```

## <a name="the--escape-character"></a>Caractere de escape “\"”

Os símbolos “#”, “0 ", “. ”, “,”, “% e "‰" em uma cadeia de caracteres de formato são interpretados como especificadores de formato e não como caracteres literais. Dependendo da sua posição em uma cadeia de caracteres de formato personalizado, o "E" em maiúscula e minúscula, bem como os símbolos + e -, também podem ser interpretados como especificadores de formato. 

Para impedir que um caractere seja interpretado como um especificador de formato, você pode precedê-lo com uma barra invertida, que é o caractere de escape. O caractere de escape significa que o próximo caractere é um literal de caractere que deve ser incluído inalterado na cadeia de caracteres de resultado.

Para incluir uma barra invertida em uma cadeia de caracteres de resultado, você deve escapá-la com outra barra invertida (\\). 

> [!NOTE]
> Alguns compiladores, como o compilador C#, também podem interpretar um único caractere de barra invertida como um caractere de escape. Para garantir que uma cadeia de caracteres seja interpretada corretamente quando formatada, você poderá usar o caractere literal de cadeia de caracteres textual (o caractere @) antes da cadeia de caracteres em C# ou adicionar outro caractere de barra invertida antes de cada barra invertida. O exemplo de C# a seguir ilustra ambas as abordagens.

O exemplo a seguir usa o caractere de escape para impedir que a operação de formatação interprete os caracteres "#", "0", e "\"" como caracteres de escape ou especificadores de formato. O exemplo usa uma barra invertida adicional para garantir que uma barra invertida seja interpretada como um caractere literal.

```csharp
int value = 123;
Console.WriteLine(value.ToString("\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#"));
Console.WriteLine(String.Format("{0:\\#\\#\\# ##0 dollars and \\0\\0 cents \\#\\#\\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString(xref:"\#\#\# ##0 dollars and \0\0 cents \#\#\#"));
Console.WriteLine(String.Format(xref:"{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}",
                                value));
// Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\"));
Console.WriteLine(String.Format("{0:\\\\\\\\\\\\ ##0 dollars and \\0\\0 cents \\\\\\\\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\

Console.WriteLine(value.ToString(xref:"\\\\\\ ##0 dollars and \0\0 cents \\\\\\"));
Console.WriteLine(String.Format(xref:"{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}",
                                value));
// Displays \\\ 123 dollars and 00 cents \\\
```

```vb
Dim value As Integer = 123
Console.WriteLine(value.ToString("\#\#\# ##0 dollars and \0\0 cents \#\#\#"))
Console.WriteLine(String.Format("{0:\#\#\# ##0 dollars and \0\0 cents \#\#\#}", 
                                value))
' Displays ### 123 dollars and 00 cents ###

Console.WriteLine(value.ToString("\\\\\\ ##0 dollars and \0\0 cents \\\\\\"))
Console.WriteLine(String.Format("{0:\\\\\\ ##0 dollars and \0\0 cents \\\\\\}", 
                                value))
' Displays \\\ 123 dollars and 00 cents \\\
```

## <a name="the--section-separator"></a>Separador de seção ";"

O ponto-e-vírgula (;) é um especificador de formato condicional que aplica formatação diferente a um número dependendo se o valor é positivo, negativo ou zero. Para produzir esse comportamento, uma cadeia de caracteres de formato personalizado pode conter até três seções separadas por ponto-e-vírgula. Essas seções são descritas na tabela a seguir. 

Número de seções | Descrição
------------------ | -----------
Uma seção | A cadeia de caracteres de formato aplica-se a todos os valores.
Duas seções | A primeira seção aplica-se a valores positivos e zeros e a segunda seção aplica-se a valores negativos. Se o número a ser formatado for negativo, mas se tornar zero após o arredondamento de acordo com o formato na segunda seção, então o zero resultante será formatado de acordo com a primeira seção.
Trê seções | A primeira seção aplica-se a valores positivos, a segunda seção aplica-se a valores negativos e a terceira seção aplica-se a zeros. A segunda seção pode ser deixada em branco (ao não ter nada entre os pontos-e-vírgulas), caso em que a primeira seção se aplica a todos os valores diferentes de zero. Se o número a ser formatado for não zero, mas se tornar zero após o arredondamento de acordo com o formato na primeira ou segunda seção, então o zero resultante será formatado de acordo com a terceira seção.

Separadores de seção ignoram qualquer formatação preexistente associada a um número quando o valor final é formatado. Por exemplo, valores negativos sempre são exibidos sem um sinal de negativ o quando os separadores de seção são usados. Se desejar que o valor final formatado contenha um sinal de negativo, você deverá incluir explicitamente o sinal de negativo como parte de especificador de formato personalizado. 

O exemplo a seguir utiliza o especificador de formato ";" para formatar números positivos, negativos e zero de maneira diferente.

```csharp
double posValue = 1234;
double negValue = -1234;
double zeroValue = 0;

string fmt2 = "##;(##)";
string fmt3 = "##;(##);**Zero**";

Console.WriteLine(posValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue));    
// Displays 1234

Console.WriteLine(negValue.ToString(fmt2));  
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue));    
// Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3)); 
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue));
// Displays **Zero**
```

```vb
Dim posValue As Double = 1234
Dim negValue As Double = -1234
Dim zeroValue As Double = 0

Dim fmt2 As String = "##;(##)"
Dim fmt3 As String = "##;(##);**Zero**"

Console.WriteLine(posValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", posValue))    
' Displays 1234

Console.WriteLine(negValue.ToString(fmt2))   
Console.WriteLine(String.Format("{0:" + fmt2 + "}", negValue))    
' Displays (1234)

Console.WriteLine(zeroValue.ToString(fmt3))  
Console.WriteLine(String.Format("{0:" + fmt3 + "}", zeroValue))
' Displays **Zero**
```

## <a name="notes"></a>Observações

### <a name="floating-point-infinities-and-nan"></a>Infinitos de ponto flutuante e NaN

Independentemente da cadeia de caracteres de formato, se o valor de um tipo de ponto flutuante [Single](xref:System.Single) ou [Double](xref:System.Double) é infinito positivo, infinito negativo ou não é um número (NaN), a cadeia de caracteres formatada é o valor das respectivas propriedades [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol), [NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol) ou [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) especificadas pelo objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) aplicável no momento. 

### <a name="rounding-and-fixed-point-format-strings"></a>Arredondamento e cadeias de caracteres de formato de ponto fixo

Para cadeias de caracteres de formato de ponto fixo (isto é, cadeias de caracteres de formato que não contêm caracteres de formato de notação científica), os números são arredondados para tantas casas decimais quanto houver espaços reservados de dígitos à direita do ponto decimal. Se a cadeia de caracteres de formato não contiver um ponto decimal, o número será arredondado para o inteiro mais próximo. Se o número tiver mais dígitos do que espaços reservados de dígitos à esquerda do ponto decimal, os dígitos extras serão copiados para a cadeia de caracteres de resultado imediatamente antes do primeiro espaço reservado de dígito.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra duas cadeias de caracteres de formato numérico personalizado. Em ambos os casos, o espaço reservado de dígito (#) exibe os dados numéricos e todos os outros caracteres são copiados para a cadeia de caracteres de resultado.

```csharp
double number1 = 1234567890;
string value1 = number1.ToString("(###) ###-####");
Console.WriteLine(value1);

int number2 = 42;
string value2 = number2.ToString("My Number = #");
Console.WriteLine(value2);
// The example displays the following output:
//       (123) 456-7890
//       My Number = 42
```

```vb
Dim number1 As Double = 1234567890
Dim value1 As String = number1.ToString("(###) ###-####")
Console.WriteLine(value1)

Dim number2 As Integer = 42
Dim value2 As String = number2.ToString("My Number = #")
Console.WriteLine(value2)
' The example displays the following output:
'       (123) 456-7890
'       My Number = 42
```

## <a name="see-also"></a>Consulte também

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[Formatando tipos](formatting-types.md)

[Cadeias de caracteres de formato numérico padrão](standard-numeric.md)

[Como preencher um número com zeros à esquerda](pad-number.md)

[Formatação de composição](composite-format.md)


