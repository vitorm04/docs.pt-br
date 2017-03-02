---
title: "Conversão de tipos"
description: "Conversão de tipos"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/22/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c9a53222-89cb-47e5-983d-4f0f204e31ba
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 0a774a170b7703b900c2044708b07faeb4e51548
ms.lasthandoff: 03/02/2017

---

# <a name="type-conversion"></a>Conversão de tipos

Cada valor tem um tipo associado, o qual define atributos como a quantidade de espaço alocado para o valor, o intervalo de valores possíveis que ele pode assumir e os membros que ele disponibiliza. Muitos valores podem ser expressos por mais de um tipo. Por exemplo, o valor de `4` pode ser expresso como um inteiro ou um valor de ponto flutuante. A conversão de tipo cria um valor em um novo tipo que é equivalente ao valor de um tipo antigo, mas que não necessariamente preserva a identidade (ou o valor exato) do objeto original.

O .NET oferece suporte automaticamente às seguintes conversões:

* Conversão de uma classe derivada em uma classe base. Isso significa, por exemplo, que uma instância de qualquer classe ou estrutura pode ser convertida em uma instância de [Objeto](xref:System.Object). Essa conversão não exige um operador de conversão.

* Conversão de uma classe base para a classe derivada original. No C#, essa conversão exige um operador de conversão. No Visual Basic, ela exige o operador `CType` quando a `Option Strict` está ativada. 

* Conversão de um tipo que implementa uma interface para um objeto de interface que representa essa interface. Essa conversão não exige um operador de conversão.

* Conversão de um objeto de interface de volta para o tipo original que implementa essa interface. No C#, essa conversão exige um operador de conversão. No Visual Basic, ela exige o operador `CType` quando a `Option Strict` está ativada. 

Além dessas conversões automáticas, o .NET fornece várias funcionalidades que oferecem suporte à conversão personalizada de tipo. Eles incluem o seguinte: 

