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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 0a774a170b7703b900c2044708b07faeb4e51548
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="type-conversion"></a><span data-ttu-id="8637c-104">Conversão de tipos</span><span class="sxs-lookup"><span data-stu-id="8637c-104">Type conversion</span></span>

<span data-ttu-id="8637c-105">Cada valor tem um tipo associado, o qual define atributos como a quantidade de espaço alocado para o valor, o intervalo de valores possíveis que ele pode assumir e os membros que ele disponibiliza.</span><span class="sxs-lookup"><span data-stu-id="8637c-105">Every value has an associated type, which defines attributes such as the amount of space allocated to the value, the range of possible values it can have, and the members that it makes available.</span></span> <span data-ttu-id="8637c-106">Muitos valores podem ser expressos por mais de um tipo.</span><span class="sxs-lookup"><span data-stu-id="8637c-106">Many values can be expressed as more than one type.</span></span> <span data-ttu-id="8637c-107">Por exemplo, o valor de `4` pode ser expresso como um inteiro ou um valor de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="8637c-107">For example, the value `4` can be expressed as an integer or a floating-point value.</span></span> <span data-ttu-id="8637c-108">A conversão de tipo cria um valor em um novo tipo que é equivalente ao valor de um tipo antigo, mas que não necessariamente preserva a identidade (ou o valor exato) do objeto original.</span><span class="sxs-lookup"><span data-stu-id="8637c-108">Type conversion creates a value in a new type that is equivalent to the value of an old type, but does not necessarily preserve the identity (or exact value) of the original object.</span></span>

<span data-ttu-id="8637c-109">O .NET oferece suporte automaticamente às seguintes conversões:</span><span class="sxs-lookup"><span data-stu-id="8637c-109">.NET automatically supports the following conversions:</span></span>

