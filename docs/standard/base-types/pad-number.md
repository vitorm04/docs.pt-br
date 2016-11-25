---
title: "Como preencher um número com zeros à esquerda"
description: "Como preencher um número com zeros à esquerda"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: a517c066-b11e-4815-826b-9262611eac40
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 0a136d88dfbc83d40ff8a204f275537c24f9748b

---

# <a name="how-to-pad-a-number-with-leading-zeros"></a>Como preencher um número com zeros à esquerda

É possível adicionar zeros à esquerda de um inteiro usando a [cadeia de caracteres de formato numérico padrão](standard-numeric.md) “D” com um especificador de precisão. Você pode adicionar zeros à esquerda de inteiros e pontos flutuantes usando uma [cadeia de caracteres de formato numérico personalizado](custom-numeric.md). Este tópico mostra como usar os dois métodos para acrescentar um número com zeros à esquerda.

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a>Para acrescentar um número inteiro com zeros à esquerda com um comprimento específico

1. Determine o número mínimo de dígitos que o valor inteiro deve exibir. Inclua os dígitos à esquerda nesse número.

2. Determine se quer exibir o inteiro como valor decimal ou hexadecimal.

    * Para exibir o número inteiro como decimal, chame seu método `ToString(String)` e informe a cadeia de caracteres “D*n*” como valor do parâmetro format, em que *n* representa o comprimento mínimo da cadeia de caracteres.
    
    * Para exibir o número inteiro como hexadecimal, chame seu método `ToString(String)` e informe a cadeia de caracteres “X*n*” como valor do parâmetro format, em que *n* representa o comprimento mínimo da cadeia de caracteres.
    
  Você também pode usar uma cadeia de caracteres de formato em um método, como [Console.WriteLine](xref:System.Console.WriteLine) ou [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)), que usa [formatação de composição](composite-format.md).  
  
O exemplo a seguir formata diversos valores inteiros com zeros à esquerda para que o comprimento total do número formatado tenha pelo menos oito caracteres.

```csharp
byte byteValue = 254;
short shortValue = 10342;
int intValue = 1023983;
long lngValue = 6985321;               
ulong ulngValue = UInt64.MaxValue;

// Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"));
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"));
Console.WriteLine();

// Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue);
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue);
// The example displays the following output:
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//       
//                     00000254               000000FE
//                     00010342               00002866
//                     01023983               000F9FEF
//                     06985321               006A9669
//         18446744073709551615       FFFFFFFFFFFFFFFF
//         18446744073709551615       FFFFFFFFFFFFFFFF
```

```vb
Dim byteValue As Byte = 254
Dim shortValue As Short = 10342
Dim intValue As Integer = 1023983
Dim lngValue As Long = 6985321               
Dim ulngValue As ULong = UInt64.MaxValue

' Display integer values by calling the ToString method.
Console.WriteLine("{0,22} {1,22}", byteValue.ToString("D8"), byteValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", shortValue.ToString("D8"), shortValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", intValue.ToString("D8"), intValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", lngValue.ToString("D8"), lngValue.ToString("X8"))
Console.WriteLine("{0,22} {1,22}", ulngValue.ToString("D8"), ulngValue.ToString("X8"))
Console.WriteLine()

' Display the same integer values by using composite formatting.
Console.WriteLine("{0,22:D8} {0,22:X8}", byteValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", shortValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", intValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", lngValue)
Console.WriteLine("{0,22:D8} {0,22:X8}", ulngValue)
' The example displays the following output:
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
'       
'                     00000254               000000FE
'                     00010342               00002866
'                     01023983               000F9FEF
'                     06985321               006A9669
'         18446744073709551615       FFFFFFFFFFFFFFFF
```

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a>Para acrescentar um número inteiro com uma determinada quantidade de zeros à esquerda

1. Determine quantos zeros à esquerda o valor inteiro deve exibir.

2. Determine se quer exibir o inteiro como valor decimal ou hexadecimal. A formatação como valor decimal requer o uso de um especificador de formato padrão “D”; já a formatação como valor hexadecimal exige que você use o especificador de formato padrão “X”.

3. Determine o comprimento da cadeia de caracteres numérica não acrescentada. Para isso, chame o método `ToString("D").Length` ou `ToString("X").Length` do valor inteiro. 

4. Adicione quantos dígitos zero à esquerda quer incluir na cadeia de caracteres formatada com comprimento da cadeia de caracteres numérica não acrescentada. Isso define o comprimento total da cadeia de caracteres acrescentada.

5. Chame o método `ToString(String)` do valor inteiro e informe a cadeia de caracteres “D*n*” para cadeias de caracteres decimais e “X*n*” para cadeias de caracteres hexadecimais, em que *n* representa o comprimento total da cadeia de caracteres acrescentada. Você também pode usar uma cadeia de caracteres de formato “D*n*” ou “X*n*” em um método com suporte para formatação de composição.

O exemplo a seguir acrescenta um valor inteiro com cinco dígitos zero à esquerda.

```csharp
int value = 160934;
int decimalLength = value.ToString("D").Length + 5;
int hexLength = value.ToString("X").Length + 5;
Console.WriteLine(value.ToString("D" + decimalLength.ToString()));
Console.WriteLine(value.ToString("X" + hexLength.ToString()));
// The example displays the following output:
//       00000160934
//       00000274A6
```

```vb
Dim value As Integer = 160934
Dim decimalLength As Integer = value.ToString("D").Length + 5
Dim hexLength As Integer = value.ToString("X").Length + 5
Console.WriteLine(value.ToString("D" + decimalLength.ToString()))
Console.WriteLine(value.ToString("X" + hexLength.ToString()))
' The example displays the following output:
'       00000160934
'       00000274A6 
```

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a>Para acrescentar um valor numérico com zeros à esquerda com comprimento específico