* O operador `Implicit`, que define as conversões de ampliação disponíveis entre tipos. Para obter mais informações, consulte a seção [Conversão implícita com o operador implícito](#implicit-conversion-with-the-implicit-operator).

* O operador `Explicit`, que define as conversões de redução disponíveis entre tipos. Para obter mais informações, consulte a seção [Conversão explícita com o operador explícito](#explicit-conversion-with-the-explicit-operator).

* A interface [IConvertible](xref:System.IConvertible), que define as conversões para cada um dos tipos de dados base do .NET. Para obter mais informações, consulte a seção [A interface IConvertible](#the-iconvertible-interface).

* A classe [Convert](xref:System.Convert), que fornece um conjunto de métodos que implementam os métodos na interface `IConvertible`. Para obter mais informações, consulte a seção [A classe Convert](#the-convert-class).

* A classe [TypeConverter](xref:System.ComponentModel.TypeConverter), que é uma classe base que pode ser estendida para oferecer suporte à conversão de um tipo especificado em qualquer outro tipo. Para obter mais informações, consulte a seção [A classe TypeConverter](#the-typeconverter-class).

## <a name="implicit-conversion-with-the-implicit-operator"></a>Conversão implícita com o operador implícito

As conversões de ampliação envolvem a criação de um novo valor do valor de um tipo existente que tem um intervalo mais restritivo ou uma lista de membros mais restrita que o tipo de destino. As conversões de ampliação não podem resultar na perda de dados (mas podem resultar em uma perda de precisão). Como os dados não podem ser perdidos, os compiladores podem tratar a conversão de forma implícita ou transparente, sem exigir o uso de um método de conversão explícita ou de um operador de conversão.

> [!NOTE]
> Embora o código que executa uma conversão implícita possa chamar um método de conversão ou usar um operador de conversão, seu uso não é exigido pelos compiladores que oferecem suporte a conversões implícitas.

Por exemplo, o tipo [Decimal](xref:System.Decimal) oferece suporte a conversões implícitas de valores de [Byte](xref:System.Byte), [Char](xref:System.Char), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) e [UInt64](xref:System.UInt64). O exemplo a seguir ilustra algumas dessas conversões implícitas ao atribuir valores a uma variável `Decimal`.

```csharp
byte byteValue = 16;
short shortValue = -1024;
int intValue = -1034000;
long longValue = 1152921504606846976;
ulong ulongValue = UInt64.MaxValue;

decimal decimalValue;

decimalValue = byteValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  byteValue.GetType().Name, decimalValue); 

decimalValue = shortValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  shortValue.GetType().Name, decimalValue); 

decimalValue = intValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  intValue.GetType().Name, decimalValue); 

decimalValue = longValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 

decimalValue = ulongValue;
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.", 
                  longValue.GetType().Name, decimalValue); 
// The example displays the following output:
//    After assigning a Byte value, the Decimal value is 16.
//    After assigning a Int16 value, the Decimal value is -1024.
//    After assigning a Int32 value, the Decimal value is -1034000.
//    After assigning a Int64 value, the Decimal value is 1152921504606846976.
//    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

```vb
Dim byteValue As Byte = 16
Dim shortValue As Short = -1024
Dim intValue As Integer = -1034000
Dim longValue As Long = CLng(1024^6)
Dim ulongValue As ULong = ULong.MaxValue

Dim decimalValue As Decimal

decimalValue = byteValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  byteValue.GetType().Name, decimalValue) 

decimalValue = shortValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  shortValue.GetType().Name, decimalValue) 

decimalValue = intValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  intValue.GetType().Name, decimalValue) 

decimalValue = longValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 

decimalValue = ulongValue
Console.WriteLine("After assigning a {0} value, the Decimal value is {1}.",
                  longValue.GetType().Name, decimalValue) 
' The example displays the following output:
'    After assigning a Byte value, the Decimal value is 16.
'    After assigning a Int16 value, the Decimal value is -1024.
'    After assigning a Int32 value, the Decimal value is -1034000.
'    After assigning a Int64 value, the Decimal value is 1152921504606846976.
'    After assigning a Int64 value, the Decimal value is 18446744073709551615.
```

Se o compilador de uma linguagem específica oferecer suporte a operadores personalizados, você também poderá definir conversões implícitas em seus próprios tipos personalizados. O exemplo a seguir oferece uma implementação parcial de um tipo de dados de byte assinado chamado `ByteWithSign` que usa a representação de sinal e magnitude. Ele oferece suporte à conversão implícita de valores de [Byte](xref:System.Byte) e [SByte](xref:System.SByte) em valores de `ByteWithSign`.

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   public static implicit operator ByteWithSign(SByte value) 
   {
      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static implicit operator ByteWithSign(Byte value)
   {
      ByteWithSign  newValue;
      newValue.signValue = 1;
      newValue.value = value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Public Overloads Shared Widening Operator CType(value As SByte) As ByteWithSign
      Dim newValue As ByteWithSign
      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator  

   Public Overloads Shared Widening Operator CType(value As Byte) As ByteWithSign
      Dim NewValue As ByteWithSign
      newValue.signValue = 1
      newValue.value = value
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

O código cliente pode então declarar uma variável `ByteWithSign` e atribuir a ela valores de [Byte](xref:System.Byte) e [SByte](xref:System.SByte) sem executar nenhuma conversão explícita ou usar operadores de conversão, conforme é mostrado no exemplo a seguir.

```csharp
SByte sbyteValue = -120;
ByteWithSign value = sbyteValue;
Console.WriteLine(value);
value = Byte.MaxValue;
Console.WriteLine(value);
// The example displays the following output:
//       -120
//       255
```

```vb
Dim sbyteValue As SByte = -120
Dim value As ByteWithSign = sbyteValue
Console.WriteLine(value.ToString()) 
value = Byte.MaxValue
Console.WriteLine(value.ToString()) 
' The example displays the following output:
'       -120
'       255
```

## <a name="explicit-conversion-with-the-explicit-operator"></a>Conversão explícita com o operador explícito

As conversões de redução envolvem a criação de um novo valor com o valor de um tipo existente que tem um intervalo mais amplo ou uma lista de membros maior do que o tipo de destino. Como uma conversão de redução pode resultar em uma perda de dados, os compiladores geralmente exigem que a conversão se torne explícita por meio da chamada de um método de conversão ou de um operador de conversão. Ou seja, a conversão deve ser tratada explicitamente no código do desenvolvedor. 

> [!NOTE]
> A finalidade principal de exigir um método de conversão ou um operador de conversão para reduzir conversões é fazer com que o desenvolvedor saiba sobre a possibilidade de perda de dados ou de uma [OverflowException](xref:System.OverflowException) para que ela possa ser tratada no código. No entanto, alguns compiladores podem amenizar esse requisito. Por exemplo, no Visual Basic, se a `Option Strict` estiver desativada (sua configuração padrão), o compilador do Visual Basic tentará executar as conversões de redução de forma implícita.

Por exemplo, os tipos de dados [UInt32](xref:System.UInt32), [Int64](xref:System.Int64) e [UInt64](xref:System.UInt64) têm intervalos que excedem o do tipo de dados [Int32](xref:System.Int32), conforme é mostrado na tabela a seguir.

Tipo | Comparação com intervalo de Int32
---- | ------------------------------
[Int64](xref:System.Int64) | [Int64.MaxValue](xref:System.Int64.MaxValue) é maior que [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue) e [Int64.MinValue](xref:System.Int64.MinValue) é menor que (tem um intervalo negativo maior que) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue).
[UInt32](xref:System.UInt32) | [UInt32.MaxValue](xref:System.UInt32.MaxValue) é maior que [Int32.MaxValue](xref:System.Int32.MaxValue).
[UInt64](xref:System.UInt64) | [UInt64.MaxValue](xref:System.UInt64.MaxValue) é maior que [Int32.MaxValue](xref:System.Int32.MaxValue).

Para tratar essas conversões de redução, o .NET permite que os tipos definam um operador `Explicit`. Os compiladores de linguagens individuais podem então implementar esse operador usando suas próprias sintaxes ou um membro da classe [Convert](xref:System.Convert) pode ser chamado para executar a conversão. (Para obter mais informações sobre a classe `Convert`, consulte [A classe Convert](#the-convert-class) mais adiante neste tópico.) O exemplo a seguir ilustra o uso das funcionalidades de linguagem para lidar com a conversão explícita destes valores inteiros que podem estar fora do intervalo em valores [Int32](xref:System.Int32). 

```csharp
long number1 = int.MaxValue + 20L;
uint number2 = int.MaxValue - 1000;
ulong number3 = int.MaxValue;

int intNumber;

try {
   intNumber = checked((int) number1);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number1.GetType().Name, intNumber); 
}
catch (OverflowException) {
   if (number1 > int.MaxValue)
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                        number1, int.MaxValue);
   else
      Console.WriteLine("Conversion failed: {0} is less than {1}.", 
                        number1, int.MinValue);
}

try {
   intNumber = checked((int) number2);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number2.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number2, int.MaxValue);
}

try {
   intNumber = checked((int) number3);
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                     number3.GetType().Name, intNumber); 
}
catch (OverflowException) {
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                     number1, int.MaxValue);
}

// The example displays the following output:
//    Conversion failed: 2147483667 exceeds 2147483647.
//    After assigning a UInt32 value, the Integer value is 2147482647.
//    After assigning a UInt64 value, the Integer value is 2147483647.
```

```vb
Dim number1 As Long = Integer.MaxValue + 20L
Dim number2 As UInteger = Integer.MaxValue - 1000
Dim number3 As ULong = Integer.MaxValue

Dim intNumber As Integer

Try
   intNumber = CInt(number1)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number1.GetType().Name, intNumber)
Catch e As OverflowException
   If number1 > Integer.MaxValue Then
      Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                        number1, Integer.MaxValue)
   Else
      Console.WriteLine("Conversion failed: {0} is less than {1}.\n", 
                                        number1, Integer.MinValue)
   End If
End Try

Try
   intNumber = CInt(number2)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number2.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.", 
                                     number2, Integer.MaxValue)
End Try