* <span data-ttu-id="8637c-110">Conversão de uma classe derivada em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="8637c-110">Conversion from a derived class to a base class.</span></span> <span data-ttu-id="8637c-111">Isso significa, por exemplo, que uma instância de qualquer classe ou estrutura pode ser convertida em uma instância de [Objeto](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="8637c-111">This means, for example, that an instance of any class or structure can be converted to an [Object](xref:System.Object) instance.</span></span> <span data-ttu-id="8637c-112">Essa conversão não exige um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-112">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="8637c-113">Conversão de uma classe base para a classe derivada original.</span><span class="sxs-lookup"><span data-stu-id="8637c-113">Conversion from a base class back to the original derived class.</span></span> <span data-ttu-id="8637c-114">No C#, essa conversão exige um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-114">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="8637c-115">No Visual Basic, ela exige o operador `CType` quando a `Option Strict` está ativada.</span><span class="sxs-lookup"><span data-stu-id="8637c-115">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

* <span data-ttu-id="8637c-116">Conversão de um tipo que implementa uma interface para um objeto de interface que representa essa interface.</span><span class="sxs-lookup"><span data-stu-id="8637c-116">Conversion from a type that implements an interface to an interface object that represents that interface.</span></span> <span data-ttu-id="8637c-117">Essa conversão não exige um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-117">This conversion does not require a casting operator.</span></span>

* <span data-ttu-id="8637c-118">Conversão de um objeto de interface de volta para o tipo original que implementa essa interface.</span><span class="sxs-lookup"><span data-stu-id="8637c-118">Conversion from an interface object back to the original type that implements that interface.</span></span> <span data-ttu-id="8637c-119">No C#, essa conversão exige um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-119">In C#, this conversion requires a casting operator.</span></span> <span data-ttu-id="8637c-120">No Visual Basic, ela exige o operador `CType` quando a `Option Strict` está ativada.</span><span class="sxs-lookup"><span data-stu-id="8637c-120">In Visual Basic, it requires the `CType` operator if `Option Strict` is on.</span></span> 

<span data-ttu-id="8637c-121">Além dessas conversões automáticas, o .NET fornece várias funcionalidades que oferecem suporte à conversão personalizada de tipo.</span><span class="sxs-lookup"><span data-stu-id="8637c-121">In addition to these automatic conversions, .NET provides several features that support custom type conversion.</span></span> <span data-ttu-id="8637c-122">Eles incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8637c-122">These include the following:</span></span> 

* <span data-ttu-id="8637c-123">O operador `Implicit`, que define as conversões de ampliação disponíveis entre tipos.</span><span class="sxs-lookup"><span data-stu-id="8637c-123">The `Implicit` operator, which defines the available widening conversions between types.</span></span> <span data-ttu-id="8637c-124">Para obter mais informações, consulte a seção [Conversão implícita com o operador implícito](#implicit-conversion-with-the-implicit-operator).</span><span class="sxs-lookup"><span data-stu-id="8637c-124">For more information, see the [Implicit conversion with the Implicit operator](#implicit-conversion-with-the-implicit-operator) section.</span></span>

* <span data-ttu-id="8637c-125">O operador `Explicit`, que define as conversões de redução disponíveis entre tipos.</span><span class="sxs-lookup"><span data-stu-id="8637c-125">The `Explicit` operator, which defines the available narrowing conversions between types.</span></span> <span data-ttu-id="8637c-126">Para obter mais informações, consulte a seção [Conversão explícita com o operador explícito](#explicit-conversion-with-the-explicit-operator).</span><span class="sxs-lookup"><span data-stu-id="8637c-126">For more information, see the [Explicit conversion with the Explicit operator](#explicit-conversion-with-the-explicit-operator) section.</span></span>

* <span data-ttu-id="8637c-127">A interface [IConvertible](xref:System.IConvertible), que define as conversões para cada um dos tipos de dados base do .NET.</span><span class="sxs-lookup"><span data-stu-id="8637c-127">The [IConvertible](xref:System.IConvertible) interface, which defines conversions to each of the base .NET data types.</span></span> <span data-ttu-id="8637c-128">Para obter mais informações, consulte a seção [A interface IConvertible](#the-iconvertible-interface).</span><span class="sxs-lookup"><span data-stu-id="8637c-128">For more information, see the [The IConvertible interface](#the-iconvertible-interface) section.</span></span>

* <span data-ttu-id="8637c-129">A classe [Convert](xref:System.Convert), que fornece um conjunto de métodos que implementam os métodos na interface `IConvertible`.</span><span class="sxs-lookup"><span data-stu-id="8637c-129">The [Convert](xref:System.Convert) class, which provides a set of methods that implement the methods in the `IConvertible` interface.</span></span> <span data-ttu-id="8637c-130">Para obter mais informações, consulte a seção [A classe Convert](#the-convert-class).</span><span class="sxs-lookup"><span data-stu-id="8637c-130">For more information, see the [The Convert class](#the-convert-class) section.</span></span>

* <span data-ttu-id="8637c-131">A classe [TypeConverter](xref:System.ComponentModel.TypeConverter), que é uma classe base que pode ser estendida para oferecer suporte à conversão de um tipo especificado em qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="8637c-131">The [TypeConverter](xref:System.ComponentModel.TypeConverter) class, which is a base class that can be extended to support the conversion of a specified type to any other type.</span></span> <span data-ttu-id="8637c-132">Para obter mais informações, consulte a seção [A classe TypeConverter](#the-typeconverter-class).</span><span class="sxs-lookup"><span data-stu-id="8637c-132">For more information, see the [The TypeConverter class](#the-typeconverter-class) section.</span></span>

## <a name="implicit-conversion-with-the-implicit-operator"></a><span data-ttu-id="8637c-133">Conversão implícita com o operador implícito</span><span class="sxs-lookup"><span data-stu-id="8637c-133">Implicit conversion with the Implicit operator</span></span>

<span data-ttu-id="8637c-134">As conversões de ampliação envolvem a criação de um novo valor do valor de um tipo existente que tem um intervalo mais restritivo ou uma lista de membros mais restrita que o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="8637c-134">Widening conversions involve the creation of a new value from the value of an existing type that has either a more restrictive range or a more restricted member list than the target type.</span></span> <span data-ttu-id="8637c-135">As conversões de ampliação não podem resultar na perda de dados (mas podem resultar em uma perda de precisão).</span><span class="sxs-lookup"><span data-stu-id="8637c-135">Widening conversions cannot result in data loss (although they may result in a loss of precision).</span></span> <span data-ttu-id="8637c-136">Como os dados não podem ser perdidos, os compiladores podem tratar a conversão de forma implícita ou transparente, sem exigir o uso de um método de conversão explícita ou de um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-136">Because data cannot be lost, compilers can handle the conversion implicitly or transparently, without requiring the use of an explicit conversion method or a casting operator.</span></span>

> [!NOTE]
> <span data-ttu-id="8637c-137">Embora o código que executa uma conversão implícita possa chamar um método de conversão ou usar um operador de conversão, seu uso não é exigido pelos compiladores que oferecem suporte a conversões implícitas.</span><span class="sxs-lookup"><span data-stu-id="8637c-137">Although code that performs an implicit conversion can call a conversion method or use a casting operator, their use is not required by compilers that support implicit conversions.</span></span>

<span data-ttu-id="8637c-138">Por exemplo, o tipo [Decimal](xref:System.Decimal) oferece suporte a conversões implícitas de valores de [Byte](xref:System.Byte), [Char](xref:System.Char), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) e [UInt64](xref:System.UInt64).</span><span class="sxs-lookup"><span data-stu-id="8637c-138">For example, the [Decimal](xref:System.Decimal) type supports implicit conversions from [Byte](xref:System.Byte), [Char](xref:System.Char), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64) values.</span></span> <span data-ttu-id="8637c-139">O exemplo a seguir ilustra algumas dessas conversões implícitas ao atribuir valores a uma variável `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="8637c-139">The following example illustrates some of these implicit conversions in assigning values to a `Decimal` variable.</span></span>

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

<span data-ttu-id="8637c-140">Se o compilador de uma linguagem específica oferecer suporte a operadores personalizados, você também poderá definir conversões implícitas em seus próprios tipos personalizados.</span><span class="sxs-lookup"><span data-stu-id="8637c-140">If a particular language compiler supports custom operators, you can also define implicit conversions in your own custom types.</span></span> <span data-ttu-id="8637c-141">O exemplo a seguir oferece uma implementação parcial de um tipo de dados de byte assinado chamado `ByteWithSign` que usa a representação de sinal e magnitude.</span><span class="sxs-lookup"><span data-stu-id="8637c-141">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="8637c-142">Ele oferece suporte à conversão implícita de valores de [Byte](xref:System.Byte) e [SByte](xref:System.SByte) em valores de `ByteWithSign`.</span><span class="sxs-lookup"><span data-stu-id="8637c-142">It supports implicit conversion of [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values to `ByteWithSign` values.</span></span>

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

<span data-ttu-id="8637c-143">O código cliente pode então declarar uma variável `ByteWithSign` e atribuir a ela valores de [Byte](xref:System.Byte) e [SByte](xref:System.SByte) sem executar nenhuma conversão explícita ou usar operadores de conversão, conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8637c-143">Client code can then declare a `ByteWithSign` variable and assign it [Byte](xref:System.Byte) and [SByte](xref:System.SByte) values without performing any explicit conversions or using any casting operators, as the following example shows.</span></span>

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

## <a name="explicit-conversion-with-the-explicit-operator"></a><span data-ttu-id="8637c-144">Conversão explícita com o operador explícito</span><span class="sxs-lookup"><span data-stu-id="8637c-144">Explicit conversion with the Explicit operator</span></span>

<span data-ttu-id="8637c-145">As conversões de redução envolvem a criação de um novo valor com o valor de um tipo existente que tem um intervalo mais amplo ou uma lista de membros maior do que o tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="8637c-145">Narrowing conversions involve the creation of a new value from the value of an existing type that has either a greater range or a larger member list than the target type.</span></span> <span data-ttu-id="8637c-146">Como uma conversão de redução pode resultar em uma perda de dados, os compiladores geralmente exigem que a conversão se torne explícita por meio da chamada de um método de conversão ou de um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-146">Because a narrowing conversion can result in a loss of data, compilers often require that the conversion be made explicit through a call to a conversion method or a casting operator.</span></span> <span data-ttu-id="8637c-147">Ou seja, a conversão deve ser tratada explicitamente no código do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="8637c-147">That is, the conversion must be handled explicitly in developer code.</span></span> 

> [!NOTE]
> <span data-ttu-id="8637c-148">A finalidade principal de exigir um método de conversão ou um operador de conversão para reduzir conversões é fazer com que o desenvolvedor saiba sobre a possibilidade de perda de dados ou de uma [OverflowException](xref:System.OverflowException) para que ela possa ser tratada no código.</span><span class="sxs-lookup"><span data-stu-id="8637c-148">The major purpose of requiring a conversion method or casting operator for narrowing conversions is to make the developer aware of the possibility of data loss or an [OverflowException](xref:System.OverflowException) so that it can be handled in code.</span></span> <span data-ttu-id="8637c-149">No entanto, alguns compiladores podem amenizar esse requisito.</span><span class="sxs-lookup"><span data-stu-id="8637c-149">However, some compilers can relax this requirement.</span></span> <span data-ttu-id="8637c-150">Por exemplo, no Visual Basic, se a `Option Strict` estiver desativada (sua configuração padrão), o compilador do Visual Basic tentará executar as conversões de redução de forma implícita.</span><span class="sxs-lookup"><span data-stu-id="8637c-150">For example, in Visual Basic, if `Option Strict` is off (its default setting), the Visual Basic compiler tries to perform narrowing conversions implicitly.</span></span>

<span data-ttu-id="8637c-151">Por exemplo, os tipos de dados [UInt32](xref:System.UInt32), [Int64](xref:System.Int64) e [UInt64](xref:System.UInt64) têm intervalos que excedem o do tipo de dados [Int32](xref:System.Int32), conforme é mostrado na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8637c-151">For example, the [UInt32](xref:System.UInt32), [Int64](xref:System.Int64), and [UInt64](xref:System.UInt64) data types have ranges that exceed that the [Int32](xref:System.Int32) data type, as the following table shows.</span></span>

<span data-ttu-id="8637c-152">Tipo</span><span class="sxs-lookup"><span data-stu-id="8637c-152">Type</span></span> | <span data-ttu-id="8637c-153">Comparação com intervalo de Int32</span><span class="sxs-lookup"><span data-stu-id="8637c-153">Comparison with range of Int32</span></span>
---- | ------------------------------
[<span data-ttu-id="8637c-154">Int64</span><span class="sxs-lookup"><span data-stu-id="8637c-154">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="8637c-155">[Int64.MaxValue](xref:System.Int64.MaxValue) é maior que [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue) e [Int64.MinValue](xref:System.Int64.MinValue) é menor que (tem um intervalo negativo maior que) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue).</span><span class="sxs-lookup"><span data-stu-id="8637c-155">[Int64.MaxValue](xref:System.Int64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32#System_Int32_MaxValue), and [Int64.MinValue](xref:System.Int64.MinValue) is less than (has a greater negative range than) [Int32.MinValue](xref:System.Int32#System_Int32_MinValue).</span></span>
[<span data-ttu-id="8637c-156">UInt32</span><span class="sxs-lookup"><span data-stu-id="8637c-156">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="8637c-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) é maior que [Int32.MaxValue](xref:System.Int32.MaxValue).</span><span class="sxs-lookup"><span data-stu-id="8637c-157">[UInt32.MaxValue](xref:System.UInt32.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>
[<span data-ttu-id="8637c-158">UInt64</span><span class="sxs-lookup"><span data-stu-id="8637c-158">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="8637c-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) é maior que [Int32.MaxValue](xref:System.Int32.MaxValue).</span><span class="sxs-lookup"><span data-stu-id="8637c-159">[UInt64.MaxValue](xref:System.UInt64.MaxValue) is greater than [Int32.MaxValue](xref:System.Int32.MaxValue).</span></span>

<span data-ttu-id="8637c-160">Para tratar essas conversões de redução, o .NET permite que os tipos definam um operador `Explicit`.</span><span class="sxs-lookup"><span data-stu-id="8637c-160">To handle such narrowing conversions, .NET allows types to define an `Explicit` operator.</span></span> <span data-ttu-id="8637c-161">Os compiladores de linguagens individuais podem então implementar esse operador usando suas próprias sintaxes ou um membro da classe [Convert](xref:System.Convert) pode ser chamado para executar a conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-161">Individual language compilers can then implement this operator using their own syntax, or a member of the [Convert](xref:System.Convert) class can be called to perform the conversion.</span></span> <span data-ttu-id="8637c-162">(Para obter mais informações sobre a classe `Convert`, consulte [A classe Convert](#the-convert-class) mais adiante neste tópico.) O exemplo a seguir ilustra o uso das funcionalidades de linguagem para lidar com a conversão explícita destes valores inteiros que podem estar fora do intervalo em valores [Int32](xref:System.Int32).</span><span class="sxs-lookup"><span data-stu-id="8637c-162">(For more information about the `Convert` class, see [The Convert class](#the-convert-class) later in this topic.) The following example illustrates the use of language features to handle the explicit conversion of these potentially out-of-range integer values to [Int32](xref:System.Int32) values.</span></span> 

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

<span data-ttu-id="8637c-163">As conversões explícitas podem produzir resultados diferentes em linguagens diferentes e esses resultados podem diferir do valor retornado pelo método [Convert](xref:System.Convert) correspondente.</span><span class="sxs-lookup"><span data-stu-id="8637c-163">Explicit conversions can produce different results in different languages, and these results can differ from the value returned by the corresponding [Convert](xref:System.Convert) method.</span></span> <span data-ttu-id="8637c-164">Por exemplo, se o valor **12.63251** de [Double](xref:System.Double) for convertido em um [Int32](xref:System.Int32), tanto o método [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) do .NET quanto o `CInt` do Visual Basic arredondarão o [Double](xref:System.Double) para retornar o valor **13**, mas o operador `(int)` do C# truncará o [Double](xref:System.Double) para retornar o valor **12**.</span><span class="sxs-lookup"><span data-stu-id="8637c-164">For example, if the [Double](xref:System.Double) value **12.63251** is converted to an [Int32](xref:System.Int32), both the .NET [Convert.ToInt32(Double)](xref:System.Convert.ToInt32(System.Double)) and the Visual Basic `CInt` method method rounds the [Double](xref:System.Double) to return a value of **13**, but the C# `(int)` operator truncates the [Double](xref:System.Double) to return a value of **12**.</span></span> <span data-ttu-id="8637c-165">Da mesma forma, o operador `(int)` do C# não oferece suporte à conversão de booliano em inteiro, mas o método `CInt` do Visual Basic converte um valor `true` em **-1**.</span><span class="sxs-lookup"><span data-stu-id="8637c-165">Similarly, the C# `(int)` operator does not support Boolean-to-integer conversion, but the Visual Basic `CInt` method converts a value of `true` to **-1**.</span></span> <span data-ttu-id="8637c-166">Por outro lado, o método [Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) converte um valor `true` em **1**.</span><span class="sxs-lookup"><span data-stu-id="8637c-166">On the other hand, the [Convert.ToInt32(Boolean)](xref:System.Convert.ToInt32(System.Boolean)) method converts a value of `true` to **1**.</span></span>

<span data-ttu-id="8637c-167">A maioria dos compiladores permite que as conversões explícitas sejam executadas de forma verificada ou não verificada.</span><span class="sxs-lookup"><span data-stu-id="8637c-167">Most compilers allow explicit conversions to be performed in a checked or unchecked manner.</span></span> <span data-ttu-id="8637c-168">Quando uma conversão verificada é executada, uma [OverflowException](xref:System.OverflowException) é gerada quando o valor do tipo a ser convertido está fora do intervalo do tipo de destino.</span><span class="sxs-lookup"><span data-stu-id="8637c-168">When a checked conversion is performed, an [OverflowException](xref:System.OverflowException) is thrown when the value of the type to be converted is outside the range of the target type.</span></span> <span data-ttu-id="8637c-169">Quando uma conversão não verificada é executada nas mesmas condições, a conversão pode não gerar uma exceção, mas o comportamento exato se tornará indefinido e um valor incorreto poderá ser produzido.</span><span class="sxs-lookup"><span data-stu-id="8637c-169">When an unchecked conversion is performed under the same conditions, the conversion might not throw an exception, but the exact behavior becomes undefined and an incorrect value might result.</span></span>

> [!NOTE]
> <span data-ttu-id="8637c-170">No C#, as conversões verificadas podem ser executadas usando a palavra-chave `checked` juntamente com um operador de conversão ou por meio da especificação da opção do compilador `/checked+`.</span><span class="sxs-lookup"><span data-stu-id="8637c-170">In C#, checked conversions can be performed by using the `checked` keyword together with a casting operator, or by specifying the `/checked+` compiler option.</span></span> <span data-ttu-id="8637c-171">Por outro lado, as conversões não verificadas podem ser executadas usando a palavra-chave `unchecked` juntamente com o operador de conversão ou especificando a opção do compilador `/checked-`.</span><span class="sxs-lookup"><span data-stu-id="8637c-171">Conversely, unchecked conversions can be performed by using the `unchecked` keyword together with the casting operator, or by specifying the `/checked-` compiler option.</span></span> <span data-ttu-id="8637c-172">Por padrão, as conversões explícitas são do tipo não verificadas.</span><span class="sxs-lookup"><span data-stu-id="8637c-172">By default, explicit conversions are unchecked.</span></span> <span data-ttu-id="8637c-173">No Visual Basic, as conversões verificadas podem ser executadas especificando a opção do compilador `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="8637c-173">In Visual Basic, checked conversions can be performed by specifying the `/removeintchecks-` compiler option.</span></span> <span data-ttu-id="8637c-174">Por outro lado, as conversões não verificadas podem ser executadas especificando a opção do compilador `/removeintchecks+`.</span><span class="sxs-lookup"><span data-stu-id="8637c-174">Conversely, unchecked conversions can be performed by specifying the `/removeintchecks+` compiler option.</span></span> <span data-ttu-id="8637c-175">Por padrão, as conversões explícitas são do tipo verificadas.</span><span class="sxs-lookup"><span data-stu-id="8637c-175">By default, explicit conversions are checked.</span></span>

<span data-ttu-id="8637c-176">O exemplo do C# a seguir usa as palavras-chave `checked` e `unchecked` para ilustrar a diferença no comportamento quando um valor fora do intervalo de [Byte](xref:System.Byte) é convertido em `Byte`.</span><span class="sxs-lookup"><span data-stu-id="8637c-176">The following C# example uses the `checked` and `unchecked` keywords to illustrate the difference in behavior when a value outside the range of a [Byte](xref:System.Byte) is converted to a `Byte`.</span></span> <span data-ttu-id="8637c-177">A conversão verificada gera uma exceção, mas a conversão não verificada atribui [Byte.MaxValue](xref:System.Byte.MaxValue) à variável `Byte`.</span><span class="sxs-lookup"><span data-stu-id="8637c-177">The checked conversion throws an exception, but the unchecked conversion assigns [Byte.MaxValue](xref:System.Byte.MaxValue) to the `Byte` variable.</span></span>

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

<span data-ttu-id="8637c-178">Se o compilador de uma linguagem específica der suporte a operadores sobrecarregados personalizados, você também poderá definir as conversões explícitas em seus próprios tipos personalizados.</span><span class="sxs-lookup"><span data-stu-id="8637c-178">If a particular language compiler supports custom overloaded operators, you can also define explicit conversions in your own custom types.</span></span> <span data-ttu-id="8637c-179">O exemplo a seguir oferece uma implementação parcial de um tipo de dados de byte assinado chamado `ByteWithSign` que usa a representação de sinal e magnitude.</span><span class="sxs-lookup"><span data-stu-id="8637c-179">The following example provides a partial implementation of a signed byte data type named `ByteWithSign` that uses sign-and-magnitude representation.</span></span> <span data-ttu-id="8637c-180">Ele oferece suporte à conversão explícita de valores de [Int32](xref:System.Int32) e [UInt32](xref:System.UInt32) em valores de `ByteWithSign`.</span><span class="sxs-lookup"><span data-stu-id="8637c-180">It supports explicit conversion of [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values to `ByteWithSign` values.</span></span>

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

<span data-ttu-id="8637c-181">O código cliente poderá então declarar uma variável `ByteWithSign` e atribuir valores de [Int32](xref:System.Int32) e [UInt32](xref:System.UInt32) a ela se as atribuições incluírem um operador de conversão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8637c-181">Client code can then declare a `ByteWithSign` variable and assign it [Int32](xref:System.Int32) and [UInt32](xref:System.UInt32) values if the assignments include a casting operator, as the following example shows.</span></span>

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

## <a name="the-iconvertible-interface"></a><span data-ttu-id="8637c-182">A interface IConvertible</span><span class="sxs-lookup"><span data-stu-id="8637c-182">The IConvertible interface</span></span>

<span data-ttu-id="8637c-183">Para oferecer suporte à conversão de qualquer tipo em um tipo base do Common Language Runtime, o .NET oferece a interface [IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="8637c-183">To support the conversion of any type to a common language runtime base type, .NET provides the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="8637c-184">O tipo de implementação é necessário para fornecer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="8637c-184">The implementing type is required to provide the following:</span></span>

* <span data-ttu-id="8637c-185">Um método que retorne o [TypeCode](xref:System.TypeCode) do tipo de implementação.</span><span class="sxs-lookup"><span data-stu-id="8637c-185">A method that returns the [TypeCode](xref:System.TypeCode) of the implementing type.</span></span>

* <span data-ttu-id="8637c-186">Métodos para converter o tipo de implementação em cada tipo base do Common Language Runtime ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double) e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="8637c-186">Methods to convert the implementing type to each common language runtime base type ([Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), and so on).</span></span>

* <span data-ttu-id="8637c-187">Um método de conversão generalizado para converter uma instância do tipo de implementação em outro tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="8637c-187">A generalized conversion method to convert an instance of the implementing type to another specified type.</span></span> <span data-ttu-id="8637c-188">As conversões sem suporte devem gerar uma [InvalidCastException](xref:System.InvalidCastException).</span><span class="sxs-lookup"><span data-stu-id="8637c-188">Conversions that are not supported should throw an [InvalidCastException](xref:System.InvalidCastException).</span></span>

<span data-ttu-id="8637c-189">Cada tipo base do Common Language Runtime, ou seja, os tipos [Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [String](xref:System.String), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32) e [UInt64](xref:System.UInt64), além de [DBNull](xref:System.DBNull) e [Enum](xref:System.Enum), implementam a interface [IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="8637c-189">Each common language runtime base type (that is, the [Boolean](xref:System.Boolean), [Byte](xref:System.Byte), [Char](xref:System.Char), [DateTime](xref:System.DateTime), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [String](xref:System.String), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), and [UInt64](xref:System.UInt64), as well as the [DBNull](xref:System.DBNull) and [Enum](xref:System.Enum) types, implement the [IConvertible](xref:System.IConvertible) interface.</span></span> <span data-ttu-id="8637c-190">No entanto, essas são implementações de interfaces explícitas. O método de conversão somente pode ser chamado por meio de uma variável da interface [IConvertible](xref:System.IConvertible), conforme é mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8637c-190">However, these are explicit interface implementations; the conversion method can be called only through an [IConvertible](xref:System.IConvertible) interface variable, as the following example shows.</span></span> <span data-ttu-id="8637c-191">Este exemplo converte um valor de [Int32](xref:System.Int32) em seu valor de [Char](xref:System.Char) equivalente.</span><span class="sxs-lookup"><span data-stu-id="8637c-191">This example converts an [Int32](xref:System.Int32) value to its equivalent [Char](xref:System.Char) value.</span></span>

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

<span data-ttu-id="8637c-192">O requisito para chamar o método de conversão em sua interface, em vez de no tipo de implementação, torna as implementações de interfaces explícitas relativamente dispendiosas.</span><span class="sxs-lookup"><span data-stu-id="8637c-192">The requirement to call the conversion method on its interface rather than on the implementing type makes explicit interface implementations relatively expensive.</span></span> <span data-ttu-id="8637c-193">Em vez disso, recomendamos que você chame o membro apropriado da classe [Convert](xref:System.Convert) para converter entre tipos base do Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="8637c-193">Instead, we recommend that you call the appropriate member of the [Convert](xref:System.Convert) class to convert between common language runtime base types.</span></span> <span data-ttu-id="8637c-194">Para obter mais informações, consulte a próxima seção: [A classe Convert](#the-convert-class).</span><span class="sxs-lookup"><span data-stu-id="8637c-194">For more information, see the next section, [The Convert class](#the-convert-class).</span></span> 

> [!NOTE]
> <span data-ttu-id="8637c-195">Além da interface [IConvertible](xref:System.IConvertible) e da classe [Convert](xref:System.Convert) fornecidas pelo .NET, as linguagens individuais também podem fornecer formas de executar conversões.</span><span class="sxs-lookup"><span data-stu-id="8637c-195">In addition to the [IConvertible](xref:System.IConvertible) interface and the [Convert](xref:System.Convert) class provided by .NET, individual languages may also provide ways to perform conversions.</span></span> <span data-ttu-id="8637c-196">Por exemplo, o C# usa operadores de conversão e Visual Basic usa funções de conversão implementadas no compilador, como `CType`,`CInt` e `DirectCast`.</span><span class="sxs-lookup"><span data-stu-id="8637c-196">For example, C# uses casting operators; Visual Basic uses compiler-implemented conversion functions such as `CType`, `CInt`, and `DirectCast`.</span></span>

<span data-ttu-id="8637c-197">Em grande parte, a interface [IConvertible](xref:System.IConvertible) é criada para oferecer suporte à conversão entre os tipos base no NET.</span><span class="sxs-lookup"><span data-stu-id="8637c-197">For the most part, the [IConvertible](xref:System.IConvertible) interface is designed to support conversion between the base types in .NET.</span></span> <span data-ttu-id="8637c-198">No entanto, a interface também pode ser implementada por um tipo personalizado para oferecer suporte à conversão desse tipo em outros tipos personalizados.</span><span class="sxs-lookup"><span data-stu-id="8637c-198">However, the interface can also be implemented by a custom type to support conversion of that type to other custom types.</span></span> <span data-ttu-id="8637c-199">Para obter mais informações, consulte a seção [Conversões personalizadas com o método ChangeType](#custom-conversions-with-the-changetype-method) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="8637c-199">For more information, see the section [Custom conversions with the ChangeType method](#custom-conversions-with-the-changetype-method) later in this topic.</span></span>

## <a name="the-convert-class"></a><span data-ttu-id="8637c-200">A classe Convert</span><span class="sxs-lookup"><span data-stu-id="8637c-200">The Convert class</span></span>

<span data-ttu-id="8637c-201">Embora a implementação da interface [IConvertible](xref:System.IConvertible) de cada tipo base possa ser chamada para executar uma conversão de tipo, chamar os métodos da classe [System.Convert](xref:System.Convert) é a maneira com neutralidade de idioma recomendada para converter de um tipo base em outro.</span><span class="sxs-lookup"><span data-stu-id="8637c-201">Although each base type's [IConvertible](xref:System.IConvertible) interface implementation can be called to perform a type conversion, calling the methods of the [System.Convert](xref:System.Convert) class is the recommended language-neutral way to convert from one base type to another.</span></span> <span data-ttu-id="8637c-202">Além disso, o método [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) pode ser usado para converter de um tipo personalizado especificado em outro tipo.</span><span class="sxs-lookup"><span data-stu-id="8637c-202">In addition, the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method can be used to convert from a specified custom type to another type.</span></span> 

### <a name="conversions-between-base-types"></a><span data-ttu-id="8637c-203">Conversões entre tipos base</span><span class="sxs-lookup"><span data-stu-id="8637c-203">Conversions between base types</span></span>

<span data-ttu-id="8637c-204">A classe [Convert](xref:System.Convert) fornece uma maneira com neutralidade de idioma de realizar conversões entre tipos base e está disponível para todas as linguagens que visam o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="8637c-204">The [Convert](xref:System.Convert) class provides a language-neutral way to perform conversions between base types and is available to all languages that target the common language runtime.</span></span> <span data-ttu-id="8637c-205">Ela fornece um conjunto completo de métodos para conversões de ampliação e de redução e gera uma [InvalidCastException](xref:System.InvalidCastException) para as conversões que não têm suporte (como a conversão de um valor de [DateTime](xref:System.DateTime) em um valor inteiro).</span><span class="sxs-lookup"><span data-stu-id="8637c-205">It provides a complete set of methods for both widening and narrowing conversions, and throws an [InvalidCastException](xref:System.InvalidCastException) for conversions that are not supported (such as the conversion of a [DateTime](xref:System.DateTime) value to an integer value).</span></span> <span data-ttu-id="8637c-206">As conversões de redução são executadas em um contexto verificado e uma [OverflowException](xref:System.OverflowException) será gerada se a conversão falhar.</span><span class="sxs-lookup"><span data-stu-id="8637c-206">Narrowing conversions are performed in a checked context, and an [OverflowException](xref:System.OverflowException) is thrown if the conversion fails.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8637c-207">Como a classe [Convert](xref:System.Convert) inclui métodos para converter de/para cada tipo base, ela elimina a necessidade de chamar a implementação de interface explicita [IConvertible](xref:System.IConvertible) de cada tipo base.</span><span class="sxs-lookup"><span data-stu-id="8637c-207">Because the [Convert](xref:System.Convert) class includes methods to convert to and from each base type, it eliminates the need to call each base type's [IConvertible](xref:System.IConvertible) explicit interface implementation.</span></span>

<span data-ttu-id="8637c-208">O exemplo a seguir ilustra o uso da classe [System.Convert](xref:System.Convert) para executar várias conversões de ampliação e redução entre os tipos base do .NET.</span><span class="sxs-lookup"><span data-stu-id="8637c-208">The following example illustrates the use of the [System.Convert](xref:System.Convert) class to perform several widening and narrowing conversions between .NET base types.</span></span>

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

<span data-ttu-id="8637c-209">Em alguns casos, principalmente na conversão de/para valores de ponto flutuante, uma conversão pode envolver uma perda de precisão, mesmo que não gere uma [OverflowException](xref:System.OverflowException).</span><span class="sxs-lookup"><span data-stu-id="8637c-209">In some cases, particularly when converting to and from floating-point values, a conversion may involve a loss of precision, even though it does not throw an [OverflowException](xref:System.OverflowException).</span></span> <span data-ttu-id="8637c-210">O exemplo a seguir ilustra essa perda de precisão.</span><span class="sxs-lookup"><span data-stu-id="8637c-210">The following example illustrates this loss of precision.</span></span> <span data-ttu-id="8637c-211">No primeiro caso, um valor de [Decimal](xref:System.Decimal) tem menos precisão (menos dígitos significativos) quando é convertido em [Double](xref:System.Double).</span><span class="sxs-lookup"><span data-stu-id="8637c-211">In the first case, a [Decimal](xref:System.Decimal) value has less precision (fewer significant digits) when it is converted to a [Double](xref:System.Double).</span></span> <span data-ttu-id="8637c-212">No segundo caso, um valor de [Double](xref:System.Double) é arredondado de **42.72** para **43** para concluir a conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-212">In the second case, a [Double](xref:System.Double) value is rounded from **42.72** to **43** in order to complete the conversion.</span></span>

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

<span data-ttu-id="8637c-213">Para ver uma tabela que lista as conversões de ampliação e redução com suporte da classe [Convert](xref:System.Convert), consulte [Tabelas de conversão de tipos](conversion-tables.md).</span><span class="sxs-lookup"><span data-stu-id="8637c-213">For a table that lists both the widening and narrowing conversions supported by the [Convert](xref:System.Convert) class, see [Type conversion tables](conversion-tables.md).</span></span>

### <a name="custom-conversions-with-the-changetype-method"></a><span data-ttu-id="8637c-214">Conversões personalizadas com o método ChangeType</span><span class="sxs-lookup"><span data-stu-id="8637c-214">Custom conversions with the ChangeType method</span></span>

<span data-ttu-id="8637c-215">Além de oferecer suporte a conversões para cada um dos tipos base, a classe [Convert](xref:System.Convert) pode ser usada para converter um tipo personalizado em um ou mais tipos predefinidos.</span><span class="sxs-lookup"><span data-stu-id="8637c-215">In addition to supporting conversions to each of the base types, the [Convert](xref:System.Convert) class can be used to convert a custom type to one or more predefined types.</span></span> <span data-ttu-id="8637c-216">Essa conversão é executada pelo método [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) que, por sua vez, encapsula uma chamada ao método [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) do parâmetro de valor.</span><span class="sxs-lookup"><span data-stu-id="8637c-216">This conversion is performed by the [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) method, which in turn wraps a call to the [IConvertible.ToType](xref:System.IConvertible.ToType(System.Type,System.IFormatProvider)) method of the value parameter.</span></span> <span data-ttu-id="8637c-217">Isso significa que o objeto representado pelo parâmetro de valor deve fornecer uma implementação da interface [IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="8637c-217">This means that the object represented by the value parameter must provide an implementation of the [IConvertible](xref:System.IConvertible) interface.</span></span>

> [!NOTE]
> <span data-ttu-id="8637c-218">Como os métodos [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) e [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) usam um objeto de [Tipo](xref:System.Type) para especificar o tipo de destino no qual o valor será convertido, eles podem ser usados para executar uma conversão dinâmica em um objeto cujo tipo não seja conhecido no tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="8637c-218">Because the [Convert.ChangeType(Object, Type)](xref:System.Convert.ChangeType(System.Object,System.Type)) and [Convert.ChangeType(Object, Type, IFormatProvider)](xref:System.Convert.ChangeType(System.Object,System.Type,System.IFormatProvider)) methods use a [Type](xref:System.Type) object to specify the target type to which value is converted, they can be used to perform a dynamic conversion to an object whose type is not known at compile time.</span></span> <span data-ttu-id="8637c-219">No entanto, observe que a implementação de valor da [IConvertible](xref:System.IConvertible) ainda deve oferecer suporte a essa conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-219">However, note that the [IConvertible](xref:System.IConvertible) implementation of value must still support this conversion.</span></span> 

<span data-ttu-id="8637c-220">O exemplo a seguir ilustra uma possível implementação da interface [IConvertible](xref:System.IConvertible) que permite que um objeto `TemperatureCelsius` seja convertido em um objeto `TemperatureFahrenheit` e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="8637c-220">The following example illustrates a possible implementation of the [IConvertible](xref:System.IConvertible) interface that allows a `TemperatureCelsius` object to be converted to a `TemperatureFahrenheit` object and vice versa.</span></span> <span data-ttu-id="8637c-221">O exemplo define uma classe base, `Temperature`, que implementa a interface [IConvertible](xref:System.IConvertible) e substitui o método [Object.ToString](xref:System.Object.ToString).</span><span class="sxs-lookup"><span data-stu-id="8637c-221">The example defines a base class, `Temperature`, that implements the [IConvertible](xref:System.IConvertible) interface and overrides the [Object.ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="8637c-222">As classes `TemperatureCelsius` e `TemperatureFahrenheit` derivadas substituem os métodos `ToType` e `ToString` da classe base.</span><span class="sxs-lookup"><span data-stu-id="8637c-222">The derived `TemperatureCelsius` and `TemperatureFahrenheit` classes each override the `ToType` and the `ToString` methods of the base class.</span></span> 

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

<span data-ttu-id="8637c-223">O exemplo a seguir ilustra várias chamadas a essas implementações da [IConvertible](xref:System.IConvertible) para converter objetos `TemperatureCelsius` em objetos `TemperatureFahrenheit` e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="8637c-223">The following example illustrates several calls to these [IConvertible](xref:System.IConvertible) implementations to convert `TemperatureCelsius` objects to `TemperatureFahrenheit` objects and vice versa.</span></span>

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

## <a name="the-typeconverter-class"></a><span data-ttu-id="8637c-224">A classe TypeConverter</span><span class="sxs-lookup"><span data-stu-id="8637c-224">The TypeConverter class</span></span>

<span data-ttu-id="8637c-225">O .NET também permite definir um conversor de tipo para um tipo personalizado, estendendo a classe [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) e associando o conversor de tipo ao tipo por meio de um atributo [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute).</span><span class="sxs-lookup"><span data-stu-id="8637c-225">.NET also allows you to define a type converter for a custom type by extending the [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter) class and associating the type converter with the type through a [System.ComponentModel.TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> <span data-ttu-id="8637c-226">A tabela a seguir realça as diferenças entre esta abordagem e a implementação da interface [IConvertible](xref:System.IConvertible) para um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8637c-226">The following table highlights the differences between this approach and implementing the [IConvertible](xref:System.IConvertible) interface for a custom type.</span></span>

> [!NOTE]
> <span data-ttu-id="8637c-227">O suporte no tempo de design somente poderá ser fornecido para um tipo personalizado se houver um conversor de tipo definido para ele.</span><span class="sxs-lookup"><span data-stu-id="8637c-227">Design-time support can be provided for a custom type only if it has a type converter defined for it.</span></span>

<span data-ttu-id="8637c-228">Conversão usando TypeConverter</span><span class="sxs-lookup"><span data-stu-id="8637c-228">Conversion using TypeConverter</span></span> | <span data-ttu-id="8637c-229">Conversão usando IConvertible</span><span class="sxs-lookup"><span data-stu-id="8637c-229">Conversion using IConvertible</span></span>
------------------------------ | -----------------------------
<span data-ttu-id="8637c-230">É implementada para um tipo personalizado por meio da derivação de uma classe separada de [TypeConverter](xref:System.ComponentModel.TypeConverter).</span><span class="sxs-lookup"><span data-stu-id="8637c-230">Is implemented for a custom type by deriving a separate class from [TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span> <span data-ttu-id="8637c-231">Essa classe derivada é associada ao tipo personalizado aplicando um atributo [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute).</span><span class="sxs-lookup"><span data-stu-id="8637c-231">This derived class is associated with the custom type by applying a [TypeConverterAttribute](xref:System.ComponentModel.TypeConverterAttribute) attribute.</span></span> | <span data-ttu-id="8637c-232">É implementada por um tipo personalizado para executar a conversão.</span><span class="sxs-lookup"><span data-stu-id="8637c-232">Is implemented by a custom type to perform conversion.</span></span> <span data-ttu-id="8637c-233">Um usuário do tipo invoca um método de conversão de [IConvertible](xref:System.IConvertible) no tipo.</span><span class="sxs-lookup"><span data-stu-id="8637c-233">A user of the type invokes an [IConvertible](xref:System.IConvertible) conversion method on the type.</span></span>
<span data-ttu-id="8637c-234">Pode ser usada tanto no tempo de design quanto no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8637c-234">Can be used both at design time and at run time.</span></span> | <span data-ttu-id="8637c-235">Somente pode ser usada no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8637c-235">Can be used only at run time.</span></span>
<span data-ttu-id="8637c-236">Usa reflexão e, consequentemente, é mais lenta do que a conversão habilitada por [IConvertible](xref:System.IConvertible).</span><span class="sxs-lookup"><span data-stu-id="8637c-236">Uses reflection; therefore, is slower than conversion enabled by [IConvertible](xref:System.IConvertible).</span></span> | <span data-ttu-id="8637c-237">Não usa reflexão.</span><span class="sxs-lookup"><span data-stu-id="8637c-237">Does not use reflection.</span></span>
<span data-ttu-id="8637c-238">Permite conversões de tipo bidirecionais do tipo personalizado para outros tipos de dados e de outros tipos de dados para o tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8637c-238">Allows two-way type conversions from the custom type to other data types, and from other data types to the custom type.</span></span> <span data-ttu-id="8637c-239">Por exemplo, um [TypeConverter](xref:System.ComponentModel.TypeConverter) definido para `MyType` permite conversões de `MyType` em [String](xref:System.String) e de [String](xref:System.String) em `MyType`.</span><span class="sxs-lookup"><span data-stu-id="8637c-239">For example, a [TypeConverter](xref:System.ComponentModel.TypeConverter) defined for `MyType` allows conversions from `MyType` to [String](xref:System.String), and from [String](xref:System.String) to `MyType`.</span></span> | <span data-ttu-id="8637c-240">Permite a conversão de um tipo personalizado em outros tipos de dados, mas não de outros tipos de dados em um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8637c-240">Allows conversion from a custom type to other data types, but not from other data types to the custom type.</span></span>

<span data-ttu-id="8637c-241">Para obter mais informações de como usar conversores de tipo para realizar conversões, consulte [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter).</span><span class="sxs-lookup"><span data-stu-id="8637c-241">For more information about using type converters to perform conversions, see [System.ComponentModel.TypeConverter](xref:System.ComponentModel.TypeConverter).</span></span>

## <a name="see-also"></a><span data-ttu-id="8637c-242">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8637c-242">See also</span></span>

[<span data-ttu-id="8637c-243">System.Convert</span><span class="sxs-lookup"><span data-stu-id="8637c-243">System.Convert</span></span>](xref:System.Convert)

[<span data-ttu-id="8637c-244">IConvertible</span><span class="sxs-lookup"><span data-stu-id="8637c-244">IConvertible</span></span>](xref:System.IConvertible)

[<span data-ttu-id="8637c-245">Tabelas de conversão de tipos</span><span class="sxs-lookup"><span data-stu-id="8637c-245">Type conversion tables</span></span>](conversion-tables.md)