1. Determine quantos dígitos a representação da cadeia de caracteres de números deve ter à esquerda dos decimais. Inclua os dígitos zero à esquerda no número total de dígitos.

2. Defina uma cadeia de caracteres de formato numérico personalizado que usa o espaço reservado com valor zero (“0”) para representar a quantidade mínima de dígitos zero.

3. Chame o método `ToString(String)` do número e apresente-o à cadeia de caracteres de formato personalizado. Você também pode usar uma cadeia de caracteres de formato personalizado com um método compatível com formatação de composição.

O exemplo a seguir formata diversos valores numéricos com zeros à esquerda para que o comprimento total do número formatado tenha pelo menos oito caracteres à esquerda do decimal.

```csharp
string fmt = "00000000.##";
int intValue = 1053240;
decimal decValue = 103932.52m;
float sngValue = 1549230.10873992f;
double dblValue = 9034521202.93217412;

// Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt));
Console.WriteLine(decValue.ToString(fmt));           
Console.WriteLine(sngValue.ToString(fmt));
Console.WriteLine(dblValue.ToString(fmt));           
Console.WriteLine();

// Display the numbers using composite formatting.
string formatString = " {0,15:" + fmt + "}";
Console.WriteLine(formatString, intValue);      
Console.WriteLine(formatString, decValue);      
Console.WriteLine(formatString, sngValue);      
Console.WriteLine(formatString, dblValue);      
// The example displays the following output:
//       01053240
//       00103932.52
//       01549230
//       9034521202.93
//       
//               01053240
//            00103932.52
//               01549230
//          9034521202.93  
```

```vb
Dim fmt As String = "00000000.##"
Dim intValue As Integer = 1053240
Dim decValue As Decimal = 103932.52d
Dim sngValue As Single = 1549230.10873992
Dim dblValue As Double = 9034521202.93217412

' Display the numbers using the ToString method.
Console.WriteLine(intValue.ToString(fmt))
Console.WriteLine(decValue.ToString(fmt))            
Console.WriteLine(sngValue.ToString(fmt))
Console.WriteLine(dblValue.ToString(fmt))            
Console.WriteLine()

' Display the numbers using composite formatting.
Dim formatString As String = " {0,15:" + fmt + "}"
Console.WriteLine(formatString, intValue)      
Console.WriteLine(formatString, decValue)      
Console.WriteLine(formatString, sngValue)      
Console.WriteLine(formatString, dblValue)      
' The example displays the following output:
'       01053240
'       00103932.52
'       01549230
'       9034521202.93
'       
'               01053240
'            00103932.52
'               01549230
'          9034521202.93
```

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a>Para acrescentar um valor numérico com uma determinada quantidade de zeros à esquerda

1. Determine quantos zeros à esquerda o valor numérico deve ter.

2. Determine a quantidade de dígitos à esquerda do decimal na cadeia de caracteres numéricos não acrescentada. Para fazer isso:

    a. Determine se a representação da cadeia de caracteres de um número inclui um símbolo de ponto decimal.
    
    b. Caso o símbolo esteja presente, determine a quantidade de caracteres à esquerda do ponto decimal.       
    
    - ou -
       
    Caso o símbolo não esteja presente, determine o comprimento da cadeia de caracteres. 
       
3. Crie uma cadeia de caracteres de formato personalizado que use o espaço reservado zero (“0”) para que cada um dos dígitos zero à esquerda apareça na cadeia de caracteres e que use o espaço reservado zero ou de dígito (“#”) para representar cada dígito na cadeia de caracteres padrão. 

4. Forneça a cadeia de caracteres de formato personalizado como parâmetro para o método ToString(String) do número ou para um método com suporte para formatação de composição.

O exemplo a seguir acrescenta dois valores [Double](xref:System.Double) com cinco dígitos zero à esquerda.

```csharp
double[] dblValues = { 9034521202.93217412, 9034521202 };
foreach (double dblValue in dblValues)
{
   string decSeparator = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator;
   string fmt, formatString;

   if (dblValue.ToString().Contains(decSeparator))
   {
      int digits = dblValue.ToString().IndexOf(decSeparator);
      fmt = new String('0', 5) + new String('#', digits) + ".##";
   }
   else
   {
      fmt = new String('0', dblValue.ToString().Length);   
   }
   formatString = "{0,20:" + fmt + "}";

   Console.WriteLine(dblValue.ToString(fmt));
   Console.WriteLine(formatString, dblValue);
}
// The example displays the following output:
//       000009034521202.93
//         000009034521202.93
//       9034521202
//                 9034521202 
```

```vb
Dim dblValues() As Double = { 9034521202.93217412, 9034521202 }
For Each dblValue As Double In dblValues
   Dim decSeparator As String = System.Globalization.NumberFormatInfo.CurrentInfo.NumberDecimalSeparator
   Dim fmt, formatString As String

   If dblValue.ToString.Contains(decSeparator) Then
      Dim digits As Integer = dblValue.ToString().IndexOf(decSeparator)
      fmt = New String("0"c, 5) + New String("#"c, digits) + ".##"
   Else
      fmt = New String("0"c, dblValue.ToString.Length)   
   End If
   formatString = "{0,20:" + fmt + "}"

   Console.WriteLine(dblValue.ToString(fmt))
   Console.WriteLine(formatString, dblValue)
Next
' The example displays the following output:
'       000009034521202.93
'         000009034521202.93
'       9034521202
'                 9034521202
```

## <a name="see-also"></a>Consulte também

[Cadeias de caracteres de formato numérico padrão](standard-numeric.md)

[Cadeias de caracteres de formato numérico personalizado](custom-numeric.md)

[Formatação de composição](composite-format.md)




<!--HONumber=Nov16_HO3-->