Try
   intNumber = CInt(number3)
   Console.WriteLine("After assigning a {0} value, the Integer value is {1}.", 
                       number3.GetType().Name, intNumber)
Catch e As OverflowException
   Console.WriteLine("Conversion failed: {0} exceeds {1}.",
                                     number1, Integer.MaxValue)
End Try
' The example displays the following output:
'    Conversion failed: 2147483667 exceeds 2147483647.
'    After assigning a UInt32 value, the Integer value is 2147482647.
'    After assigning a UInt64 value, the Integer value is 2147483647.
```

As conversões explícitas podem produzir resultados diferentes em linguagens diferentes e esses resultados podem diferir do valor retornado pelo método [Convert](xref:System.Convert) correspondente. Por exemplo, se o valor **12.63251** de [Double](xref:System.Double) for convertido em um [Int32](xref:System.Int32), tanto o método [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) do .NET quanto o `CInt` do Visual Basic arredondarão o [Double](xref:System.Double) para retornar o valor **13**, mas o operador `(int)` do C# truncará o [Double](xref:System.Double) para retornar o valor **12**. Da mesma forma, o operador `(int)` do C# não oferece suporte à conversão de booliano em inteiro, mas o método `CInt` do Visual Basic converte um valor `true` em **-1**. Por outro lado, o método [Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) converte um valor `true` em **1**.

A maioria dos compiladores permite que as conversões explícitas sejam executadas de forma verificada ou não verificada. Quando uma conversão verificada é executada, uma [OverflowException](xref:System.OverflowException) é gerada quando o valor do tipo a ser convertido está fora do intervalo do tipo de destino. Quando uma conversão não verificada é executada nas mesmas condições, a conversão pode não gerar uma exceção, mas o comportamento exato se tornará indefinido e um valor incorreto poderá ser produzido.

> [!NOTE]
> No C#, as conversões verificadas podem ser executadas usando a palavra-chave `checked` juntamente com um operador de conversão ou por meio da especificação da opção do compilador `/checked+`. Por outro lado, as conversões não verificadas podem ser executadas usando a palavra-chave `unchecked` juntamente com o operador de conversão ou especificando a opção do compilador `/checked-`. Por padrão, as conversões explícitas são do tipo não verificadas. No Visual Basic, as conversões verificadas podem ser executadas especificando a opção do compilador `/removeintchecks-`. Por outro lado, as conversões não verificadas podem ser executadas especificando a opção do compilador `/removeintchecks+`. Por padrão, as conversões explícitas são do tipo verificadas.

O exemplo do C# a seguir usa as palavras-chave `checked` e `unchecked` para ilustrar a diferença no comportamento quando um valor fora do intervalo de [Byte](xref:System.Byte) é convertido em `Byte`. A conversão verificada gera uma exceção, mas a conversão não verificada atribui [Byte.MaxValue](xref:System.Byte.MaxValue) à variável `Byte`.

```csharp
int largeValue = Int32.MaxValue;
byte newValue;

try {
   newValue = unchecked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}

try {
   newValue = checked((byte) largeValue);
   Console.WriteLine("Converted the {0} value {1} to the {2} value {3}.", 
                     largeValue.GetType().Name, largeValue,
                     newValue.GetType().Name, newValue);
}
catch (OverflowException) {
   Console.WriteLine("{0} is outside the range of the Byte data type.", 
                     largeValue);
}
// The example displays the following output:
//    Converted the Int32 value 2147483647 to the Byte value 255.
//    2147483647 is outside the range of the Byte data type.
```

Se o compilador de uma linguagem específica der suporte a operadores sobrecarregados personalizados, você também poderá definir as conversões explícitas em seus próprios tipos personalizados. O exemplo a seguir oferece uma implementação parcial de um tipo de dados de byte assinado chamado `ByteWithSign` que usa a representação de sinal e magnitude. Ele oferece suporte à conversão explícita de valores de [Int32](xref:System.Int32) e [UInt32](xref:System.UInt32) em valores de `ByteWithSign`.

```csharp
public struct ByteWithSign
{
   private SByte signValue; 
   private Byte value;

   private const byte MaxValue = byte.MaxValue;
   private const int MinValue = -1 * byte.MaxValue;

   public static explicit operator ByteWithSign(int value) 
   {
      // Check for overflow.
      if (value > ByteWithSign.MaxValue || value < ByteWithSign.MinValue)
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = (SByte) Math.Sign(value);
      newValue.value = (byte) Math.Abs(value);
      return newValue;
   }  

   public static explicit operator ByteWithSign(uint value)
   {
      if (value > ByteWithSign.MaxValue) 
         throw new OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", 
                                                   value));

      ByteWithSign newValue;
      newValue.signValue = 1;
      newValue.value = (byte) value;
      return newValue;
   }

   public override string ToString()
   { 
      return (signValue * value).ToString();
   }
}
```

```vb
Public Structure ByteWithSign
   Private signValue As SByte 
   Private value As Byte

   Private Const MaxValue As Byte = Byte.MaxValue
   Private Const MinValue As Integer = -1 * Byte.MaxValue

   Public Overloads Shared Narrowing Operator CType(value As Integer) As ByteWithSign
      ' Check for overflow.
      If value > ByteWithSign.MaxValue Or value < ByteWithSign.MinValue Then
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim newValue As ByteWithSign

      newValue.signValue = CSByte(Math.Sign(value))
      newValue.value = CByte(Math.Abs(value))
      Return newValue
   End Operator

   Public Overloads Shared Narrowing Operator CType(value As UInteger) As ByteWithSign
      If value > ByteWithSign.MaxValue Then 
         Throw New OverflowException(String.Format("'{0}' is out of range of the ByteWithSign 
                                                   data type.", value))
      End If

      Dim NewValue As ByteWithSign

      newValue.signValue = 1
      newValue.value = CByte(value)
      Return newValue
   End Operator

   Public Overrides Function ToString() As String 
      Return (signValue * value).ToString()
   End Function
End Structure
```

O código cliente poderá então declarar uma variável `ByteWithSign` e atribuir valores de [Int32](xref:System.Int32) e [UInt32](xref:System.UInt32) a ela se as atribuições incluírem um operador de conversão, como mostra o exemplo a seguir.

```csharp
ByteWithSign value;

try {
   int intValue = -120;
   value = (ByteWithSign) intValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
   Console.WriteLine(e.Message);
}

try {
   uint uintValue = 1024;
   value = (ByteWithSign) uintValue;
   Console.WriteLine(value);
}
catch (OverflowException e) {
    Console.WriteLine(e.Message);
}
// The example displays the following output:
//       -120
//       '1024' is out of range of the ByteWithSign data type.
```

```vb
Dim value As ByteWithSign

Try  
   Dim intValue As Integer = -120
   value = CType(intValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try

Try
   Dim uintValue As UInteger = 1024
   value = CType(uintValue, ByteWithSign)
   Console.WriteLine(value) 
Catch e As OverflowException
   Console.WriteLine(e.Message)
End Try
' The example displays the following output:
'       -120
'       '1024' is out of range of the ByteWithSign data type.
```

## <a name="the-iconvertible-interface"></a>A interface IConvertible

Para oferecer suporte à conversão de qualquer tipo em um tipo base do Common Language Runtime, o .NET oferece a interface [IConvertible](xref:System.IConvertible). O tipo de implementação é necessário para fornecer o seguinte:

* Um método que retorne o [TypeCode](xref:System.TypeCode) do tipo de implementação.

* Métodos para converter o tipo de implementação em cada tipo base do Common Language Runtime ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double) e assim por diante).

* Um método de conversão generalizado para converter uma instância do tipo de implementação em outro tipo especificado. As conversões sem suporte devem gerar uma [InvalidCastException](xref:System.InvalidCastException).

Cada tipo base do Common Language Runtime, ou seja, os tipos [Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [String](xref:System.String), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) e [UInt64](xref:System.UInt64), além de [DBNull](xref:System.DBNull) e [Enum](xref:System.Enum), implementam a interface [IConvertible](xref:System.IConvertible). No entanto, essas são implementações de interfaces explícitas. O método de conversão somente pode ser chamado por meio de uma variável da interface [IConvertible](xref:System.IConvertible), conforme é mostrado no exemplo a seguir. Este exemplo converte um valor de [Int32](xref:System.Int32) em seu valor de [Char](xref:System.Char) equivalente.

```csharp
int codePoint = 1067;
IConvertible iConv = codePoint;
char ch = iConv.ToChar(null);
Console.WriteLine("Converted {0} to {1}.", codePoint, ch);
```

```vb
Dim codePoint As Integer = 1067
Dim iConv As IConvertible = codePoint
Dim ch As Char = iConv.ToChar(Nothing)
Console.WriteLine("Converted {0} to {1}.", codePoint, ch)
```

O requisito para chamar o método de conversão em sua interface, em vez de no tipo de implementação, torna as implementações de interfaces explícitas relativamente dispendiosas. Em vez disso, recomendamos que você chame o membro apropriado da classe [Convert](xref:System.Convert) para converter entre tipos base do Common Language Runtime. Para obter mais informações, consulte a próxima seção: [A classe Convert](#the-convert-class). 

> [!NOTE]
> Além da interface [IConvertible](xref:System.IConvertible) e da classe [Convert](xref:System.Convert) fornecidas pelo .NET, as linguagens individuais também podem fornecer formas de executar conversões. Por exemplo, o C# usa operadores de conversão e Visual Basic usa funções de conversão implementadas no compilador, como `CType`,`CInt` e `DirectCast`.

Em grande parte, a interface [IConvertible](xref:System.IConvertible) é criada para oferecer suporte à conversão entre os tipos base no NET. No entanto, a interface também pode ser implementada por um tipo personalizado para oferecer suporte à conversão desse tipo em outros tipos personalizados. Para obter mais informações, consulte a seção [Conversões personalizadas com o método ChangeType](#custom-conversions-with-the-changetype-method) mais adiante neste tópico.

## <a name="the-convert-class"></a>A classe Convert

Embora a implementação da interface [IConvertible](xref:System.IConvertible) de cada tipo base possa ser chamada para executar uma conversão de tipo, chamar os métodos da classe [System.Convert](xref:System.Convert) é a maneira com neutralidade de idioma recomendada para converter de um tipo base em outro. Além disso, o método [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) pode ser usado para converter de um tipo personalizado especificado em outro tipo. 

### <a name="conversions-between-base-types"></a>Conversões entre tipos base

A classe [Convert](xref:System.Convert) fornece uma maneira com neutralidade de idioma de realizar conversões entre tipos base e está disponível para todas as linguagens que visam o Common Language Runtime. Ela fornece um conjunto completo de métodos para conversões de ampliação e de redução e gera uma [InvalidCastException](xref:System.InvalidCastException) para as conversões que não têm suporte (como a conversão de um valor de [DateTime](xref:System.DateTime) em um valor inteiro). As conversões de redução são executadas em um contexto verificado e uma [OverflowException](xref:System.OverflowException) será gerada se a conversão falhar.

> [!IMPORTANT]
> Como a classe [Convert](xref:System.Convert) inclui métodos para converter de/para cada tipo base, ela elimina a necessidade de chamar a implementação de interface explicita [IConvertible](xref:System.IConvertible) de cada tipo base.

O exemplo a seguir ilustra o uso da classe [System.Convert](xref:System.Convert) para executar várias conversões de ampliação e redução entre os tipos base do .NET.

```csharp
// Convert an Int32 value to a Decimal (a widening conversion).
int integralValue = 12534;
decimal decimalValue = Convert.ToDecimal(integralValue);
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:N2}.", 
                                  integralValue.GetType().Name, 
                                  integralValue, 
                                  decimalValue.GetType().Name, 
                                  decimalValue);
// Convert a Byte value to an Int32 value (a widening conversion).
byte byteValue = Byte.MaxValue;
int integralValue2 = Convert.ToInt32(byteValue);                                  
Console.WriteLine("Converted the {0} value {1} to " +  
                                  "the {2} value {3:G}.", 
                                  byteValue.GetType().Name, 
                                  byteValue, 
                                  integralValue2.GetType().Name, 
                                  integralValue2);

// Convert a Double value to an Int32 value (a narrowing conversion).
double doubleValue = 16.32513e12;
try {
   long longValue = Convert.ToInt64(doubleValue);
   Console.WriteLine("Converted the {0} value {1:E} to " +  
                                     "the {2} value {3:N0}.", 
                                     doubleValue.GetType().Name, 
                                     doubleValue, 
                                     longValue.GetType().Name, 
                                     longValue);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0:E} value {1}.", 
                                     doubleValue.GetType().Name, doubleValue);
}

// Convert a signed byte to a byte (a narrowing conversion).     
sbyte sbyteValue = -16;
try {
   byte byteValue2 = Convert.ToByte(sbyteValue);
   Console.WriteLine("Converted the {0} value {1} to " +  
                                     "the {2} value {3:G}.", 
                                     sbyteValue.GetType().Name, 
                                     sbyteValue, 
                                     byteValue2.GetType().Name, 
                                     byteValue2);
}
catch (OverflowException) {
   Console.WriteLine("Unable to convert the {0} value {1}.", 
                                     sbyteValue.GetType().Name, sbyteValue);
}                                         
// The example displays the following output:
//       Converted the Int32 value 12534 to the Decimal value 12,534.00.
//       Converted the Byte value 255 to the Int32 value 255.
//       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
//       Unable to convert the SByte value -16.
```

```vb
' Convert an Int32 value to a Decimal (a widening conversion).
Dim integralValue As Integer = 12534
Dim decimalValue As Decimal = Convert.ToDecimal(integralValue)
Console.WriteLine("Converted the {0} value {1} to the {2} value {3:N2}.", 
                  integralValue.GetType().Name,
                  integralValue,
                  decimalValue.GetType().Name,
                  decimalValue)

' Convert a Byte value to an Int32 value (a widening conversion).
Dim byteValue As Byte = Byte.MaxValue
Dim integralValue2 As Integer = Convert.ToInt32(byteValue)                                  
Console.WriteLine("Converted the {0} value {1} to " + 
                                  "the {2} value {3:G}.",
                                  byteValue.GetType().Name,
                                  byteValue,
                                  integralValue2.GetType().Name,
                                  integralValue2)

' Convert a Double value to an Int32 value (a narrowing conversion).
Dim doubleValue As Double = 16.32513e12
Try
   Dim longValue As Long = Convert.ToInt64(doubleValue)
   Console.WriteLine("Converted the {0} value {1:E} to " + 
                                     "the {2} value {3:N0}.",
                                     doubleValue.GetType().Name,
                                     doubleValue,
                                     longValue.GetType().Name,
                                     longValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0:E} value {1}.",
                                     doubleValue.GetType().Name, doubleValue)
End Try                                                             

' Convert a signed byte to a byte (a narrowing conversion).     
Dim sbyteValue As SByte = -16
Try
   Dim byteValue2 As Byte = Convert.ToByte(sbyteValue)
   Console.WriteLine("Converted the {0} value {1} to " + 
                                     "the {2} value {3:G}.",
                                     sbyteValue.GetType().Name,
                                     sbyteValue,
                                     byteValue2.GetType().Name,
                                     byteValue2)
Catch e As OverflowException
   Console.WriteLine("Unable to convert the {0} value {1}.",
                                     sbyteValue.GetType().Name, sbyteValue)
End Try 
' The example displays the following output:
'       Converted the Int32 value 12534 to the Decimal value 12,534.00.
'       Converted the Byte value 255 to the Int32 value 255.
'       Converted the Double value 1.632513E+013 to the Int64 value 16,325,130,000,000.
'       Unable to convert the SByte value -16.
```

Em alguns casos, principalmente na conversão de/para valores de ponto flutuante, uma conversão pode envolver uma perda de precisão, mesmo que não gere uma [OverflowException](xref:System.OverflowException). O exemplo a seguir ilustra essa perda de precisão. No primeiro caso, um valor de [Decimal](xref:System.Decimal) tem menos precisão (menos dígitos significativos) quando é convertido em [Double](xref:System.Double). No segundo caso, um valor de [Double](xref:System.Double) é arredondado de **42.72** para **43** para concluir a conversão.

```csharp
double doubleValue; 

// Convert a Double to a Decimal.
decimal decimalValue = 13956810.96702888123451471211m;
doubleValue = Convert.ToDouble(decimalValue);
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue);

doubleValue = 42.72;
try {
   int integerValue = Convert.ToInt32(doubleValue);
   Console.WriteLine("{0} converted to {1}.", 
                                     doubleValue, integerValue);
}
catch (OverflowException) {      
   Console.WriteLine("Unable to convert {0} to an integer.", 
                                     doubleValue);
}   
// The example displays the following output:
//       13956810.96702888123451471211 converted to 13956810.9670289.
//       42.72 converted to 43.
```

```vb
Dim doubleValue As Double 

' Convert a Double to a Decimal.
Dim decimalValue As Decimal = 13956810.96702888123451471211d
doubleValue = Convert.ToDouble(decimalValue)
Console.WriteLine("{0} converted to {1}.", decimalValue, doubleValue)

doubleValue = 42.72
Try
   Dim integerValue As Integer = Convert.ToInt32(doubleValue)
   Console.WriteLine("{0} converted to {1}.",
                                     doubleValue, integerValue)
Catch e As OverflowException
   Console.WriteLine("Unable to convert {0} to an integer.",
                                     doubleValue)
End Try   
' The example displays the following output:
'       13956810.96702888123451471211 converted to 13956810.9670289.
'       42.72 converted to 43.
```

Para ver uma tabela que lista as conversões de ampliação e redução com suporte da classe [Convert](xref:System.Convert), consulte [Tabelas de conversão de tipos](conversion-tables.md).

### <a name="custom-conversions-with-the-changetype-method"></a>Conversões personalizadas com o método ChangeType

Além de oferecer suporte a conversões para cada um dos tipos base, a classe [Convert](xref:System.Convert) pode ser usada para converter um tipo personalizado em um ou mais tipos predefinidos. Essa conversão é executada pelo método [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) que, por sua vez, encapsula uma chamada ao método [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) do parâmetro de valor. Isso significa que o objeto representado pelo parâmetro de valor deve fornecer uma implementação da interface [IConvertible](xref:System.IConvertible).

> [!NOTE]
> Como os métodos [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) e [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) usam um objeto de [Tipo](xref:System.Type) para especificar o tipo de destino no qual o valor será convertido, eles podem ser usados para executar uma conversão dinâmica em um objeto cujo tipo não seja conhecido no tempo de compilação. No entanto, observe que a implementação de valor da [IConvertible](xref:System.IConvertible) ainda deve oferecer suporte a essa conversão. 

O exemplo a seguir ilustra uma possível implementação da interface [IConvertible](xref:System.IConvertible) que permite que um objeto `TemperatureCelsius` seja convertido em um objeto `TemperatureFahrenheit` e vice-versa. O exemplo define uma classe base, `Temperature`, que implementa a interface [IConvertible](xref:System.IConvertible) e substitui o método [Object.ToString](xref:System.Object.ToString). As classes `TemperatureCelsius` e `TemperatureFahrenheit` derivadas substituem os métodos `ToType` e `ToString` da classe base. 

```csharp
using System;

public abstract class Temperature : IConvertible
{
   protected decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;
   }

   public decimal Value
   { 
      get { return this.temp; } 
      set { this.temp = Value; }        
   }

   public override string ToString()
   {
      return temp.ToString(null as IFormatProvider) + "º";
   }

   // IConvertible implementations.
   public TypeCode GetTypeCode() { 
      return TypeCode.Object;
   }   

   public bool ToBoolean(IFormatProvider provider) {
      throw new InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."));
   }

   public byte ToByte(IFormatProvider provider) {
      if (temp < Byte.MinValue || temp > Byte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Byte data type.", temp));
      else
         return (byte) temp;
   }

   public char ToChar(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-Char conversion is not supported.");
   }

   public DateTime ToDateTime(IFormatProvider provider) {
      throw new InvalidCastException("Temperature-to-DateTime conversion is not supported.");
   }

   public decimal ToDecimal(IFormatProvider provider) {
      return temp;
   }

   public double ToDouble(IFormatProvider provider) {
      return (double) temp;
   }

   public short ToInt16(IFormatProvider provider) {
      if (temp < Int16.MinValue || temp > Int16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp));
      else
         return (short) Math.Round(temp);
   }

   public int ToInt32(IFormatProvider provider) {
      if (temp < Int32.MinValue || temp > Int32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp));
      else
         return (int) Math.Round(temp);
   }

   public long ToInt64(IFormatProvider provider) {
      if (temp < Int64.MinValue || temp > Int64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp));
      else
         return (long) Math.Round(temp);
   }

   public sbyte ToSByte(IFormatProvider provider) {
      if (temp < SByte.MinValue || temp > SByte.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the SByte data type.", temp));
      else
         return (sbyte) temp;
   }

   public float ToSingle(IFormatProvider provider) {
      return (float) temp;
   }

   public virtual string ToString(IFormatProvider provider) {
      return temp.ToString(provider) + "°";
   }

   // If conversionType is implemented by another IConvertible method, call it.
   public virtual object ToType(Type conversionType, IFormatProvider provider) {
      switch (Type.GetTypeCode(conversionType))
      {
         case TypeCode.Boolean:
            return this.ToBoolean(provider);
         case TypeCode.Byte:
            return this.ToByte(provider);
         case TypeCode.Char:
            return this.ToChar(provider);
         case TypeCode.DateTime:
            return this.ToDateTime(provider);
         case TypeCode.Decimal:
            return this.ToDecimal(provider);
         case TypeCode.Double:
            return this.ToDouble(provider);
         case TypeCode.Empty:
            throw new NullReferenceException("The target type is null.");
         case TypeCode.Int16:
            return this.ToInt16(provider);
         case TypeCode.Int32:
            return this.ToInt32(provider);
         case TypeCode.Int64:
            return this.ToInt64(provider);
         case TypeCode.Object:
            // Leave conversion of non-base types to derived classes.
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
         case TypeCode.SByte:
            return this.ToSByte(provider);
         case TypeCode.Single:
            return this.ToSingle(provider);
         case TypeCode.String:
            IConvertible iconv = this;
            return iconv.ToString(provider);
         case TypeCode.UInt16:
            return this.ToUInt16(provider);
         case TypeCode.UInt32:
            return this.ToUInt32(provider);
         case TypeCode.UInt64:
            return this.ToUInt64(provider);
         default:
            throw new InvalidCastException("Conversion not supported.");
      }
   }

   public ushort ToUInt16(IFormatProvider provider) {
      if (temp < UInt16.MinValue || temp > UInt16.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp));
      else
         return (ushort) Math.Round(temp);
   }

   public uint ToUInt32(IFormatProvider provider) {
      if (temp < UInt32.MinValue || temp > UInt32.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp));
      else
         return (uint) Math.Round(temp);
   }

   public ulong ToUInt64(IFormatProvider provider) {
      if (temp < UInt64.MinValue || temp > UInt64.MaxValue)
         throw new OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp));
      else
         return (ulong) Math.Round(temp);
   }
}

public class TemperatureCelsius : Temperature, IConvertible
{
   public TemperatureCelsius(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°C"; 
   }

   // If conversionType is a implemented by another IConvertible method, call it.
   public override object ToType(Type conversionType, IFormatProvider provider) {
      // For non-objects, call base method.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         if (conversionType.Equals(typeof(TemperatureCelsius)))
            return this;
         else if (conversionType.Equals(typeof(TemperatureFahrenheit)))
            return new TemperatureFahrenheit((decimal) this.temp * 9 / 5 + 32);
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }
   }
}

public class TemperatureFahrenheit : Temperature, IConvertible 
{
   public TemperatureFahrenheit(decimal value) : base(value)
   {
   }

   // Override ToString methods.
   public override string ToString()
   {
      return this.ToString(null);
   }

   public override string ToString(IFormatProvider provider)
   {
      return temp.ToString(provider) + "°F"; 
   }

   public override object ToType(Type conversionType, IFormatProvider provider)
   { 
      // For non-objects, call base methood.
      if (Type.GetTypeCode(conversionType) != TypeCode.Object) {
         return base.ToType(conversionType, provider);
      }   
      else
      {   
         // Handle conversion between derived classes.
         if (conversionType.Equals(typeof(TemperatureFahrenheit))) 
            return this;
         else if (conversionType.Equals(typeof(TemperatureCelsius)))
            return new TemperatureCelsius((decimal) (this.temp - 32) * 5 / 9);
         // Unspecified object type: throw an InvalidCastException.
         else
            throw new InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", 
                                           conversionType.Name));
      }                                 
   }
}
```

```vb
Public MustInherit Class Temperature
   Implements IConvertible

   Protected temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Property Value As Decimal
      Get 
         Return Me.temp
      End Get
      Set
         Me.temp = Value
      End Set   
   End Property

   Public Overrides Function ToString() As String
      Return temp.ToString() & "º"
   End Function

   ' IConvertible implementations.
   Public Function GetTypeCode() As TypeCode Implements IConvertible.GetTypeCode
      Return TypeCode.Object
   End Function   

   Public Function ToBoolean(provider As IFormatProvider) As Boolean Implements IConvertible.ToBoolean
      Throw New InvalidCastException(String.Format("Temperature-to-Boolean conversion is not supported."))
   End Function

   Public Function ToByte(provider As IFormatProvider) As Byte Implements IConvertible.ToByte
      If temp < Byte.MinValue Or temp > Byte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Byte data type.", temp))
      Else
         Return CByte(temp)
      End If    
   End Function

   Public Function ToChar(provider As IFormatProvider) As Char Implements IConvertible.ToChar
      Throw New InvalidCastException("Temperature-to-Char conversion is not supported.")
   End Function

   Public Function ToDateTime(provider As IFormatProvider) As DateTime Implements IConvertible.ToDateTime
      Throw New InvalidCastException("Temperature-to-DateTime conversion is not supported.")
   End Function

   Public Function ToDecimal(provider As IFormatProvider) As Decimal Implements IConvertible.ToDecimal
      Return temp
   End Function

   Public Function ToDouble(provider As IFormatProvider) As Double Implements IConvertible.ToDouble
      Return CDbl(temp)
   End Function

   Public Function ToInt16(provider As IFormatProvider) As Int16 Implements IConvertible.ToInt16
      If temp < Int16.MinValue Or temp > Int16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int16 data type.", temp))
      End If
      Return CShort(Math.Round(temp))
   End Function

   Public Function ToInt32(provider As IFormatProvider) As Int32 Implements IConvertible.ToInt32
      If temp < Int32.MinValue Or temp > Int32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int32 data type.", temp))
      End If
      Return CInt(Math.Round(temp))
   End Function

   Public Function ToInt64(provider As IFormatProvider) As Int64 Implements IConvertible.ToInt64
      If temp < Int64.MinValue Or temp > Int64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the Int64 data type.", temp))
      End If
      Return CLng(Math.Round(temp))
   End Function

   Public Function ToSByte(provider As IFormatProvider) As SByte Implements IConvertible.ToSByte
      If temp < SByte.MinValue Or temp > SByte.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the SByte data type.", temp))
      Else
         Return CSByte(temp)
      End If    
   End Function

   Public Function ToSingle(provider As IFormatProvider) As Single Implements IConvertible.ToSingle
      Return CSng(temp)
   End Function

   Public Overridable Overloads Function ToString(provider As IFormatProvider) As String Implements IConvertible.ToString
      Return temp.ToString(provider) & " °C"
   End Function

   ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overridable Function ToType(conversionType As Type, provider As IFormatProvider) As Object Implements IConvertible.ToType
      Select Case Type.GetTypeCode(conversionType)
         Case TypeCode.Boolean
            Return Me.ToBoolean(provider)
         Case TypeCode.Byte
            Return Me.ToByte(provider)
         Case TypeCode.Char
            Return Me.ToChar(provider)   
         Case TypeCode.DateTime
            Return Me.ToDateTime(provider)
         Case TypeCode.Decimal
            Return Me.ToDecimal(provider)
         Case TypeCode.Double
            Return Me.ToDouble(provider)
         Case TypeCode.Empty
            Throw New NullReferenceException("The target type is null.")
         Case TypeCode.Int16
            Return Me.ToInt16(provider)
         Case TypeCode.Int32
            Return Me.ToInt32(provider)
         Case TypeCode.Int64
            Return Me.ToInt64(provider)
         Case TypeCode.Object
            ' Leave conversion of non-base types to derived classes.
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         Case TypeCode.SByte
            Return Me.ToSByte(provider)
         Case TypeCode.Single
            Return Me.ToSingle(provider)
         Case TypeCode.String
            Return Me.ToString(provider)
         Case TypeCode.UInt16
            Return Me.ToUInt16(provider)
         Case TypeCode.UInt32
            Return Me.ToUInt32(provider)
         Case TypeCode.UInt64
            Return Me.ToUInt64(provider)
         Case Else
            Throw New InvalidCastException("Conversion not supported.")   
      End Select
   End Function

   Public Function ToUInt16(provider As IFormatProvider) As UInt16 Implements IConvertible.ToUInt16
      If temp < UInt16.MinValue Or temp > UInt16.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt16 data type.", temp))
      End If
      Return CUShort(Math.Round(temp))
   End Function

   Public Function ToUInt32(provider As IFormatProvider) As UInt32 Implements IConvertible.ToUInt32
      If temp < UInt32.MinValue Or temp > UInt32.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt32 data type.", temp))
      End If
      Return CUInt(Math.Round(temp))
   End Function

   Public Function ToUInt64(provider As IFormatProvider) As UInt64 Implements IConvertible.ToUInt64
      If temp < UInt64.MinValue Or temp > UInt64.MaxValue Then
         Throw New OverflowException(String.Format("{0} is out of range of the UInt64 data type.", temp))
      End If
      Return CULng(Math.Round(temp))
   End Function
End Class

Public Class TemperatureCelsius : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°C" 
   End Function

  ' If conversionType is a implemented by another IConvertible method, call it.
   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base method.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         If conversionType.Equals(GetType(TemperatureCelsius)) Then
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureFahrenheit))
            Return New TemperatureFahrenheit(CDec(Me.temp * 9 / 5 + 32))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _ 
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class

Public Class TemperatureFahrenheit : Inherits Temperature : Implements IConvertible
   Public Sub New(value As Decimal)
      MyBase.New(value)
   End Sub

   ' Override ToString methods.
   Public Overrides Function ToString() As String
      Return Me.ToString(Nothing)
   End Function

   Public Overrides Function ToString(provider As IFormatProvider ) As String
      Return temp.ToString(provider) + "°F" 
   End Function

   Public Overrides Function ToType(conversionType As Type, provider As IFormatProvider) As Object
      ' For non-objects, call base methood.
      If Type.GetTypeCode(conversionType) <> TypeCode.Object Then
         Return MyBase.ToType(conversionType, provider)
      Else   
         ' Handle conversion between derived classes.
         If conversionType.Equals(GetType(TemperatureFahrenheit)) Then 
            Return Me
         ElseIf conversionType.Equals(GetType(TemperatureCelsius))
            Return New TemperatureCelsius(CDec((MyBase.temp - 32) * 5 / 9))
         ' Unspecified object type: throw an InvalidCastException.
         Else
            Throw New InvalidCastException(String.Format("Cannot convert from Temperature to {0}.", _
                                           conversionType.Name))
         End If
      End If                                  
   End Function
End Class
```

O exemplo a seguir ilustra várias chamadas a essas implementações da [IConvertible](xref:System.IConvertible) para converter objetos `TemperatureCelsius` em objetos `TemperatureFahrenheit` e vice-versa.

```csharp
TemperatureCelsius tempC1 = new TemperatureCelsius(0);
TemperatureFahrenheit tempF1 = (TemperatureFahrenheit) Convert.ChangeType(tempC1, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempF1);
TemperatureCelsius tempC2 = (TemperatureCelsius) Convert.ChangeType(tempC1, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempC1, tempC2);
TemperatureFahrenheit tempF2 = new TemperatureFahrenheit(212);
TemperatureCelsius tempC3 = (TemperatureCelsius) Convert.ChangeType(tempF2, typeof(TemperatureCelsius), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempC3);
TemperatureFahrenheit tempF3 = (TemperatureFahrenheit) Convert.ChangeType(tempF2, typeof(TemperatureFahrenheit), null);
Console.WriteLine("{0} equals {1}.", tempF2, tempF3);
// The example displays the following output:
//       0°C equals 32°F.
//       0°C equals 0°C.
//       212°F equals 100°C.
//       212°F equals 212°F.
```

```vb
Dim tempC1 As New TemperatureCelsius(0)
Dim tempF1 As TemperatureFahrenheit = CType(Convert.ChangeType(tempC1, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempC1, tempF1) 
Dim tempC2 As TemperatureCelsius = CType(Convert.ChangeType(tempC1, GetType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempC1, tempC2) 
Dim tempF2 As New TemperatureFahrenheit(212)
Dim tempC3 As TEmperatureCelsius = CType(Convert.ChangeType(tempF2, GEtType(TemperatureCelsius), Nothing), TemperatureCelsius)
Console.WriteLine("{0} equals {1}.", tempF2, tempC3) 
Dim tempF3 As TemperatureFahrenheit = CType(Convert.ChangeType(tempF2, GetType(TemperatureFahrenheit), Nothing), TemperatureFahrenheit)
Console.WriteLine("{0} equals {1}.", tempF2, tempF3)
' The example displays the following output:
'       0°C equals 32°F.
'       0°C equals 0°C.
'       212°F equals 100°C.
'       212°F equals 212°F.
```

## <a name="the-typeconverter-class"></a>A classe TypeConverter

O .NET também permite definir um conversor de tipo para um tipo personalizado, estendendo a classe [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) e associando o conversor de tipo ao tipo por meio de um atributo [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute). A tabela a seguir realça as diferenças entre esta abordagem e a implementação da interface [IConvertible](xref:System.IConvertible) para um tipo personalizado.

> [!NOTE]
> O suporte no tempo de design somente poderá ser fornecido para um tipo personalizado se houver um conversor de tipo definido para ele.

Conversão usando TypeConverter | Conversão usando IConvertible
------------------------------ | -----------------------------
É implementada para um tipo personalizado por meio da derivação de uma classe separada de [TypeConverter](xref:System.ComponentModel.TypeConverter). Essa classe derivada é associada ao tipo personalizado aplicando um atributo [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute). | É implementada por um tipo personalizado para executar a conversão. Um usuário do tipo invoca um método de conversão de [IConvertible](xref:System.IConvertible) no tipo.
Pode ser usada tanto no tempo de design quanto no tempo de execução. | Somente pode ser usada no tempo de execução.
Usa reflexão e, consequentemente, é mais lenta do que a conversão habilitada por [IConvertible](xref:System.IConvertible). | Não usa reflexão.
Permite conversões de tipo bidirecionais do tipo personalizado para outros tipos de dados e de outros tipos de dados para o tipo personalizado. Por exemplo, um [TypeConverter](xref:System.ComponentModel.TypeConverter) definido para `MyType` permite conversões de `MyType` em [String](xref:System.String) e de [String](xref:System.String) em `MyType`. | Permite a conversão de um tipo personalizado em outros tipos de dados, mas não de outros tipos de dados em um tipo personalizado.

Para obter mais informações de como usar conversores de tipo para realizar conversões, consulte [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter).

## <a name="see-also"></a>Consulte também

[System.Convert](xref:System.Convert)

[IConvertible](xref:System.IConvertible)

[Tabelas de conversão de tipos](conversion-tables.md)
