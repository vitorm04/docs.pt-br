---
title: Formatando tipos
description: Formatando tipos
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: cf497639-9f91-45cb-836f-998d1cea2f43
ms.translationtype: Human Translation
ms.sourcegitcommit: b967d8e55347f44a012e4ad8e916440ae228c8ec
ms.openlocfilehash: e9b8ad13a48dd43236769b130d6f8a75b7b023ca
ms.contentlocale: pt-br
ms.lasthandoff: 03/10/2017

---

# <a name="formatting-types"></a><span data-ttu-id="dbe90-104">Formatando tipos</span><span class="sxs-lookup"><span data-stu-id="dbe90-104">Formatting types</span></span>

<span data-ttu-id="dbe90-105">Formatação é o processo de conversão de uma instância de classe, estrutura ou valor de enumeração em sua representação de cadeia de caracteres, de forma que a cadeia de caracteres resultante possa ser exibida aos usuários ou desserializada para restaurar o tipo de dados original.</span><span class="sxs-lookup"><span data-stu-id="dbe90-105">Formatting is the process of converting an instance of a class, structure, or enumeration value to its string representation, often so that the resulting string can be displayed to users or deserialized to restore the original data type.</span></span> <span data-ttu-id="dbe90-106">Essa conversão pode apresentar uma série de desafios:</span><span class="sxs-lookup"><span data-stu-id="dbe90-106">This conversion can pose a number of challenges:</span></span>

* <span data-ttu-id="dbe90-107">A maneira que os valores são armazenados internamente não necessariamente reflete a maneira que os usuários desejam exibi-los.</span><span class="sxs-lookup"><span data-stu-id="dbe90-107">The way that values are stored internally does not necessarily reflect the way that users want to view them.</span></span> <span data-ttu-id="dbe90-108">Por exemplo, um número de telefone pode ser armazenado no formato **8009999999**, que não é amigável.</span><span class="sxs-lookup"><span data-stu-id="dbe90-108">For example, a telephone number might be stored in the form **8009999999**, which is not user-friendly.</span></span> <span data-ttu-id="dbe90-109">Em vez disso, ele deve ser exibido como **800-999-9999**.</span><span class="sxs-lookup"><span data-stu-id="dbe90-109">It should instead be displayed as **800-999-9999**.</span></span> <span data-ttu-id="dbe90-110">Veja a seção [Cadeias de caracteres de formato personalizado](#custom-format-strings) para obter um exemplo que formata um número dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="dbe90-110">See the [Custom format strings](#custom-format-strings) section for an example that formats a number in this way.</span></span> 

* <span data-ttu-id="dbe90-111">Às vezes, a conversão de um objeto para sua representação de cadeia de caracteres não é intuitiva.</span><span class="sxs-lookup"><span data-stu-id="dbe90-111">Sometimes the conversion of an object to its string representation is not intuitive.</span></span> <span data-ttu-id="dbe90-112">Por exemplo, não é claro o modo como a representação de cadeia de caracteres de um objeto de **Temperatura** ou um objeto de **Pessoa** deve aparecer.</span><span class="sxs-lookup"><span data-stu-id="dbe90-112">For example, it is not clear how the string representation of a **Temperature** object or a **Person** object should appear.</span></span> <span data-ttu-id="dbe90-113">Para obter um exemplo que formata um objeto **Temperatura** de diversas maneiras, veja a seção [Cadeias de caracteres de formato padrão](#standard-format-strings).</span><span class="sxs-lookup"><span data-stu-id="dbe90-113">For an example that formats a **Temperature** object in a variety of ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

* <span data-ttu-id="dbe90-114">Muitas vezes, os valores exigem formatação que leva em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="dbe90-114">Values often require culture-sensitive formatting.</span></span> <span data-ttu-id="dbe90-115">Por exemplo, em um aplicativo que usa números para refletir os valores monetários, cadeias de caracteres numéricas devem incluir o símbolo da moeda da cultura atual, o separador de grupo (que, na maioria das culturas, é o separador de milhar) e o símbolo decimal.</span><span class="sxs-lookup"><span data-stu-id="dbe90-115">For example, in an application that uses numbers to reflect monetary values, numeric strings should include the current culture’s currency symbol, group separator (which, in most cultures, is the thousands separator), and decimal symbol.</span></span> <span data-ttu-id="dbe90-116">Para ver um exemplo, consulte a seção [Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface).</span><span class="sxs-lookup"><span data-stu-id="dbe90-116">For an example, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span> 

* <span data-ttu-id="dbe90-117">Um aplicativo pode ter que exibir o mesmo valor de maneiras diferentes.</span><span class="sxs-lookup"><span data-stu-id="dbe90-117">An application may have to display the same value in different ways.</span></span> <span data-ttu-id="dbe90-118">Por exemplo, um aplicativo pode representar um membro de enumeração ao exibindo uma representação de cadeia de caracteres de seu nome ou exibindo seu valor subjacente.</span><span class="sxs-lookup"><span data-stu-id="dbe90-118">For example, an application may represent an enumeration member by displaying a string representation of its name or by displaying its underlying value.</span></span> <span data-ttu-id="dbe90-119">Para obter um exemplo que formata um membro da enumeração [DayOfWeek](xref:System.DayOfWeek) de maneiras diferentes, veja a seção [Cadeias de caracteres de formato padrão](#standard-format-strings).</span><span class="sxs-lookup"><span data-stu-id="dbe90-119">For an example that formats a member of the [DayOfWeek](xref:System.DayOfWeek) enumeration in different ways, see the [Standard format strings](#standard-format-strings) section.</span></span>

<span data-ttu-id="dbe90-120">O .NET dá suporte à formatação avançada, que permite aos desenvolvedores atender a esses requisitos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-120">.NET provides rich formatting support that enables developers to address these requirements.</span></span> 

> [!NOTE]
> <span data-ttu-id="dbe90-121">A formatação converte o valor de um tipo em uma representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe90-121">Formatting converts the value of a type into a string representation.</span></span> <span data-ttu-id="dbe90-122">A análise é o inverso da formatação.</span><span class="sxs-lookup"><span data-stu-id="dbe90-122">Parsing is the inverse of formatting.</span></span> <span data-ttu-id="dbe90-123">Uma operação de análise cria uma instância de um tipo de dados com base em na representação de sua cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe90-123">A parsing operation creates an instance of a data type from its string representation.</span></span> <span data-ttu-id="dbe90-124">Para obter informações sobre como converter cadeias de caracteres em outros tipos de dados, veja [Analisando cadeias de caracteres](parsing-strings.md).</span><span class="sxs-lookup"><span data-stu-id="dbe90-124">For information about converting strings to other data types, see [Parsing strings](parsing-strings.md).</span></span>

<span data-ttu-id="dbe90-125">Esta visão geral contém as seguintes seções:</span><span class="sxs-lookup"><span data-stu-id="dbe90-125">This overview contains the following sections:</span></span>

* [<span data-ttu-id="dbe90-126">Formatação em .NET</span><span class="sxs-lookup"><span data-stu-id="dbe90-126">Formatting in .NET</span></span>](#formatting-in-net)

* [<span data-ttu-id="dbe90-127">Formatação padrão usando o método ToString</span><span class="sxs-lookup"><span data-stu-id="dbe90-127">Default formatting using the ToString method</span></span>](#default-formatting-using-the-tostring-method)

* [<span data-ttu-id="dbe90-128">Substituindo o método ToString</span><span class="sxs-lookup"><span data-stu-id="dbe90-128">Overriding the ToString method</span></span>](#overriding-the-tostring-method)

* [<span data-ttu-id="dbe90-129">As cadeias de caractere de formato e do método ToString</span><span class="sxs-lookup"><span data-stu-id="dbe90-129">The ToString method and format strings</span></span>](#the-tostring-method-and-format-strings)

    * [<span data-ttu-id="dbe90-130">Cadeias de caracteres de formato padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-130">Standard format strings</span></span>](#standard-format-strings)
    
    * [<span data-ttu-id="dbe90-131">Cadeias de caracteres de formato personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-131">Custom format strings</span></span>](#custom-format-strings)
    
    * [<span data-ttu-id="dbe90-132">Cadeias de caracteres de formato e tipos do .NET</span><span class="sxs-lookup"><span data-stu-id="dbe90-132">Format strings and .NET types</span></span>](#format-strings-and-net-types)
    
* [<span data-ttu-id="dbe90-133">Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="dbe90-133">Culture-sensitive formatting with format providers and the IFormatProvider interface</span></span>](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface)

    * [<span data-ttu-id="dbe90-134">Formatação de valores numéricos que leva em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="dbe90-134">Culture-sensitive formatting of numeric values</span></span>](#culture-sensitive-formatting-of-numeric-values)
    
    * [<span data-ttu-id="dbe90-135">Formatação de valores de data e hora que leva em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="dbe90-135">Culture-sensitive formatting of date and time values</span></span>](#culture-sensitive-formatting-of-date-and-time-values)
    
* [<span data-ttu-id="dbe90-136">A interface IFormattable</span><span class="sxs-lookup"><span data-stu-id="dbe90-136">The IFormattable interface</span></span>](#the-iformattable-interface)

* [<span data-ttu-id="dbe90-137">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="dbe90-137">Composite formatting</span></span>](#composite-formatting)

* [<span data-ttu-id="dbe90-138">Formatação personalizada com ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="dbe90-138">Custom formatting with ICustomFormatter</span></span>](#custom-formatting-with-icustomformatter)

* [<span data-ttu-id="dbe90-139">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="dbe90-139">Related topics</span></span>](#related-topics)

* [<span data-ttu-id="dbe90-140">Referência</span><span class="sxs-lookup"><span data-stu-id="dbe90-140">Reference</span></span>](#reference)

## <a name="formatting-in-net"></a><span data-ttu-id="dbe90-141">Formatação em .NET</span><span class="sxs-lookup"><span data-stu-id="dbe90-141">Formatting in .NET</span></span>

<span data-ttu-id="dbe90-142">O mecanismo básico de formatação é a implementação padrão do método [Object.ToString](xref:System.Object.ToString), que é abordado na seção [Formatação padrão usando o método ToString](#default-formatting-using-the-tostring-method), mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="dbe90-142">The basic mechanism for formatting is the default implementation of the [Object.ToString](xref:System.Object.ToString) method, which is discussed in the [Default formatting using the ToString method](#default-formatting-using-the-tostring-method) section later in this topic.</span></span> <span data-ttu-id="dbe90-143">No entanto, o .NET oferece várias maneiras de modificar e estender o suporte à formatação padrão.</span><span class="sxs-lookup"><span data-stu-id="dbe90-143">However, .NET provides several ways to modify and extend its default formatting support.</span></span> <span data-ttu-id="dbe90-144">Eles incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbe90-144">These include the following:</span></span>

* <span data-ttu-id="dbe90-145">A substituição do método [ToString](xref:System.Object.ToString) para definir uma representação de cadeia de caracteres personalizada do valor de um objeto.</span><span class="sxs-lookup"><span data-stu-id="dbe90-145">Overriding the [Object.ToString](xref:System.Object.ToString) method to define a custom string representation of an object’s value.</span></span> <span data-ttu-id="dbe90-146">Para obter mais informações, veja a seção [Substituindo o método ToString](#overriding-the-tostring-method) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="dbe90-146">For more information, see the [Overriding the ToString method](#overriding-the-tostring-method) section later in this topic.</span></span>

* <span data-ttu-id="dbe90-147">A definição dos especificadores de formato que permitem que a representação de cadeia de caracteres do valor de um objeto assuma várias formas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-147">Defining format specifiers that enable the string representation of an object’s value to take multiple forms.</span></span> <span data-ttu-id="dbe90-148">Por exemplo, o especificador de formato "X" na instrução a seguir converte um inteiro na representação de cadeia de caracteres de um valor hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="dbe90-148">For example, the "X" format specifier in the following statement converts an integer to the string representation of a hexadecimal value.</span></span>

  ```csharp
  int integerValue = 60312;
  Console.WriteLine(integerValue.ToString("X"));   // Displays EB98.
  ```

  ```vb
  Dim integerValue As Integer = 60312
  Console.WriteLine(integerValue.ToString("X"))   ' Displays EB98.
  ```
  
  <span data-ttu-id="dbe90-149">Para obter mais informações sobre especificadores de formato, veja a seção [As cadeias de caractere de formato e do método ToString](#the-tostring-method-and-format-strings).</span><span class="sxs-lookup"><span data-stu-id="dbe90-149">For more information about format specifiers, see the [The ToString method and format strings](#the-tostring-method-and-format-strings) section.</span></span>
  
* <span data-ttu-id="dbe90-150">O uso de provedores de formato para aproveitar as convenções de formatação de uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="dbe90-150">Using format providers to take advantage of the formatting conventions of a specific culture.</span></span> <span data-ttu-id="dbe90-151">Por exemplo, a instrução a seguir exibe um valor de moeda usando as convenções de formatação da cultura en-US.</span><span class="sxs-lookup"><span data-stu-id="dbe90-151">For example, the following statement displays a currency value by using the formatting conventions of the en-US culture.</span></span> 

  ```csharp
  double cost = 1632.54; 
  Console.WriteLine(cost.ToString("C", 
                  new System.Globalization.CultureInfo("en-US")));   
  // The example displays the following output:
  //       $1,632.54
  ```

  ```vb
  Dim cost As Double = 1632.54
  Console.WriteLine(cost.ToString("C", New System.Globalization.CultureInfo("en-US")))
  ' The example displays the following output:
  '       $1,632.54
  ```
  
  <span data-ttu-id="dbe90-152">Para obter mais informações sobre a formatação com provedores de formato, veja a seção [Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface).</span><span class="sxs-lookup"><span data-stu-id="dbe90-152">For more information about formatting with format providers, see the [Culture-sensitive formatting with format providers and the IFormatProvider interface](#culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface) section.</span></span>  
  
* <span data-ttu-id="dbe90-153">A implementação da interface [IFormattable](xref:System.IFormattable) para dar suporte tanto à conversão de cadeia de caracteres com a classe [Convert](xref:System.Convert) quanto à formatação de composição.</span><span class="sxs-lookup"><span data-stu-id="dbe90-153">Implementing the [IFormattable](xref:System.IFormattable) interface to support both string conversion with the [Convert](xref:System.Convert) class and composite formatting.</span></span> <span data-ttu-id="dbe90-154">Para obter mais informações, veja a seção [A interface IFormattable](#the-iformattable-interface).</span><span class="sxs-lookup"><span data-stu-id="dbe90-154">For more information, see the [The IFormattable interface](#the-iformattable-interface) section.</span></span>

* <span data-ttu-id="dbe90-155">O uso da formatação de composição para inserir a representação de cadeia de caracteres de um valor em uma cadeia de caracteres maior.</span><span class="sxs-lookup"><span data-stu-id="dbe90-155">Using composite formatting to embed the string representation of a value in a larger string.</span></span> <span data-ttu-id="dbe90-156">Para obter mais informações, veja a seção [Formatação de composição](#composite-formatting).</span><span class="sxs-lookup"><span data-stu-id="dbe90-156">For more information, see the [Composite formatting](#composite-formatting) section.</span></span>

* <span data-ttu-id="dbe90-157">A implementação de [ICustomFormatter](xref:System.ICustomFormatter) e [IFormatProvider](xref:System.IFormatProvider) para fornecer uma solução completa de formatação personalizada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-157">Implementing [ICustomFormatter](xref:System.ICustomFormatter) and [IFormatProvider](xref:System.IFormatProvider) to provide a complete custom formatting solution.</span></span> <span data-ttu-id="dbe90-158">Para obter mais informações, veja a seção [Formatação personalizada com ICustomFormatter](#custom-formatting-with-icustomformatter).</span><span class="sxs-lookup"><span data-stu-id="dbe90-158">For more information, see the [Custom formatting with ICustomFormatter](#custom-formatting-with-icustomformatter) section.</span></span>

<span data-ttu-id="dbe90-159">As seções a seguir examinam esses métodos para converter um objeto em sua representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe90-159">The following sections examine these methods for converting an object to its string representation.</span></span>

## <a name="default-formatting-using-the-tostring-method"></a><span data-ttu-id="dbe90-160">Formatação padrão usando o método ToString</span><span class="sxs-lookup"><span data-stu-id="dbe90-160">Default formatting using the ToString method</span></span>

<span data-ttu-id="dbe90-161">Cada tipo é derivado de [System.Object](xref:System.Object) herda automaticamente um método [ToString](xref:System.Object.ToString) sem parâmetros, que retorna o nome do tipo por padrão.</span><span class="sxs-lookup"><span data-stu-id="dbe90-161">Every type that is derived from [System.Object](xref:System.Object) automatically inherits a parameterless [ToString](xref:System.Object.ToString) method, which returns the name of the type by default.</span></span> <span data-ttu-id="dbe90-162">O exemplo a seguir ilustra o método [ToString](xref:System.Object.ToString) padrão.</span><span class="sxs-lookup"><span data-stu-id="dbe90-162">The following example illustrates the default [ToString](xref:System.Object.ToString) method.</span></span> <span data-ttu-id="dbe90-163">Ele define uma classe chamada `Automobile` que não tem nenhuma implementação.</span><span class="sxs-lookup"><span data-stu-id="dbe90-163">It defines a class named `Automobile` that has no implementation.</span></span> <span data-ttu-id="dbe90-164">Quando a classe é instanciada e seu método [ToString](xref:System.Object.ToString) é chamado, ele exibe seu nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-164">When the class is instantiated and its [ToString](xref:System.Object.ToString) method is called, it displays its type name.</span></span> <span data-ttu-id="dbe90-165">Observe que o método [ToString](xref:System.Object.ToString) não é chamado explicitamente no exemplo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-165">Note that the [ToString](xref:System.Object.ToString) method is not explicitly called in the example.</span></span> <span data-ttu-id="dbe90-166">O método [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) chama implicitamente o método [ToString](xref:System.Object.ToString) do objeto é passado para ele como um argumento.</span><span class="sxs-lookup"><span data-stu-id="dbe90-166">The [Console.WriteLine(Object)](xref:System.Console.WriteLine(System.Object)) method implicitly calls the [ToString](xref:System.Object.ToString) method of the object passed to it as an argument.</span></span> 

```csharp
using System;

public class Automobile
{
   // No implementation. All members are inherited from Object.
}

public class Example
{
   public static void Main()
   {
      Automobile firstAuto = new Automobile();
      Console.WriteLine(firstAuto);
   }
}
// The example displays the following output:
//       Automobile
```

```vb 
Public Class Automobile
   ' No implementation. All members are inherited from Object.
End Class

Module Example
   Public Sub Main()
      Dim firstAuto As New Automobile()
      Console.WriteLine(firstAuto)
   End Sub
End Module
' The example displays the following output:
'       Automobile
```

<span data-ttu-id="dbe90-167">Já que todos os tipos, com a exceção das interfaces, são derivados de [Object](xref:System.Object), essa funcionalidade é fornecida automaticamente para suas estruturas ou classes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-167">Because all types other than interfaces are derived from [Object](xref:System.Object), this functionality is automatically provided to your custom classes or structures.</span></span> <span data-ttu-id="dbe90-168">No entanto, a funcionalidade oferecida pelo método [ToString](xref:System.Object.ToString) padrão é limitada: embora ele identifique o tipo, não fornece nenhuma informação sobre uma instância do tipo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-168">However, the functionality offered by the default [ToString](xref:System.Object.ToString) method, is limited: Although it identifies the type, it fails to provide any information about an instance of the type.</span></span> <span data-ttu-id="dbe90-169">Para fornecer uma representação de cadeia de caracteres de um objeto que fornece informações sobre o objeto, você deve substituir o método [ToString](xref:System.Object.ToString).</span><span class="sxs-lookup"><span data-stu-id="dbe90-169">To provide a string representation of an object that provides information about that object, you must override the [ToString](xref:System.Object.ToString) method.</span></span>

> [!NOTE]
> <span data-ttu-id="dbe90-170">Estruturas herdam de [ValueType](xref:System.ValueType), que por sua vez é derivado de [Object](xref:System.Object).</span><span class="sxs-lookup"><span data-stu-id="dbe90-170">Structures inherit from [ValueType](xref:System.ValueType), which in turn is derived from [Object](xref:System.Object).</span></span> <span data-ttu-id="dbe90-171">Embora [ValueType](xref:System.ValueType) substitua [Object.ToString](xref:System.Object.ToString), sua implementação é idêntica.</span><span class="sxs-lookup"><span data-stu-id="dbe90-171">Although [ValueType](xref:System.ValueType) overrides [Object.ToString](xref:System.Object.ToString), its implementation is identical.</span></span>

## <a name="overriding-the-tostring-method"></a><span data-ttu-id="dbe90-172">Substituindo o método ToString</span><span class="sxs-lookup"><span data-stu-id="dbe90-172">Overriding the ToString method</span></span>

<span data-ttu-id="dbe90-173">A exibição do nome de um tipo é geralmente de uso limitado e não permite que os consumidores dos seus tipos diferenciem uma instância da outra.</span><span class="sxs-lookup"><span data-stu-id="dbe90-173">Displaying the name of a type is often of limited use and does not allow consumers of your types to differentiate one instance from another.</span></span> <span data-ttu-id="dbe90-174">No entanto, você pode substituir o método [ToString](xref:System.Object.ToString) para fornecer uma representação mais útil do valor de um objeto.</span><span class="sxs-lookup"><span data-stu-id="dbe90-174">However, you can override the [ToString](xref:System.Object.ToString) method to provide a more useful representation of an object’s value.</span></span> <span data-ttu-id="dbe90-175">O exemplo a seguir define um objeto `Temperature` e substitui seu método [ToString](xref:System.Object.ToString) para exibir a temperatura em graus Celsius.</span><span class="sxs-lookup"><span data-stu-id="dbe90-175">The following example defines a `Temperature` object and overrides its [ToString](xref:System.Object.ToString) method to display the temperature in degrees Celsius.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal temp;

   public Temperature(decimal temperature)
   {
      this.temp = temperature;   
   }

   public override string ToString()
   {
      return this.temp.ToString("N1") + "°C";
   }
}

public class Example
{
   public static void Main()
   {
      Temperature currentTemperature = new Temperature(23.6m);
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString());
   }
}
// The example displays the following output:
//       The current temperature is 23.6°C.
```

```vb
Public Class Temperature
   Private temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.temp = temperature
   End Sub

   Public Overrides Function ToString() As String
      Return Me.temp.ToString("N1") + "°C"   
   End Function
End Class

Module Example
   Public Sub Main()
      Dim currentTemperature As New Temperature(23.6d)
      Console.WriteLine("The current temperature is " +
                        currentTemperature.ToString())
   End Sub
End Module
' The example displays the following output:
'       The current temperature is 23.6°C.
```

<span data-ttu-id="dbe90-176">No .NET, o método [ToString](xref:System.Object.ToString) de cada tipo de valor primitivo foi substituído para exibir o valor do objeto, em vez de seu nome.</span><span class="sxs-lookup"><span data-stu-id="dbe90-176">In .NET, the [ToString](xref:System.Object.ToString) method of each primitive value type has been overridden to display the object’s value instead of its name.</span></span> <span data-ttu-id="dbe90-177">A tabela a seguir mostra a substituição de cada tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-177">The following table shows the override for each primitive type.</span></span> <span data-ttu-id="dbe90-178">Observe que a maioria dos métodos substituídos chama outra sobrecarga do método [ToString](xref:System.Object.ToString) e passa-a ao especificador de formato "G" que define o formato geral de seu tipo, além de um objeto [IFormatProvider](xref:System.IFormatProvider) que representa a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-178">Note that most of the overridden methods call another overload of the [ToString](xref:System.Object.ToString) method and pass it the "G" format specifier, which defines the general format for its type, and an [IFormatProvider](xref:System.IFormatProvider) object that represents the current culture.</span></span>

<span data-ttu-id="dbe90-179">Tipo</span><span class="sxs-lookup"><span data-stu-id="dbe90-179">Type</span></span> | <span data-ttu-id="dbe90-180">Substituição de ToString</span><span class="sxs-lookup"><span data-stu-id="dbe90-180">ToString override</span></span>
---- | -----------------
[<span data-ttu-id="dbe90-181">Booliano</span><span class="sxs-lookup"><span data-stu-id="dbe90-181">Boolean</span></span>](xref:System.Boolean) | <span data-ttu-id="dbe90-182">Retorna um [Boolean.TrueString](xref:System.Boolean.TrueString) ou [Boolean.FalseString](xref:System.Boolean.FalseString).</span><span class="sxs-lookup"><span data-stu-id="dbe90-182">Returns either [Boolean.TrueString](xref:System.Boolean.TrueString) or [Boolean.FalseString](xref:System.Boolean.FalseString).</span></span>
[<span data-ttu-id="dbe90-183">Byte</span><span class="sxs-lookup"><span data-stu-id="dbe90-183">Byte</span></span>](xref:System.Byte) | <span data-ttu-id="dbe90-184">Chama `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Byte](xref:System.Byte) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-184">Calls `Byte.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Byte](xref:System.Byte) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-185">Char</span><span class="sxs-lookup"><span data-stu-id="dbe90-185">Char</span></span>](xref:System.Char) | <span data-ttu-id="dbe90-186">Retorna o caractere como uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe90-186">Returns the character as a string.</span></span>
[<span data-ttu-id="dbe90-187">DateTime</span><span class="sxs-lookup"><span data-stu-id="dbe90-187">DateTime</span></span>](xref:System.DateTime) | <span data-ttu-id="dbe90-188">Chama `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` para formatar o valor de data e hora para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-188">Calls `DateTime.ToString("G", DatetimeFormatInfo.CurrentInfo)` to format the date and time value for the current culture.</span></span> 
[<span data-ttu-id="dbe90-189">Decimal</span><span class="sxs-lookup"><span data-stu-id="dbe90-189">Decimal</span></span>](xref:System.Decimal) | <span data-ttu-id="dbe90-190">Chama `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Decimal](xref:System.Decimal) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-190">Calls `Decimal.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Decimal](xref:System.Decimal) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-191">Duplo</span><span class="sxs-lookup"><span data-stu-id="dbe90-191">Double</span></span>](xref:System.Double) | <span data-ttu-id="dbe90-192">Chama `Double.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Double](xref:System.Double) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-192">Calls `Double.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Double](xref:System.Double) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-193">Int16</span><span class="sxs-lookup"><span data-stu-id="dbe90-193">Int16</span></span>](xref:System.Int16) | <span data-ttu-id="dbe90-194">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Int16](xref:System.Int16) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-194">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int16](xref:System.Int16) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-195">Int32</span><span class="sxs-lookup"><span data-stu-id="dbe90-195">Int32</span></span>](xref:System.Int32) | <span data-ttu-id="dbe90-196">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Int32](xref:System.Int32) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-196">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int32](xref:System.Int32) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-197">Int64</span><span class="sxs-lookup"><span data-stu-id="dbe90-197">Int64</span></span>](xref:System.Int64) | <span data-ttu-id="dbe90-198">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Int64](xref:System.Int64) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-198">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Int64](xref:System.Int64) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-199">SByte</span><span class="sxs-lookup"><span data-stu-id="dbe90-199">SByte</span></span>](xref:System.SByte) | <span data-ttu-id="dbe90-200">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [SByte](xref:System.SByte)</span><span class="sxs-lookup"><span data-stu-id="dbe90-200">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [SByte](xref:System.SByte)</span></span> | <span data-ttu-id="dbe90-201">para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-201">value for the current culture.</span></span>
[<span data-ttu-id="dbe90-202">Simples</span><span class="sxs-lookup"><span data-stu-id="dbe90-202">Single</span></span>](xref:System.Single) | <span data-ttu-id="dbe90-203">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [Single](xref:System.Single) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-203">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [Single](xref:System.Single) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-204">UInt32</span><span class="sxs-lookup"><span data-stu-id="dbe90-204">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="dbe90-205">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [UInt32](xref:System.UInt32) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-205">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32)value for the current culture.</span></span>
[<span data-ttu-id="dbe90-206">UInt32</span><span class="sxs-lookup"><span data-stu-id="dbe90-206">UInt32</span></span>](xref:System.UInt32) | <span data-ttu-id="dbe90-207">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [UInt32](xref:System.UInt32) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-207">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt32](xref:System.UInt32) value for the current culture.</span></span>
[<span data-ttu-id="dbe90-208">UInt64</span><span class="sxs-lookup"><span data-stu-id="dbe90-208">UInt64</span></span>](xref:System.UInt64) | <span data-ttu-id="dbe90-209">Chama `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` para formatar o valor [UInt64](xref:System.UInt64) para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-209">Calls `Int16.ToString("G", NumberFormatInfo.CurrentInfo)` to format the [UInt64](xref:System.UInt64)  value for the current culture.</span></span>

## <a name="the-tostring-method-and-format-strings"></a><span data-ttu-id="dbe90-210">As cadeias de caractere de formato e do método ToString</span><span class="sxs-lookup"><span data-stu-id="dbe90-210">The ToString method and format strings</span></span>

<span data-ttu-id="dbe90-211">Contar com o método padrão [ToString](xref:System.Object.ToString) ou substituir [ToString](xref:System.Object.ToString) é apropriado quando um objeto tem uma única representação de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe90-211">Relying on the default [ToString](xref:System.Object.ToString) method or overriding [ToString](xref:System.Object.ToString) is appropriate when an object has a single string representation.</span></span> <span data-ttu-id="dbe90-212">No entanto, o valor de um objeto normalmente tem várias representações.</span><span class="sxs-lookup"><span data-stu-id="dbe90-212">However, the value of an object often has multiple representations.</span></span> <span data-ttu-id="dbe90-213">Por exemplo, uma temperatura pode ser expressa em graus Fahrenheit, graus Celsius ou kelvins.</span><span class="sxs-lookup"><span data-stu-id="dbe90-213">For example, a temperature can be expressed in degrees Fahrenheit, degrees Celsius, or kelvins.</span></span> <span data-ttu-id="dbe90-214">De forma similar, o valor de inteiro 10 pode ser representado de várias maneiras, incluindo 10, 10,0, 1.0e01 ou US $10,00.</span><span class="sxs-lookup"><span data-stu-id="dbe90-214">Similarly, the integer value 10 can be represented in numerous ways, including 10, 10.0, 1.0e01, or $10.00.</span></span>

<span data-ttu-id="dbe90-215">Para permitir que um único valor tenha várias representações de cadeia de caracteres, o .NET usa cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="dbe90-215">To enable a single value to have multiple string representations, .NET uses format strings.</span></span> <span data-ttu-id="dbe90-216">Uma cadeia de caracteres de formato é uma cadeia de caracteres que contém um ou mais especificadores de formato predefinidos, que são caracteres únicos ou grupos de caracteres que definem como o método [ToString](xref:System.Object.ToString) deve formatar sua saída.</span><span class="sxs-lookup"><span data-stu-id="dbe90-216">A format string is a string that contains one or more predefined format specifiers, which are single characters or groups of characters that define how the [ToString](xref:System.Object.ToString) method should format its output.</span></span> <span data-ttu-id="dbe90-217">A cadeia de caracteres de formato é passada como um parâmetro para o método [ToString](xref:System.Object.ToString) do objeto e determina como a representação de cadeia de caracteres do valor do objeto deve ser exibida.</span><span class="sxs-lookup"><span data-stu-id="dbe90-217">The format string is then passed as a parameter to the object's [ToString](xref:System.Object.ToString) method and determines how the string representation of that object's value should appear.</span></span>

<span data-ttu-id="dbe90-218">Todos os tipos numéricos, de data e hora e tipos de enumeração no .NET dão suporte a um conjunto predefinido de especificadores de formato.</span><span class="sxs-lookup"><span data-stu-id="dbe90-218">All numeric types, date and time types, and enumeration types in .NET support a predefined set of format specifiers.</span></span> <span data-ttu-id="dbe90-219">Você também pode usar cadeias de caracteres de formato para definir várias representações de cadeia de caracteres de seus tipos de dados definidos pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-219">You can also use format strings to define multiple string representations of your application-defined data types.</span></span>

### <a name="standard-format-strings"></a><span data-ttu-id="dbe90-220">Cadeias de caracteres de formato padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-220">Standard format strings</span></span>

<span data-ttu-id="dbe90-221">Uma cadeia de caracteres de formato padrão contém um único especificador de formato, que é um caractere alfabético que define a representação de cadeia de caracteres do objeto ao qual ela é aplicada, junto com um especificador de precisão opcional que afeta a quantos dígitos serão exibidos na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-221">A standard format string contains a single format specifier, which is an alphabetic character that defines the string representation of the object to which it is applied, along with an optional precision specifier that affects how many digits are displayed in the result string.</span></span> <span data-ttu-id="dbe90-222">Se o especificador de precisão for omitido ou não houver suporte a ele, um especificador de formato padrão será equivalente a uma cadeia de caracteres de formato padrão.</span><span class="sxs-lookup"><span data-stu-id="dbe90-222">If the precision specifier is omitted or is not supported, a standard format specifier is equivalent to a standard format string.</span></span> 

<span data-ttu-id="dbe90-223">O .NET define um conjunto de especificadores de formato padrão para todos os tipos numéricos, todos os tipos de data e hora e todos os tipos de enumeração.</span><span class="sxs-lookup"><span data-stu-id="dbe90-223">.NET defines a set of standard format specifiers for all numeric types, all date and time types, and all enumeration types.</span></span> <span data-ttu-id="dbe90-224">Por exemplo, cada uma dessas categorias dá suporte a um especificador de formato padrão "G", que define uma representação de cadeia de caracteres geral de um valor desse mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-224">For example, each of these categories supports a "G" standard format specifier, which defines a general string representation of a value of that type.</span></span>

<span data-ttu-id="dbe90-225">Cadeias de caracteres de formato padrão para tipos de enumeração controlam diretamente a representação de cadeia de caracteres de um valor.</span><span class="sxs-lookup"><span data-stu-id="dbe90-225">Standard format strings for enumeration types directly control the string representation of a value.</span></span> <span data-ttu-id="dbe90-226">As cadeias de caracteres de formato passadas para o método [ToString](xref:System.Object.ToString) de um valor de enumeração determinam se o valor é exibido usando seu nome de cadeia de caracteres (especificadores de formato "G" e "F"), seu valor integral subjacente (o especificador de formato "D") ou seu valor hexadecimal (o especificador de formato "X").</span><span class="sxs-lookup"><span data-stu-id="dbe90-226">The format strings passed to an enumeration value’s [ToString](xref:System.Object.ToString) method determine whether the value is displayed using its string name (the "G" and "F" format specifiers), its underlying integral value (the "D" format specifier), or its hexadecimal value (the "X" format specifier).</span></span> <span data-ttu-id="dbe90-227">O exemplo a seguir ilustra o uso de cadeias de caracteres de formato padrão para formatar um valor de enumeração [DayOfWeek](xref:System.DayOfWeek).</span><span class="sxs-lookup"><span data-stu-id="dbe90-227">The following example illustrates the use of standard format strings to format a [DayOfWeek](xref:System.DayOfWeek) enumeration value.</span></span> 

```csharp
DayOfWeek thisDay = DayOfWeek.Monday;
string[] formatStrings = {"G", "F", "D", "X"};

foreach (string formatString in formatStrings)
   Console.WriteLine(thisDay.ToString(formatString));
// The example displays the following output:
//       Monday
//       Monday
//       1
//       00000001
```

```vb
Dim thisDay As DayOfWeek = DayOfWeek.Monday
Dim formatStrings() As String = {"G", "F", "D", "X"}

For Each formatString As String In formatStrings
   Console.WriteLine(thisDay.ToString(formatString))
Next
' The example displays the following output:
'       Monday
'       Monday
'       1
'       00000001
```

<span data-ttu-id="dbe90-228">Para obter informações sobre cadeias de caracteres de formato de enumeração, veja [Cadeias de caracteres de formato de enumeração](enumeration-format.md).</span><span class="sxs-lookup"><span data-stu-id="dbe90-228">For information about enumeration format strings, see [Enumeration format strings](enumeration-format.md).</span></span>

<span data-ttu-id="dbe90-229">Cadeias de caracteres de formato padrão para tipos numéricos geralmente definem uma cadeia de caracteres de resultado cuja aparência exata é controlada por um ou mais valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="dbe90-229">Standard format strings for numeric types usually define a result string whose precise appearance is controlled by one or more property values.</span></span> <span data-ttu-id="dbe90-230">Por exemplo, o especificador de formato "C" formata um número como um valor de moeda.</span><span class="sxs-lookup"><span data-stu-id="dbe90-230">For example, the "C" format specifier formats a number as a currency value.</span></span> <span data-ttu-id="dbe90-231">Quando você chama o método [ToString](xref:System.Object.ToString) com o especificador de formato "C" como o único parâmetro, os seguintes valores de propriedade do objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) da cultura atual são usados para definir a representação de cadeia de caracteres do valor numérico:</span><span class="sxs-lookup"><span data-stu-id="dbe90-231">When you call the [ToString](xref:System.Object.ToString) method with the "C" format specifier as the only parameter, the following property values from the current culture’s [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object are used to define the string representation of the numeric value:</span></span>

* <span data-ttu-id="dbe90-232">A propriedade [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol), que especifica o símbolo da moeda da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-232">The [CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) property, which specifies the current culture’s currency symbol.</span></span>

* <span data-ttu-id="dbe90-233">A propriedade [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) ou [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern), que retorna um inteiro que determina o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbe90-233">The [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) or [CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) property, which returns an integer that determines the following:</span></span> 

    * <span data-ttu-id="dbe90-234">O posicionamento do símbolo da moeda.</span><span class="sxs-lookup"><span data-stu-id="dbe90-234">The placement of the currency symbol.</span></span>
    
    * <span data-ttu-id="dbe90-235">Se valores negativos são indicados por um sinal de negativo à esquerda, um sinal de negativo à direita ou parênteses.</span><span class="sxs-lookup"><span data-stu-id="dbe90-235">Whether negative values are indicated by a leading negative sign, a trailing negative sign, or parentheses.</span></span>
    
    * <span data-ttu-id="dbe90-236">Se um espaço é ou não exibido entre o valor numérico e o símbolo da moeda.</span><span class="sxs-lookup"><span data-stu-id="dbe90-236">Whether a space appears between the numeric value and the currency symbol.</span></span>
    
* <span data-ttu-id="dbe90-237">A propriedade [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits), que define o número de dígitos fracionários na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-237">The [CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) property, which defines the number of fractional digits in the result string.</span></span>

* <span data-ttu-id="dbe90-238">A propriedade [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator), que define o símbolo do separador decimal na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-238">The [CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) property, which defines the decimal separator symbol in the result string.</span></span>

* <span data-ttu-id="dbe90-239">A propriedade [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator), que define o símbolo de separador de grupo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-239">The [CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) property, which defines the group separator symbol.</span></span>

* <span data-ttu-id="dbe90-240">A propriedade [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes), que define o número de dígitos em cada grupo à esquerda da vírgula decimal.</span><span class="sxs-lookup"><span data-stu-id="dbe90-240">The [CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) property, which defines the number of digits in each group to the left of the decimal.</span></span>

* <span data-ttu-id="dbe90-241">A propriedade [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign), que determinará o sinal de negativo usado na cadeia de caracteres de resultado se parênteses não forem usados para indicar valores negativos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-241">The [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) property, which determines the negative sign used in the result string if parentheses are not used to indicate negative values.</span></span>

<span data-ttu-id="dbe90-242">Além disso, cadeias de caracteres de formato numérico podem incluir um especificador de precisão.</span><span class="sxs-lookup"><span data-stu-id="dbe90-242">In addition, numeric format strings may include a precision specifier.</span></span> <span data-ttu-id="dbe90-243">O significado desse especificador depende da cadeia de caracteres de formato com o qual ele é usado, mas ele normalmente indica o número total de dígitos ou o número de dígitos fracionários que devem aparecer na cadeia de caracteres de resultado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-243">The meaning of this specifier depends on the format string with which it is used, but it typically indicates either the total number of digits or the number of fractional digits that should appear in the result string.</span></span> <span data-ttu-id="dbe90-244">Por exemplo, o exemplo a seguir usa a cadeia de caracteres numérica padrão "X4" e um especificador de precisão para criar um valor de cadeia de caracteres com quatro dígitos hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="dbe90-244">For example, the following example uses the "X4" standard numeric string and a precision specifier to create a string value that has four hexadecimal digits.</span></span>

```csharp
byte[] byteValues = { 12, 163, 255 };
foreach (byte byteValue in byteValues)
   Console.WriteLine(byteValue.ToString("X4"));
// The example displays the following output:
//       000C
//       00A3
//       00FF
```

```vb
Dim byteValues() As Byte = { 12, 163, 255 }
For Each byteValue As Byte In byteValues
   Console.WriteLine(byteValue.ToString("X4"))
Next
' The example displays the following output:
'       000C
'       00A3
'       00FF
```

<span data-ttu-id="dbe90-245">Para obter mais informações sobre cadeias de caracteres de formatação numérica padrão, veja [Cadeias de caracteres de formato numérico padrão](standard-numeric.md).</span><span class="sxs-lookup"><span data-stu-id="dbe90-245">For more information about standard numeric formatting strings, see [Standard numeric format strings](standard-numeric.md).</span></span> 

<span data-ttu-id="dbe90-246">Cadeias de caracteres de formato padrão para valores de data e hora são aliases para cadeias de caracteres de formato personalizado armazenadas por uma determinada classe [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo).</span><span class="sxs-lookup"><span data-stu-id="dbe90-246">Standard format strings for date and time values are aliases for custom format strings stored by a particular [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) class.</span></span> <span data-ttu-id="dbe90-247">Por exemplo, chamar o método [ToString](xref:System.Object.ToString) de um valor de data e hora com o especificador de formato "D" exibe a data e hora por meio do uso da cadeia de caracteres de formato personalizado armazenada na propriedade [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-247">For example, calling the [ToString](xref:System.Object.ToString) method of a date and time value with the "D" format specifier displays the date and time by using the custom format string stored in the current culture’s [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) property.</span></span> <span data-ttu-id="dbe90-248">(Para obter mais informações sobre cadeias de caracteres de formato personalizado, veja a seção [Cadeias de caracteres de formato personalizado](#custom-format-strings).) O exemplo a seguir ilustra essa relação.</span><span class="sxs-lookup"><span data-stu-id="dbe90-248">(For more information about custom format strings, see the [Custom format strings](#custom-format-strings) section.) The following example illustrates this relationship.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      DateTime date1 = new DateTime(2017, 6, 30);
      Console.WriteLine("D Format Specifier:     {0:D}", date1);
      string longPattern = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern;
      Console.WriteLine("'{0}' custom format string:     {1}", 
                        longPattern, date1.ToString(longPattern));
   }
}
// The example displays the following output when run on a system whose
// current culture is en-US:
//    D Format Specifier:     Tuesday, June 30, 2017
//    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2017
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim date1 As Date = #6/30/2009#
      Console.WriteLine("D Format Specifier:     {0:D}", date1)
      Dim longPattern As String = CultureInfo.CurrentCulture.DateTimeFormat.LongDatePattern
      Console.WriteLine("'{0}' custom format string:     {1}", _
                        longPattern, date1.ToString(longPattern))
   End Sub
End Module
' The example displays the following output when run on a system whose
' current culture is en-US:
'    D Format Specifier:     Tuesday, June 30, 2009
'    'dddd, MMMM dd, yyyy' custom format string:     Tuesday, June 30, 2009
```

<span data-ttu-id="dbe90-249">Para obter mais informações sobre o padrão de data e cadeias de caracteres de formato de hora, veja [Cadeias de caracteres de formato de data e hora padrão](standard-datetime.md).</span><span class="sxs-lookup"><span data-stu-id="dbe90-249">For more information about standard date and time format strings, see [Standard date and time format strings](standard-datetime.md).</span></span>

<span data-ttu-id="dbe90-250">Você também pode usar cadeias de caracteres de formato padrão para definir a representação de cadeia de caracteres de um objeto definido pelo aplicativo que é produzido pelo método `ToString(String)` do objeto.</span><span class="sxs-lookup"><span data-stu-id="dbe90-250">You can also use standard format strings to define the string representation of an application-defined object that is produced by the object’s `ToString(String)` method.</span></span> <span data-ttu-id="dbe90-251">Você pode definir os especificadores de formato padrão específicos que dão suporte a seu objeto e você pode determinar se eles diferenciam ou não maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-251">You can define the specific standard format specifiers that your object supports, and you can determine whether they are case-sensitive or case-insensitive.</span></span> <span data-ttu-id="dbe90-252">A implementação do `ToString(String)` método deve dar suporte ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbe90-252">Your implementation of the `ToString(String)` method should support the following:</span></span>

* <span data-ttu-id="dbe90-253">Um especificador de formato "G" que representa um formato comum ou habitual do objeto.</span><span class="sxs-lookup"><span data-stu-id="dbe90-253">A "G" format specifier that represents a customary or common format of the object.</span></span> <span data-ttu-id="dbe90-254">A sobrecarga sem parâmetros do método `ToString` de seu objeto deve chamar sua sobrecarga `ToString(String)` e passar cadeia de caracteres de formato padrão "G".</span><span class="sxs-lookup"><span data-stu-id="dbe90-254">The parameterless overload of your object's `ToString` method should call its `ToString(String)` overload and pass it the "G" standard format string.</span></span>

* <span data-ttu-id="dbe90-255">Suporte para um especificador de formato que é igual a uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="dbe90-255">Support for a format specifier that is equal to a null reference.</span></span> <span data-ttu-id="dbe90-256">Um especificador de formato igual a uma referência nula deve ser considerado equivalente ao especificador de formato "G".</span><span class="sxs-lookup"><span data-stu-id="dbe90-256">A format specifier that is equal to a null reference should be considered equivalent to the "G" format specifier.</span></span>

<span data-ttu-id="dbe90-257">Por exemplo, um `Temperature` classe interna pode armazenar a temperatura em graus Celsius e usar especificadores de formato para representar o valor do objeto `Temperature` em graus Fahrenheit, graus Celsius e kelvins.</span><span class="sxs-lookup"><span data-stu-id="dbe90-257">For example, a `Temperature` class can internally store the temperature in degrees Celsius and use format specifiers to represent the value of the `Temperature` object in degrees Celsius, degrees Fahrenheit, and kelvins.</span></span> <span data-ttu-id="dbe90-258">O exemplo a seguir fornece uma ilustração.</span><span class="sxs-lookup"><span data-stu-id="dbe90-258">The following example provides an illustration.</span></span>

```csharp
using System;

public class Temperature
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round(((decimal) (this.m_Temp * 9 / 5 + 32)), 2); }
   }

   public override string ToString()
   {
      return this.ToString("C");
   }

   public string ToString(string format)
   {  
      // Handle null or empty string.
      if (String.IsNullOrEmpty(format)) format = "C";
      // Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant();      

      // Convert temperature to Fahrenheit and return string.
      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2") + " °F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2") + " K";
         // return temperature in Celsius.
         case "G":
         case "C":
            return this.Celsius.ToString("N2") + " °C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}

public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(0m);
      Console.WriteLine(temp1.ToString());
      Console.WriteLine(temp1.ToString("G"));
      Console.WriteLine(temp1.ToString("C"));
      Console.WriteLine(temp1.ToString("F"));
      Console.WriteLine(temp1.ToString("K"));

      Temperature temp2 = new Temperature(-40m);
      Console.WriteLine(temp2.ToString());
      Console.WriteLine(temp2.ToString("G"));
      Console.WriteLine(temp2.ToString("C"));
      Console.WriteLine(temp2.ToString("F"));
      Console.WriteLine(temp2.ToString("K"));

      Temperature temp3 = new Temperature(16m);
      Console.WriteLine(temp3.ToString());
      Console.WriteLine(temp3.ToString("G"));
      Console.WriteLine(temp3.ToString("C"));
      Console.WriteLine(temp3.ToString("F"));
      Console.WriteLine(temp3.ToString("K"));

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3));
   }
}
// The example displays the following output:
//       0.00 °C
//       0.00 °C
//       0.00 °C
//       32.00 °F
//       273.15 K
//       -40.00 °C
//       -40.00 °C
//       -40.00 °C
//       -40.00 °F
//       233.15 K
//       16.00 °C
//       16.00 °C
//       16.00 °C
//       60.80 °F
//       289.15 K
//       The temperature is now 16.00 °C.
```

```vb
Public Class Temperature
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("C")
   End Function

   Public Overloads Function ToString(format As String) As String  
      ' Handle null or empty string.
      If String.IsNullOrEmpty(format) Then format = "C"
      ' Remove spaces and convert to uppercase.
      format = format.Trim().ToUpperInvariant()      

      Select Case format
         Case "F"
           ' Convert temperature to Fahrenheit and return string.
            Return Me.Fahrenheit.ToString("N2") & " °F"
         Case "K"
            ' Convert temperature to Kelvin and return string.
            Return Me.Kelvin.ToString("N2") & " K"
         Case "C", "G"
            ' Return temperature in Celsius.
            Return Me.Celsius.ToString("N2") & " °C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class

Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(0d)
      Console.WriteLine(temp1.ToString())
      Console.WriteLine(temp1.ToString("G"))
      Console.WriteLine(temp1.ToString("C"))
      Console.WriteLine(temp1.ToString("F"))
      Console.WriteLine(temp1.ToString("K"))

      Dim temp2 As New Temperature(-40d)
      Console.WriteLine(temp2.ToString())
      Console.WriteLine(temp2.ToString("G"))
      Console.WriteLine(temp2.ToString("C"))
      Console.WriteLine(temp2.ToString("F"))
      Console.WriteLine(temp2.ToString("K"))

      Dim temp3 As New Temperature(16d)
      Console.WriteLine(temp3.ToString())
      Console.WriteLine(temp3.ToString("G"))
      Console.WriteLine(temp3.ToString("C"))
      Console.WriteLine(temp3.ToString("F"))
      Console.WriteLine(temp3.ToString("K"))

      Console.WriteLine(String.Format("The temperature is now {0:F}.", temp3))
   End Sub
End Module
' The example displays the following output:
'       0.00 °C
'       0.00 °C
'       0.00 °C
'       32.00 °F
'       273.15 K
'       -40.00 °C
'       -40.00 °C
'       -40.00 °C
'       -40.00 °F
'       233.15 K
'       16.00 °C
'       16.00 °C
'       16.00 °C
'       60.80 °F
'       289.15 K
'       The temperature is now 16.00 °C.
```

### <a name="custom-format-strings"></a><span data-ttu-id="dbe90-259">Cadeias de caracteres de formato personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-259">Custom format strings</span></span>

<span data-ttu-id="dbe90-260">Além de cadeias de caracteres de formato padrão, o .NET define cadeias de caracteres de formato personalizado para valores numéricos e valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="dbe90-260">In addition to the standard format strings, .NET defines custom format strings for both numeric values and date and time values.</span></span> <span data-ttu-id="dbe90-261">Uma cadeia de caracteres de formato personalizado consiste em um ou mais especificadores de formato personalizado que definem a representação de cadeia de caracteres de um valor.</span><span class="sxs-lookup"><span data-stu-id="dbe90-261">A custom format string consists of one or more custom format specifiers that define the string representation of a value.</span></span> <span data-ttu-id="dbe90-262">Por exemplo, a cadeia de caracteres de formato de data e hora personalizada "aaaa/mm/dd hh:mm:ss.ffff t zzz" converte uma data em sua representação de cadeia de caracteres no formato "2008/11/15 07:45:00.0000 P -08:00" para a cultura en-US.</span><span class="sxs-lookup"><span data-stu-id="dbe90-262">For example, the custom date and time format string "yyyy/mm/dd hh:mm:ss.ffff t zzz" converts a date to its string representation in the form "2008/11/15 07:45:00.0000 P -08:00" for the en-US culture.</span></span> <span data-ttu-id="dbe90-263">Da mesma forma, a cadeia de caracteres de formato personalizado "0000" converte o valor inteiro 12 em "0012".</span><span class="sxs-lookup"><span data-stu-id="dbe90-263">Similarly, the custom format string "0000" converts the integer value 12 to "0012".</span></span> <span data-ttu-id="dbe90-264">Para obter uma lista completa de cadeias de caracteres de formato personalizado, veja [Cadeias de caracteres de formato de data e hora personalizado](custom-datetime.md) e [Cadeias de caracteres de formato numérico personalizado](custom-numeric.md).</span><span class="sxs-lookup"><span data-stu-id="dbe90-264">For a complete list of custom format strings, see [Custom date and time format strings](custom-datetime.md) and [Custom numeric format strings](custom-numeric.md).</span></span>

<span data-ttu-id="dbe90-265">Se uma cadeia de caracteres de formato consiste em um único especificador de formato personalizado, o especificador de formato deve ser precedido pelo símbolo de porcentagem (%) para evitar confusão com um especificador de formato padrão.</span><span class="sxs-lookup"><span data-stu-id="dbe90-265">If a format string consists of a single custom format specifier, the format specifier should be preceded by the percent (%) symbol to avoid confusion with a standard format specifier.</span></span> <span data-ttu-id="dbe90-266">O exemplo a seguir usa o especificador de formato personalizado "M" para exibir um número de um ou dois dígitos do mês de uma data específica.</span><span class="sxs-lookup"><span data-stu-id="dbe90-266">The following example uses the "M" custom format specifier to display a one-digit or two-digit number of the month of a particular date.</span></span>

```csharp
DateTime date1 = new DateTime(2009, 9, 8);
Console.WriteLine(date1.ToString("%M"));       
// Displays 9
```

```vb
Dim date1 As Date = #09/08/2009#
Console.WriteLine(date1.ToString("%M"))      ' Displays 9
```

<span data-ttu-id="dbe90-267">Muitas cadeias de caracteres de formato padrão para valores de data e hora são aliases para cadeias de caracteres de formato personalizado que são definidas pelas propriedades do objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo).</span><span class="sxs-lookup"><span data-stu-id="dbe90-267">Many standard format strings for date and time values are aliases for custom format strings that are defined by properties of the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object.</span></span> <span data-ttu-id="dbe90-268">Cadeias de caracteres de formato personalizado também oferecem flexibilidade considerável no fornecimento de formação definida pelo aplicativo para valores numéricos ou valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="dbe90-268">Custom format strings also offer considerable flexibility in providing application-defined formatting for numeric values or date and time values.</span></span> <span data-ttu-id="dbe90-269">Você pode definir suas próprias cadeias de caracteres de resultado personalizadas para valores numéricos e valores de data e hora combinando vários especificadores de formato personalizado em uma única cadeia de caracteres de formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-269">You can define your own custom result strings for both numeric values and date and time values by combining multiple custom format specifiers into a single custom format string.</span></span> <span data-ttu-id="dbe90-270">O exemplo a seguir define uma cadeia de caracteres de formato personalizado que exibe o dia da semana entre parênteses após o nome do mês, o dia e o ano.</span><span class="sxs-lookup"><span data-stu-id="dbe90-270">The following example defines a custom format string that displays the day of the week in parentheses after the month name, day, and year.</span></span>

```csharp
string customFormat = "MMMM dd, yyyy (dddd)";
DateTime date1 = new DateTime(2009, 8, 28);
Console.WriteLine(date1.ToString(customFormat));   
// The example displays the following output if run on a system
// whose language is English:
//       August 28, 2009 (Friday) 
```

```vb
Dim customFormat As String = "MMMM dd, yyyy (dddd)"
Dim date1 As Date = #8/28/2009#
Console.WriteLine(date1.ToString(customFormat))   
' The example displays the following output if run on a system
' whose language is English:
'       August 28, 2009 (Friday) 
```

<span data-ttu-id="dbe90-271">O exemplo a seguir define uma cadeia de caracteres de formato personalizado que exibe um valor [Int64](xref:System.Int64) como um número de telefone de sete dígitos padrão dos EUA, junto com seu código de área.</span><span class="sxs-lookup"><span data-stu-id="dbe90-271">The following example defines a custom format string that displays an [Int64](xref:System.Int64) value as a standard, seven-digit U.S. telephone number along with its area code.</span></span> 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      long number = 8009999999;
      string fmt = "000-000-0000";
      Console.WriteLine(number.ToString(fmt));
   }
}
// The example displays the following output:
//        800-999-9999
```

```vb
Module Example
   Public Sub Main()
      Dim number As Long = 8009999999
      Dim fmt As String = "000-000-0000"
      Console.WriteLine(number.ToString(fmt))
   End Sub
End Module
' The example displays the following output:

' The example displays the following output:
'       800-999-9999
```

<span data-ttu-id="dbe90-272">Embora as cadeias de caracteres de formato padrão geralmente tratem da maioria das necessidades de formatação para os tipos definidos pelo aplicativo, você também pode definir especificadores de formato personalizado para formatar seus tipos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-272">Although standard format strings can generally handle most of the formatting needs for your application-defined types, you may also define custom format specifiers to format your types.</span></span> 

### <a name="format-strings-and-net-types"></a><span data-ttu-id="dbe90-273">Cadeias de caracteres de formato e tipos do .NET</span><span class="sxs-lookup"><span data-stu-id="dbe90-273">Format strings and .NET types</span></span>

<span data-ttu-id="dbe90-274">Todos os tipos numéricos (ou seja, os tipos [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64) e [BigInteger](xref:System.Numerics.BigInteger)), bem como [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid) e todos os tipos de enumeração, dão suporte à formatação com cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="dbe90-274">All numeric types (that is, the [Byte](xref:System.Byte), [Decimal](xref:System.Decimal), [Double](xref:System.Double), [Int16](xref:System.Int16), [Int32](xref:System.Int32), [Int64](xref:System.Int64), [SByte](xref:System.SByte), [Single](xref:System.Single), [UInt16](xref:System.UInt16), [UInt32](xref:System.UInt32), [UInt64](xref:System.UInt64), and [BigInteger](xref:System.Numerics.BigInteger) types), as well as the [DateTime](xref:System.DateTime), [DateTimeOffset](xref:System.DateTimeOffset), [TimeSpan](xref:System.TimeSpan), [Guid](xref:System.Guid), and all enumeration types, support formatting with format strings.</span></span> <span data-ttu-id="dbe90-275">Para obter informações sobre as cadeias de caracteres de formato específicas às quais cada tipo dá suporte, veja os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="dbe90-275">For information on the specific format strings supported by each type, see the following topics:</span></span> 

<span data-ttu-id="dbe90-276">Título</span><span class="sxs-lookup"><span data-stu-id="dbe90-276">Title</span></span> | <span data-ttu-id="dbe90-277">Definição</span><span class="sxs-lookup"><span data-stu-id="dbe90-277">Definition</span></span>
----- | ----------
[<span data-ttu-id="dbe90-278">Cadeias de caracteres de formato numérico padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-278">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="dbe90-279">Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores numéricos frequentemente usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-279">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="dbe90-280">Cadeias de caracteres de formato numérico personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-280">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="dbe90-281">Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-281">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="dbe90-282">Cadeias de caracteres de formato de data e hora padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-282">Standard date and time format strings</span></span>](standard-datetime.md) | <span data-ttu-id="dbe90-283">Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores [DateTime](xref:System.DateTime) frequentemente usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-283">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="dbe90-284">Cadeias de caracteres de formato de data e hora personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-284">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="dbe90-285">Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="dbe90-285">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="dbe90-286">Cadeias de caracteres de formato TimeSpan padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-286">Standard TimeSpan format Strings</span></span>](standard-timespan.md) | <span data-ttu-id="dbe90-287">Descreve cadeias de caracteres de formato padrão que criam representações de intervalos de tempo frequentemente usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-287">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="dbe90-288">Cadeias de caracteres de formato TimeSpan personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-288">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="dbe90-289">Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para intervalos de tempo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-289">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="dbe90-290">Cadeias de caracteres de formato de enumeração</span><span class="sxs-lookup"><span data-stu-id="dbe90-290">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="dbe90-291">Descreve cadeias de caracteres de formato padrão que são usadas para criar representações de cadeia de caracteres de valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="dbe90-291">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
<span data-ttu-id="dbe90-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span><span class="sxs-lookup"><span data-stu-id="dbe90-292">[Guid.ToString(String)](xref:System.Guid.ToString(System.String))</span></span> | <span data-ttu-id="dbe90-293">Descreve cadeias de caracteres de formato padrão para valores [Guid](xref:System.Guid).</span><span class="sxs-lookup"><span data-stu-id="dbe90-293">Describes standard format strings for [Guid](xref:System.Guid) values.</span></span>

## <a name="culture-sensitive-formatting-with-format-providers-and-the-iformatprovider-interface"></a><span data-ttu-id="dbe90-294">Formatação que leva em conta a cultura com provedores de formato e a interface IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="dbe90-294">Culture-Sensitive Formatting with Format Providers and the IFormatProvider Interface</span></span>

<span data-ttu-id="dbe90-295">Embora os especificadores de formato permitam personalizar a formatação de objetos, a produção de uma representação de cadeia de caracteres de objetos significativa geralmente requer informações de formatação adicionais.</span><span class="sxs-lookup"><span data-stu-id="dbe90-295">Although format specifiers let you customize the formatting of objects, producing a meaningful string representation of objects often requires additional formatting information.</span></span> <span data-ttu-id="dbe90-296">Por exemplo, formatar um número como um valor de moeda usando a cadeia de caracteres de formato padrão "C" ou então uma cadeia de caracteres de formato personalizado como "$ #,#.00" requer que, no mínimo, informações sobre o símbolo correto da moeda, o separador de grupo e o separador decimal estejam disponíveis para inclusão na cadeia de caracteres formatada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-296">For example, formatting a number as a currency value by using either the "C" standard format string or a custom format string such as "$ #,#.00" requires, at a minimum, information about the correct currency symbol, group separator, and decimal separator to be available to include in the formatted string.</span></span> <span data-ttu-id="dbe90-297">No .NET, essas informações de formatação adicionais são disponibilizadas por meio da interface [IFormatProvider](xref:System.IFormatProvider), que é fornecida como um parâmetro para um ou mais sobrecargas do método `ToString` de tipos numéricos e tipos de data e hora.</span><span class="sxs-lookup"><span data-stu-id="dbe90-297">In .NET, this additional formatting information is made available through the [IFormatProvider](xref:System.IFormatProvider) interface, which is provided as a parameter to one or more overloads of the `ToString` method of numeric types and date and time types.</span></span> <span data-ttu-id="dbe90-298">Implementações [IFormatProvider](xref:System.IFormatProvider) são usadas em .NET para dar suporte à formatação de cultura específica.</span><span class="sxs-lookup"><span data-stu-id="dbe90-298">[IFormatProvider](xref:System.IFormatProvider) implementations are used in .NET to support culture-specific formatting.</span></span> <span data-ttu-id="dbe90-299">O exemplo a seguir ilustra como a representação de cadeia de caracteres de um objeto é alterado quando ele é formatado com três objetos [IFormatProvider](xref:System.IFormatProvider) que representam diferentes culturas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-299">The following example illustrates how the string representation of an object changes when it is formatted with three [IFormatProvider](xref:System.IFormatProvider) objects that represent different cultures.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      decimal value = 1603.42m;
      Console.WriteLine(value.ToString("C3", new CultureInfo("en-US")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("fr-FR")));
      Console.WriteLine(value.ToString("C3", new CultureInfo("de-DE")));
   }
}
// The example displays the following output:
//       $1,603.420
//       1 603,420 €
//       1.603,420 €
```

```vb
Imports System.Globalization

Public Module Example
   Public Sub Main()
      Dim value As Decimal = 1603.42d
      Console.WriteLine(value.ToString("C3", New CultureInfo("en-US")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("fr-FR")))
      Console.WriteLine(value.ToString("C3", New CultureInfo("de-DE")))
   End Sub
End Module
' The example displays the following output:
'       $1,603.420
'       1 603,420 €
'       1.603,420 €
```

<span data-ttu-id="dbe90-300">A interface [IFormatProvider](xref:System.IFormatProvider) inclui um método, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), que tem um único parâmetro que especifica o tipo de objeto que fornece informações de formatação.</span><span class="sxs-lookup"><span data-stu-id="dbe90-300">The [IFormatProvider](xref:System.IFormatProvider) interface includes one method, [GetFormat(Type)](xref:System.IFormatProvider.GetFormat(System.Type)), which has a single parameter that specifies the type of object that provides formatting information.</span></span> <span data-ttu-id="dbe90-301">Se o método puder fornecer um objeto desse tipo, ele retornará esse objeto.</span><span class="sxs-lookup"><span data-stu-id="dbe90-301">If the method can provide an object of that type, it returns it.</span></span> <span data-ttu-id="dbe90-302">Caso contrário, ele retornará uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="dbe90-302">Otherwise, it returns a null reference.</span></span>

<span data-ttu-id="dbe90-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) é um método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-303">[IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) is a callback method.</span></span> <span data-ttu-id="dbe90-304">Quando você chama uma sobrecarga de método `ToString` que inclui um parâmetro [IFormatProvider](xref:System.IFormatProvider), ele chama o método [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) desse objeto [IFormatProvider](xref:System.IFormatProvider).</span><span class="sxs-lookup"><span data-stu-id="dbe90-304">When you call a `ToString` method overload that includes an [IFormatProvider](xref:System.IFormatProvider) parameter, it calls the [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method of that [IFormatProvider](xref:System.IFormatProvider) object.</span></span> <span data-ttu-id="dbe90-305">O método [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) é responsável por retornar um objeto que fornece as informações de formatação necessárias (conforme especificadas pelo seu parâmetro *formatType*) para o método `ToString`.</span><span class="sxs-lookup"><span data-stu-id="dbe90-305">The [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method is responsible for returning an object that provides the necessary formatting information, as specified by its *formatType* parameter, to the `ToString` method.</span></span> 

<span data-ttu-id="dbe90-306">Um número de métodos de conversão de cadeia de caracteres ou formatação inclui um parâmetro de tipo [IFormatProvider](xref:System.IFormatProvider), mas em muitos casos o valor do parâmetro é ignorado quando o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-306">A number of formatting or string conversion methods include a parameter of type [IFormatProvider](xref:System.IFormatProvider), but in many cases the value of the parameter is ignored when the method is called.</span></span> <span data-ttu-id="dbe90-307">A tabela a seguir lista alguns dos métodos de formatação que usam o parâmetro e o tipo do objeto [Type](xref:System.Type) que passam para o método [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)).</span><span class="sxs-lookup"><span data-stu-id="dbe90-307">The following table lists some of the formatting methods that use the parameter and the type of the [Type](xref:System.Type) object that they pass to the [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) method.</span></span> 

<span data-ttu-id="dbe90-308">Método</span><span class="sxs-lookup"><span data-stu-id="dbe90-308">Method</span></span> | <span data-ttu-id="dbe90-309">Tipo de parâmetro *formatType*</span><span class="sxs-lookup"><span data-stu-id="dbe90-309">Type of *formatType* parameter</span></span>
------ | ------------------------------
<span data-ttu-id="dbe90-310">`ToString` método de tipos numéricos</span><span class="sxs-lookup"><span data-stu-id="dbe90-310">`ToString` method of numeric types</span></span> | [<span data-ttu-id="dbe90-311">System.Globalization.NumberFormatInfo</span><span class="sxs-lookup"><span data-stu-id="dbe90-311">System.Globalization.NumberFormatInfo</span></span>](xref:System.Globalization.NumberFormatInfo)
<span data-ttu-id="dbe90-312">`ToString` método de tipos de data e hora</span><span class="sxs-lookup"><span data-stu-id="dbe90-312">`ToString` method of date and time types</span></span> | [<span data-ttu-id="dbe90-313">System.Globalization.DateTimeFormatInfo</span><span class="sxs-lookup"><span data-stu-id="dbe90-313">System.Globalization.DateTimeFormatInfo</span></span>](xref:System.Globalization.DateTimeFormatInfo)
<span data-ttu-id="dbe90-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="dbe90-314">[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="dbe90-315">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="dbe90-315">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)
<span data-ttu-id="dbe90-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="dbe90-316">[StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object))</span></span> | [<span data-ttu-id="dbe90-317">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="dbe90-317">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

<span data-ttu-id="dbe90-318">O .NET fornece três classes que implementam [IFormatProvider](xref:System.IFormatProvider):</span><span class="sxs-lookup"><span data-stu-id="dbe90-318">.NET provides three classes that implement [IFormatProvider](xref:System.IFormatProvider):</span></span> 

* <span data-ttu-id="dbe90-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), uma classe que fornece informações de formatação para valores de data e hora para uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="dbe90-319">[DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo), a class that provides formatting information for date and time values for a specific culture.</span></span> <span data-ttu-id="dbe90-320">Sua implementação [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retorna uma instância de si mesma.</span><span class="sxs-lookup"><span data-stu-id="dbe90-320">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="dbe90-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), uma classe que fornece informações de formatação numérica para uma cultura específica.</span><span class="sxs-lookup"><span data-stu-id="dbe90-321">[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo), a class that provides numeric formatting information for a specific culture.</span></span> <span data-ttu-id="dbe90-322">Sua implementação [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retorna uma instância de si mesma.</span><span class="sxs-lookup"><span data-stu-id="dbe90-322">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation returns an instance of itself.</span></span>

* <span data-ttu-id="dbe90-323">[CultureInfo](xref:System.Globalization.CultureInfo).</span><span class="sxs-lookup"><span data-stu-id="dbe90-323">[CultureInfo](xref:System.Globalization.CultureInfo).</span></span> <span data-ttu-id="dbe90-324">Sua implementação [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) pode retornar um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) para fornecer informações de formatação numérica ou um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) para fornecer informações de formatação para valores de data e hora.</span><span class="sxs-lookup"><span data-stu-id="dbe90-324">Its [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) implementation can return either a [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object to provide numeric formatting information or a [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object to provide formatting information for date and time values.</span></span> 

<span data-ttu-id="dbe90-325">Você também pode implementar seu próprio provedor de formato para substituir qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="dbe90-325">You can also implement your own format provider to replace any one of these classes.</span></span> <span data-ttu-id="dbe90-326">No entanto, se o seu método `GetFormat` de sua implementação precisar fornecer informações de formatação ao método `ToString`, ele deverá retornar um objeto do tipo listado na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="dbe90-326">However, your implementation’s `GetFormat` method must return an object of the type listed in the previous table if it has to provide formatting information to the `ToString` method.</span></span>

### <a name="culture-sensitive-formatting-of-numeric-values"></a><span data-ttu-id="dbe90-327">Formatação de valores numéricos que leva em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="dbe90-327">Culture-sensitive formatting of numeric values</span></span>

<span data-ttu-id="dbe90-328">Por padrão, a formatação de valores numéricos leva em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="dbe90-328">By default, the formatting of numeric values is culture-sensitive.</span></span> <span data-ttu-id="dbe90-329">Se você não especificar uma cultura quando chamar um método de formatação, as convenções de formatação da cultura do thread atual serão usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-329">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="dbe90-330">Isso é ilustrado no exemplo a seguir, que altera a cultura do thread atual quatro vezes e, em seguida, chama o método [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)).</span><span class="sxs-lookup"><span data-stu-id="dbe90-330">This is illustrated in the following example, which changes the current thread culture four times and then calls the [Decimal.ToString(String)](xref:System.Decimal.ToString(System.String)) method.</span></span> <span data-ttu-id="dbe90-331">Em cada caso, a cadeia de caracteres de resultado reflete as convenções de formatação da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-331">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="dbe90-332">Isso ocorre porque os métodos `ToString` e `ToString(String)` encapsulam chamadas para o método `ToString(String, IFormatProvider)` de cada tipo numérico.</span><span class="sxs-lookup"><span data-stu-id="dbe90-332">This is because the `ToString` and `ToString(String)` methods wrap calls to each numeric type's `ToString(String, IFormatProvider)` method.</span></span> 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      Decimal value = 1043.17m;

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(value.ToString("C2"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       $1,043.17
//       
//       The current culture is fr-FR
//       1 043,17 €
//       
//       The current culture is es-MX
//       $1,043.17
//       
//       The current culture is de-DE
//       1.043,17 €
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim value As Decimal = 1043.17d 

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(value.ToString("C2"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       $1,043.17
'       
'       The current culture is fr-FR
'       1 043,17 €
'       
'       The current culture is es-MX
'       $1,043.17
'       
'       The current culture is de-DE
'       1.043,17 €
```

<span data-ttu-id="dbe90-333">Você também pode formatar um valor numérico para uma cultura específica chamando uma sobrecarga `ToString` que tenha um parâmetro de *provedor* e passando-o a um dos dois elementos a seguir:</span><span class="sxs-lookup"><span data-stu-id="dbe90-333">You can also format a numeric value for a specific culture by calling a `ToString` overload that has a *provider* parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="dbe90-334">Um [CultureInfo](xref:System.Globalization.CultureInfo) objeto que representa a cultura cujas convenções de formatação devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-334">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="dbe90-335">Seu método [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retorna o valor da propriedade [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), que é o objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que fornece informações de formatação específicas da cultura para valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-335">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="dbe90-336">Um objeto [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que define as convenções de formatação específicas da cultura a ser usada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-336">A [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="dbe90-337">Seu método [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) retorna uma instância de si mesmo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-337">Its [GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="dbe90-338">O exemplo a seguir usa objetos [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) que representam as culturas inglês (Estados Unidos) e inglês (Grã-Bretanha), além das culturas neutras francês e russo, para formatar um número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="dbe90-338">The following example uses [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a floating-point number.</span></span>

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      Double value = 1043.62957;
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         NumberFormatInfo nfi = CultureInfo.CreateSpecificCulture(name).NumberFormat;
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 1,043.630
//       en-GB: 1,043.630
//       ru:    1 043,630
//       fr:    1 043,630
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As Double = 1043.62957
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim nfi As NumberFormatInfo = CultureInfo.CreateSpecificCulture(name).NumberFormat
         Console.WriteLine("{0,-6} {1}", name + ":", value.ToString("N3", nfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 1,043.630
'       en-GB: 1,043.630
'       ru:    1 043,630
'       fr:    1 043,630
```

### <a name="culture-sensitive-formatting-of-date-and-time-values"></a><span data-ttu-id="dbe90-339">Formatação de valores de data e hora que leva em conta a cultura</span><span class="sxs-lookup"><span data-stu-id="dbe90-339">Culture-sensitive formatting of date and time values</span></span>

<span data-ttu-id="dbe90-340">Por padrão, a formatação de valores de data e hora leva em conta a cultura.</span><span class="sxs-lookup"><span data-stu-id="dbe90-340">By default, the formatting of date and time values is culture-sensitive.</span></span> <span data-ttu-id="dbe90-341">Se você não especificar uma cultura quando chamar um método de formatação, as convenções de formatação da cultura do thread atual serão usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-341">If you do not specify a culture when you call a formatting method, the formatting conventions of the current thread culture are used.</span></span> <span data-ttu-id="dbe90-342">Isso é ilustrado no exemplo a seguir, que altera a cultura do thread atual quatro vezes e, em seguida, chama o método [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)).</span><span class="sxs-lookup"><span data-stu-id="dbe90-342">This is illustrated in the following example, which changes the current thread culture four times and then calls the [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)) method.</span></span> <span data-ttu-id="dbe90-343">Em cada caso, a cadeia de caracteres de resultado reflete as convenções de formatação da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="dbe90-343">In each case, the result string reflects the formatting conventions of the current culture.</span></span> <span data-ttu-id="dbe90-344">Isso ocorre porque os métodos [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)) e [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) encapsulam chamadas para os métodos [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) e [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)).</span><span class="sxs-lookup"><span data-stu-id="dbe90-344">This is because the [DateTime.ToString()](xref:System.DateTime.ToString), [DateTime.ToString(String)](xref:System.DateTime.ToString(System.String)), [DateTimeOffset.ToString()](xref:System.DateTimeOffset.ToString(System.String)), and [DateTimeOffset.ToString(String)](xref:System.DateTimeOffset.ToString(System.String)) methods wrap calls to the [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) and [DateTimeOffset.ToString(String, IFormatProvider)](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) methods.</span></span>

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] cultureNames = { "en-US", "fr-FR", "es-MX", "de-DE" };
      DateTime dateToFormat = new DateTime(2012, 5, 28, 11, 30, 0);

      foreach (var cultureName in cultureNames) {
         // Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName);
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name);
         Console.WriteLine(dateToFormat.ToString("F"));
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//       The current culture is en-US
//       Monday, May 28, 2012 11:30:00 AM
//       
//       The current culture is fr-FR
//       lundi 28 mai 2012 11:30:00
//       
//       The current culture is es-MX
//       lunes, 28 de mayo de 2012 11:30:00 a.m.
//       
//       The current culture is de-DE
//       Montag, 28. Mai 2012 11:30:00
```

```vb
Imports System.Globalization
Imports System.Threading 

Module Example
   Public Sub Main()
      Dim cultureNames() As String = { "en-US", "fr-FR", "es-MX", "de-DE" }
      Dim dateToFormat As Date = #5/28/2012 11:30AM#

      For Each cultureName In cultureNames
         ' Change the current thread culture.
         Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture(cultureName)
         Console.WriteLine("The current culture is {0}", 
                           Thread.CurrentThread.CurrentCulture.Name)
         Console.WriteLine(dateToFormat.ToString("F"))
         Console.WriteLine()
      Next                  
   End Sub
End Module
' The example displays the following output:
'       The current culture is en-US
'       Monday, May 28, 2012 11:30:00 AM
'       
'       The current culture is fr-FR
'       lundi 28 mai 2012 11:30:00
'       
'       The current culture is es-MX
'       lunes, 28 de mayo de 2012 11:30:00 a.m.
'       
'       The current culture is de-DE
'       Montag, 28. Mai 2012 11:30:00
```

<span data-ttu-id="dbe90-345">Você também pode formatar um valor de data e hora para uma cultura específica chamando uma sobrecarga [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) ou [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) que tenha um parâmetro de provedor e passando-o a um dos dois elementos a seguir:</span><span class="sxs-lookup"><span data-stu-id="dbe90-345">You can also format a date and time value for a specific culture by calling a [DateTime.ToString](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) or [DateTimeOffset.ToString](xref:System.DateTimeOffset.ToString(System.String,System.IFormatProvider)) overload that has a provider parameter and passing it either of the following:</span></span> 

* <span data-ttu-id="dbe90-346">Um [CultureInfo](xref:System.Globalization.CultureInfo) objeto que representa a cultura cujas convenções de formatação devem ser usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-346">A [CultureInfo](xref:System.Globalization.CultureInfo) object that represents the culture whose formatting conventions are to be used.</span></span> <span data-ttu-id="dbe90-347">Seu método [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) retorna o valor da propriedade [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat), que é o objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que fornece informações de formatação específicas da cultura para valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-347">Its [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) method returns the value of the [CultureInfo.NumberFormat](xref:System.Globalization.CultureInfo.NumberFormat) property, which is the [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that provides culture-specific formatting information for numeric values.</span></span>

* <span data-ttu-id="dbe90-348">Um objeto [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que define as convenções de formatação específicas da cultura a ser usada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-348">A [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) object that defines the culture-specific formatting conventions to be used.</span></span> <span data-ttu-id="dbe90-349">Seu método [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) retorna uma instância de si mesmo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-349">Its [GetFormat](xref:System.Globalization.DateTimeFormatInfo.GetFormat(System.Type)) method returns an instance of itself.</span></span>

<span data-ttu-id="dbe90-350">O exemplo a seguir usa objetos [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) que representam as culturas inglês (Estados Unidos) e inglês (Grã-Bretanha), além das culturas neutras francês e russo, para formatar uma data.</span><span class="sxs-lookup"><span data-stu-id="dbe90-350">The following example uses [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) objects that represent the English (United States) and English (Great Britain) cultures and the French and Russian neutral cultures to format a date.</span></span> 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {                                                                                                    
      DateTime dat1 = new DateTime(2012, 5, 28, 11, 30, 0);
      string[] cultureNames = { "en-US", "en-GB", "ru", "fr" };

      foreach (var name in cultureNames) {
         DateTimeFormatInfo dtfi = CultureInfo.CreateSpecificCulture(name).DateTimeFormat;
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi));
      }   
   }
}
// The example displays the following output:
//       en-US: 5/28/2012 11:30:00 AM
//       en-GB: 28/05/2012 11:30:00
//       ru: 28.05.2012 11:30:00
//       fr: 28/05/2012 11:30:00
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dat1 As Date = #5/28/2012 11:30AM#
      Dim cultureNames() As String = { "en-US", "en-GB", "ru", "fr" }

      For Each name In cultureNames
         Dim dtfi As DateTimeFormatInfo = CultureInfo.CreateSpecificCulture(name).DateTimeFormat
         Console.WriteLine("{0}: {1}", name, dat1.ToString(dtfi))
      Next   
   End Sub
End Module
' The example displays the following output:
'       en-US: 5/28/2012 11:30:00 AM
'       en-GB: 28/05/2012 11:30:00
'       ru: 28.05.2012 11:30:00
'       fr: 28/05/2012 11:30:00
```

## <a name="the-iformattable-interface"></a><span data-ttu-id="dbe90-351">A interface IFormattable</span><span class="sxs-lookup"><span data-stu-id="dbe90-351">The IFormattable interface</span></span>

<span data-ttu-id="dbe90-352">Normalmente, os tipos que sobrecarregam o método `ToString` com uma cadeia de caracteres de formato e um parâmetro [IFormatProvider](xref:System.IFormatProvider) também implementam a interface [IFormattable](xref:System.IFormattable).</span><span class="sxs-lookup"><span data-stu-id="dbe90-352">Typically, types that overload the `ToString` method with a format string and an [IFormatProvider](xref:System.IFormatProvider) parameter also implement the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="dbe90-353">Essa interface tem um único membro, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), que inclui como parâmetros uma cadeia de caracteres de formato e um provedor de formato.</span><span class="sxs-lookup"><span data-stu-id="dbe90-353">This interface has a single member, [IFormattable.ToString(String, IFormatProvider)](xref:System.IFormattable.ToString(System.String,System.IFormatProvider)), that includes both a format string and a format provider as parameters.</span></span>

<span data-ttu-id="dbe90-354">Implementar a interface [IFormattable](xref:System.IFormattable) para a classe definida pelo aplicativo oferece duas vantagens:</span><span class="sxs-lookup"><span data-stu-id="dbe90-354">Implementing the [IFormattable](xref:System.IFormattable) interface for your application-defined class offers two advantages:</span></span> 

* <span data-ttu-id="dbe90-355">Suporte para conversão de cadeia de caracteres pela classe [Convert](xref:System.Convert).</span><span class="sxs-lookup"><span data-stu-id="dbe90-355">Support for string conversion by the [Convert](xref:System.Convert) class.</span></span> <span data-ttu-id="dbe90-356">Chamadas para os métodos [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) e [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) chamam sua implementação [IFormattable](xref:System.IFormattable) automaticamente.</span><span class="sxs-lookup"><span data-stu-id="dbe90-356">Calls to the [Convert.ToString(Object)](xref:System.Convert.ToString(System.Object)) and [Convert.ToString(Object, IFormatProvider)](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) methods call your [IFormattable](xref:System.IFormattable) implementation automatically.</span></span>

* <span data-ttu-id="dbe90-357">Suporte à formatação composição.</span><span class="sxs-lookup"><span data-stu-id="dbe90-357">Support for composite formatting.</span></span> <span data-ttu-id="dbe90-358">Se um item de formato que inclui uma cadeia de caracteres de formato for usado para formatar seu tipo personalizado, o Common Language Runtime chamará automaticamente a implementação [IFormattable](xref:System.IFormattable) e passará a ele a cadeia de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="dbe90-358">If a format item that includes a format string is used to format your custom type, the Common Language Runtime automatically calls your [IFormattable](xref:System.IFormattable) implementation and passes it the format string.</span></span> <span data-ttu-id="dbe90-359">Para obter mais informações sobre formatação de composição com métodos como `String.Format` ou `Console.WriteLine`, veja a seção [Formatação de composição](#composite-formatting).</span><span class="sxs-lookup"><span data-stu-id="dbe90-359">For more information about composite formatting with methods such as `String.Format` or `Console.WriteLine`, see the [Composite formatting](#composite-formatting) section.</span></span>

<span data-ttu-id="dbe90-360">O exemplo a seguir define uma classe `Temperature` que implementa a interface [IFormattable](xref:System.IFormattable).</span><span class="sxs-lookup"><span data-stu-id="dbe90-360">The following example defines a `Temperature` class that implements the [IFormattable](xref:System.IFormattable) interface.</span></span> <span data-ttu-id="dbe90-361">Ela dá suporte aos especificadores de formato "C" ou "G" para exibir a temperatura em graus Celsius, o especificador de formato "F" para exibir a temperatura em Fahrenheit e o especificador de formato "K" para exibir a temperatura em Kelvin.</span><span class="sxs-lookup"><span data-stu-id="dbe90-361">It supports the "C" or "G" format specifiers to display the temperature in Celsius, the "F" format specifier to display the temperature in Fahrenheit, and the "K" format specifier to display the temperature in Kelvin.</span></span>

```csharp
using System;
using System.Globalization;

public class Temperature : IFormattable
{
   private decimal m_Temp;

   public Temperature(decimal temperature)
   {
      this.m_Temp = temperature;
   }

   public decimal Celsius
   {
      get { return this.m_Temp; }
   }

   public decimal Kelvin
   {
      get { return this.m_Temp + 273.15m; }   
   }

   public decimal Fahrenheit
   {
      get { return Math.Round((decimal) this.m_Temp * 9 / 5 + 32, 2); }
   }

   public override string ToString()
   {
      return this.ToString("G", null);
   }

   public string ToString(string format)
   {
      return this.ToString(format, null);
   }

   public string ToString(string format, IFormatProvider provider)  
   {
      // Handle null or empty arguments.
      if (String.IsNullOrEmpty(format)) format = "G";
      // Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant();

      if (provider == null) provider = NumberFormatInfo.CurrentInfo;

      switch (format)
      {
         // Convert temperature to Fahrenheit and return string.
         case "F":
            return this.Fahrenheit.ToString("N2", provider) + "°F";
         // Convert temperature to Kelvin and return string.
         case "K":
            return this.Kelvin.ToString("N2", provider) + "K";
         // Return temperature in Celsius.
         case "C":
         case "G":
            return this.Celsius.ToString("N2", provider) + "°C";
         default:
            throw new FormatException(String.Format("The '{0}' format string is not supported.", format));
      }      
   }
}
```

```vb
Imports System.Globalization

Public Class Temperature : Implements IFormattable
   Private m_Temp As Decimal

   Public Sub New(temperature As Decimal)
      Me.m_Temp = temperature
   End Sub

   Public ReadOnly Property Celsius() As Decimal
      Get
         Return Me.m_Temp
      End Get   
   End Property

   Public ReadOnly Property Kelvin() As Decimal
      Get
         Return Me.m_Temp + 273.15d   
      End Get
   End Property

   Public ReadOnly Property Fahrenheit() As Decimal
      Get
         Return Math.Round(CDec(Me.m_Temp * 9 / 5 + 32), 2)
      End Get      
   End Property

   Public Overrides Function ToString() As String
      Return Me.ToString("G", Nothing)
   End Function

   Public Overloads Function ToString(format As String) As String
      Return Me.ToString(format, Nothing)
   End Function

   Public Overloads Function ToString(format As String, provider As IFormatProvider) As String _  
      Implements IFormattable.ToString

      ' Handle null or empty arguments.
      If String.IsNullOrEmpty(format) Then format = "G"
      ' Remove any white space and convert to uppercase.
      format = format.Trim().ToUpperInvariant()

      If provider Is Nothing Then provider = NumberFormatInfo.CurrentInfo

      Select Case format
         ' Convert temperature to Fahrenheit and return string.
         Case "F"
            Return Me.Fahrenheit.ToString("N2", provider) & "°F"
         ' Convert temperature to Kelvin and return string.
         Case "K"
            Return Me.Kelvin.ToString("N2", provider) & "K"
         ' Return temperature in Celsius.
         Case "C", "G"
            Return Me.Celsius.ToString("N2", provider) & "°C"
         Case Else
            Throw New FormatException(String.Format("The '{0}' format string is not supported.", format))
      End Select      
   End Function
End Class
```

<span data-ttu-id="dbe90-362">O exemplo a seguir instancia um objeto `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="dbe90-362">The following example instantiates a `Temperature` object.</span></span> <span data-ttu-id="dbe90-363">Depois, ele chama o método [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) e usa várias cadeias de caracteres de formato de composição para obter diferentes representações de um objeto `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="dbe90-363">It then calls the [ToString](xref:System.Convert.ToString(System.Object,System.IFormatProvider)) method and uses several composite format strings to obtain different string representations of a `Temperature` object.</span></span> <span data-ttu-id="dbe90-364">Cada uma dessas chamadas de método, por sua vez, chama a implementação [IFormattable](xref:System.IFormattable) da classe `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="dbe90-364">Each of these method calls, in turn, calls the [IFormattable](xref:System.IFormattable) implementation of the `Temperature` class.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      Temperature temp1 = new Temperature(22m);
      Console.WriteLine(Convert.ToString(temp1, new CultureInfo("ja-JP")));
      Console.WriteLine("Temperature: {0:K}", temp1);
      Console.WriteLine("Temperature: {0:F}", temp1);
      Console.WriteLine(String.Format(new CultureInfo("fr-FR"), "Temperature: {0:F}", temp1));
   }
}
// The example displays the following output:
//       22.00°C
//       Temperature: 295.15°K
//       Temperature: 71.60°F
//       Temperature: 71,60°F
```

```vb
Public Module Example
   Public Sub Main()
      Dim temp1 As New Temperature(22d)
      Console.WriteLine(Convert.ToString(temp1, New CultureInfo("ja-JP")))
      Console.WriteLine("Temperature: {0:K}", temp1)
      Console.WriteLine("Temperature: {0:F}", temp1)
      Console.WriteLine(String.Format(New CultureInfo("fr-FR"), "Temperature: {0:F}", temp1)) 
   End Sub
End Module
' The example displays the following output:
'       22.00°C
'       Temperature: 295.15°K
'       Temperature: 71.60°F
'       Temperature: 71,60°F
```

## <a name="composite-formatting"></a><span data-ttu-id="dbe90-365">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="dbe90-365">Composite formatting</span></span>

<span data-ttu-id="dbe90-366">Alguns métodos, tais como `String.Format` e `StringBuilder.AppendFormat`, dão suporte à formatação de composição.</span><span class="sxs-lookup"><span data-stu-id="dbe90-366">Some methods, such as `String.Format` and `StringBuilder.AppendFormat`, support composite formatting.</span></span> <span data-ttu-id="dbe90-367">Uma cadeia de caracteres de formato de composição é um tipo de modelo que retorna uma única cadeia de caracteres que incorpora a representação de cadeia de caracteres de zero, um ou mais objetos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-367">A composite format string is a kind of template that returns a single string that incorporates the string representation of zero, one, or more objects.</span></span> <span data-ttu-id="dbe90-368">Cada objeto é representado na cadeia de caracteres de formato de composição por um item de formato indexado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-368">Each object is represented in the composite format string by an indexed format item.</span></span> <span data-ttu-id="dbe90-369">O índice do item de formato corresponde à posição do objeto que ele representa na lista de parâmetros do método.</span><span class="sxs-lookup"><span data-stu-id="dbe90-369">The index of the format item corresponds to the position of the object that it represents in the method's parameter list.</span></span> <span data-ttu-id="dbe90-370">Os índices são baseados em zero.</span><span class="sxs-lookup"><span data-stu-id="dbe90-370">Indexes are zero-based.</span></span> <span data-ttu-id="dbe90-371">Por exemplo, na seguinte chamada para o método `String.Format`, o primeiro item de formato, `{0:D}`, é substituído pela representação de cadeia de caracteres de `thatDate`; o segundo item de formato, `{1}`, é substituído pela representação de cadeia de caracteres de `item1` e, por fim, o terceiro item de formato, `{2:C2}`, é substituído pela representação de cadeia de caracteres de `item1.Value`.</span><span class="sxs-lookup"><span data-stu-id="dbe90-371">For example, in the following call to the `String.Format` method, the first format item, `{0:D}`, is replaced by the string representation of `thatDate`; the second format item, `{1}`, is replaced by the string representation of `item1`; and the third format item, `{2:C2}`, is replaced by the string representation of `item1.Value`.</span></span>

```csharp
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", 
                       thatDate, item1, item1.Value);
Console.WriteLine(result);                            
// The example displays output like the following if run on a system
// whose current culture is en-US:
//       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

```vb
result = String.Format("On {0:d}, the inventory of {1} was worth {2:C2}.", _
                       thatDate, item1, item1.Value)
Console.WriteLine(result)                            
' The example displays output like the following if run on a system
' whose current culture is en-US:
'       On 5/1/2009, the inventory of WidgetA was worth $107.44.
```

<span data-ttu-id="dbe90-372">Além de substituir um item de formato pela representação de cadeia de caracteres de seu objeto correspondente, os itens de formato também permitem que você controle o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbe90-372">In addition to replacing a format item with the string representation of its corresponding object, format items also let you control the following:</span></span> 

* <span data-ttu-id="dbe90-373">O modo específico em que um objeto é representado como uma cadeia de caracteres, se o objeto implementa a interface [IFormattable](xref:System.IFormattable) e se dá suporte a cadeias de caracteres de formato.</span><span class="sxs-lookup"><span data-stu-id="dbe90-373">The specific way in which an object is represented as a string, if the object implements the [IFormattable](xref:System.IFormattable) interface and supports format strings.</span></span> <span data-ttu-id="dbe90-374">Você pode fazer isso seguindo o índice do item de formato com um : (dois-pontos) seguido por uma cadeia de caracteres de formato válido.</span><span class="sxs-lookup"><span data-stu-id="dbe90-374">You do this by following the format item's index with a : (colon) followed by a valid format string.</span></span> <span data-ttu-id="dbe90-375">O exemplo anterior já fez isso ao formatar um valor de data com a cadeia de caracteres de formato (por exemplo, `{0:d}`) "d" (padrão de data abreviada) e formatando um valor numérico com a cadeia de caracteres de formato "C2" (por exemplo, `{2:C2}`) para representar o número como um valor de moeda com dois dígitos decimais fracionários.</span><span class="sxs-lookup"><span data-stu-id="dbe90-375">The previous example did this by formatting a date value with the "d" (short date pattern) format string (for example, `{0:d}`) and by formatting a numeric value with the "C2" format string (for example, `{2:C2}` to represent the number as a currency value with two fractional decimal digits).</span></span> 

* <span data-ttu-id="dbe90-376">A largura do campo que contém a representação de cadeia de caracteres do objeto e o alinhamento da representação de cadeia de caracteres nesse campo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-376">The width of the field that contains the object's string representation, and the alignment of the string representation in that field.</span></span> <span data-ttu-id="dbe90-377">Você pode fazer isso seguindo o índice do item de formato com uma , (vírgula) seguida da largura do campo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-377">You do this by following the format item's index with a , (comma) followed the field width.</span></span> <span data-ttu-id="dbe90-378">A cadeia de caracteres será alinhada à direita no campo se a largura do campo for um valor positivo ou à esquerda se esse valor for negativo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-378">The string is right-aligned in the field if the field width is a positive value, and it is left-aligned if the field width is a negative value.</span></span> <span data-ttu-id="dbe90-379">O exemplo a seguir alinha os valores de data à esquerda em um campo de 20 caracteres e alinha valores decimais com um dígito fracionário à direita em um campo de 11 caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe90-379">The following example left-aligns date values in a 20-character field, and it right-aligns decimal values with one fractional digit in an 11-character field.</span></span> 

```csharp
DateTime startDate = new DateTime(2015, 8, 28, 6, 0, 0);
decimal[] temps = { 73.452m, 68.98m, 72.6m, 69.24563m,
                   74.1m, 72.156m, 72.228m };
Console.WriteLine("{0,-20} {1,11}\n", "Date", "Temperature");
for (int ctr = 0; ctr < temps.Length; ctr++)
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps[ctr]);

// The example displays the following output:
//       Date                 Temperature
//
//       8/28/2015 6:00 AM           73.5
//       8/29/2015 6:00 AM           69.0
//       8/30/2015 6:00 AM           72.6
//       8/31/2015 6:00 AM           69.2
//       9/1/2015 6:00 AM            74.1
//       9/2/2015 6:00 AM            72.2
//       9/3/2015 6:00 AM            72.2
```

```vb
Dim startDate As New Date(2015, 8, 28, 6, 0, 0)
Dim temps() As Decimal = { 73.452, 68.98, 72.6, 69.24563,
                           74.1, 72.156, 72.228 }
Console.WriteLine("{0,-20} {1,11}", "Date", "Temperature")
Console.WriteLine()
For ctr As Integer = 0 To temps.Length - 1
   Console.WriteLine("{0,-20:g} {1,11:N1}", startDate.AddDays(ctr), temps(ctr))
Next
' The example displays the following output:
'       Date                 Temperature
'
'       8/28/2015 6:00 AM           73.5
'       8/29/2015 6:00 AM           69.0
'       8/30/2015 6:00 AM           72.6
'       8/31/2015 6:00 AM           69.2
'       9/1/2015 6:00 AM            74.1
'       9/2/2015 6:00 AM            72.2
'       9/3/2015 6:00 AM            72.2
```

<span data-ttu-id="dbe90-380">Observe que, se o componente de cadeia de caracteres de alinhamento e o componente de cadeia de caracteres de formato estiverem presentes, o primeiro precederá o último (por exemplo, `{0,-20:g}`.</span><span class="sxs-lookup"><span data-stu-id="dbe90-380">Note that, if both the alignment string component and the format string component are present, the former precedes the latter (for example, `{0,-20:g}`.</span></span> 

<span data-ttu-id="dbe90-381">Para obter mais informações sobre formatação de composição, veja [Formatação de composição](composite-format.md).</span><span class="sxs-lookup"><span data-stu-id="dbe90-381">For more information about composite formatting, see [Composite formatting](composite-format.md).</span></span>

## <a name="custom-formatting-with-icustomformatter"></a><span data-ttu-id="dbe90-382">Formatação personalizada com ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="dbe90-382">Custom formatting with ICustomFormatter</span></span>

<span data-ttu-id="dbe90-383">Dois métodos de formatação de composição, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) e [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), incluem um parâmetro de provedor de formato que dá suporte à formatação personalizada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-383">Two composite formatting methods, [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object[])) and [StringBuilder.AppendFormat(IFormatProvider, String, Object[])](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)), include a format provider parameter that supports custom formatting.</span></span> <span data-ttu-id="dbe90-384">Quando um desses métodos de formatação é chamado, ele passa um objeto [Type](xref:System.Type) que representa uma interface [ICustomFormatter](xref:System.ICustomFormatter) para o método `GetFormat` do provedor de formato.</span><span class="sxs-lookup"><span data-stu-id="dbe90-384">When either of these formatting methods is called, it passes a [Type](xref:System.Type) object that represents an [ICustomFormatter](xref:System.ICustomFormatter) interface to the format provider’s `GetFormat` method.</span></span> <span data-ttu-id="dbe90-385">O `GetFormat` em seguida, o método é responsável por retornar a implementação [ICustomFormatter](xref:System.ICustomFormatter) que oferece formatação personalizada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-385">The `GetFormat` method is then responsible for returning the [ICustomFormatter](xref:System.ICustomFormatter) implementation that provides custom formatting.</span></span>

<span data-ttu-id="dbe90-386">A interface [ICustomFormatter](xref:System.ICustomFormatter) tem um único método, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), que é chamado automaticamente por um método de formatação de composição, uma vez para cada item de formato em uma cadeia de caracteres de formato de composição.</span><span class="sxs-lookup"><span data-stu-id="dbe90-386">The [ICustomFormatter](xref:System.ICustomFormatter) interface has a single method, [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)), that is called automatically by a composite formatting method, once for each format item in a composite format string.</span></span> <span data-ttu-id="dbe90-387">O método [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) tem três parâmetros: uma cadeia de caracteres de formato, que representa o argumento *formatString* em um item de formato, um objeto a ser formatado e um objeto [IFormatProvider](xref:System.IFormatProvider) que oferece serviços de formatação.</span><span class="sxs-lookup"><span data-stu-id="dbe90-387">The [Format(String, Object, IFormatProvider)](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method has three parameters: a format string, which represents the *formatString* argument in a format item, an object to format, and an [IFormatProvider](xref:System.IFormatProvider) object that provides formatting services.</span></span> <span data-ttu-id="dbe90-388">Normalmente, a classe que implementa [ICustomFormatter](xref:System.ICustomFormatter) também implementa [IFormatProvider](xref:System.IFormatProvider), portanto, este último parâmetro é uma referência para a própria classe de formatação personalizada.</span><span class="sxs-lookup"><span data-stu-id="dbe90-388">Typically, the class that implements [ICustomFormatter](xref:System.ICustomFormatter) also implements [IFormatProvider](xref:System.IFormatProvider), so this last parameter is a reference to the custom formatting class itself.</span></span> <span data-ttu-id="dbe90-389">O método retorna uma representação de cadeia de caracteres formatada personalizada do objeto a ser formatado.</span><span class="sxs-lookup"><span data-stu-id="dbe90-389">The method returns a custom formatted string representation of the object to be formatted.</span></span> <span data-ttu-id="dbe90-390">Se o método não for capaz de formatar o objeto, ele deverá retornar uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="dbe90-390">If the method cannot format the object, it should return a null reference.</span></span>

<span data-ttu-id="dbe90-391">O exemplo a seguir fornece uma implementação [ICustomFormatter](xref:System.ICustomFormatter) chamada `ByteByByteFormatter` que exibe valores inteiros como uma sequência de valores hexadecimais de dois dígitos seguidos por um espaço.</span><span class="sxs-lookup"><span data-stu-id="dbe90-391">The following example provides an [ICustomFormatter](xref:System.ICustomFormatter) implementation named `ByteByByteFormatter` that displays integer values as a sequence of two-digit hexadecimal values followed by a space.</span></span>

```csharp
public class ByteByByteFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   { 
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }

   public string Format(string format, object arg, 
                          IFormatProvider formatProvider)
   {   
      if (! formatProvider.Equals(this)) return null;

      // Handle only hexadecimal format string.
      if (! format.StartsWith("X")) return null;

      byte[] bytes;
      string output = null;

      // Handle only integral types.
      if (arg is Byte) 
         bytes = BitConverter.GetBytes((Byte) arg);
      else if (arg is Int16)
         bytes = BitConverter.GetBytes((Int16) arg);
      else if (arg is Int32)
         bytes = BitConverter.GetBytes((Int32) arg);
      else if (arg is Int64)   
         bytes = BitConverter.GetBytes((Int64) arg);
      else if (arg is SByte)
         bytes = BitConverter.GetBytes((SByte) arg);
      else if (arg is UInt16)
         bytes = BitConverter.GetBytes((UInt16) arg);
      else if (arg is UInt32)
         bytes = BitConverter.GetBytes((UInt32) arg);
      else if (arg is UInt64)
         bytes = BitConverter.GetBytes((UInt64) arg);
      else
         return null;

      for (int ctr = bytes.Length - 1; ctr >= 0; ctr--)
         output += String.Format("{0:X2} ", bytes[ctr]);   

      return output.Trim();
   }
}
```

```vb
Public Class ByteByByteFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If
   End Function

   Public Function Format(fmt As String, arg As Object, 
                          formatProvider As IFormatProvider) As String _
                          Implements ICustomFormatter.Format

      If Not formatProvider.Equals(Me) Then Return Nothing

      ' Handle only hexadecimal format string.
      If Not fmt.StartsWith("X") Then 
            Return Nothing
      End If

      ' Handle only integral types.
      If Not typeof arg Is Byte AndAlso
         Not typeof arg Is Int16 AndAlso
         Not typeof arg Is Int32 AndAlso
         Not typeof arg Is Int64 AndAlso
         Not typeof arg Is SByte AndAlso
         Not typeof arg Is UInt16 AndAlso
         Not typeof arg Is UInt32 AndAlso
         Not typeof arg Is UInt64 Then _
            Return Nothing

      Dim bytes() As Byte = BitConverter.GetBytes(arg)
      Dim output As String = Nothing

      For ctr As Integer = bytes.Length - 1 To 0 Step -1
         output += String.Format("{0:X2} ", bytes(ctr))   
      Next

      Return output.Trim()
   End Function
End Class
```

<span data-ttu-id="dbe90-392">O exemplo a seguir usa a classe `ByteByByteFormatter` para formatar valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="dbe90-392">The following example uses the `ByteByByteFormatter` class to format integer values.</span></span> <span data-ttu-id="dbe90-393">Observe que o método [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) é chamado mais de uma vez na segunda chamada do método [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) e que o provedor padrão [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) é usado na terceira chamada de método porque o método `.ByteByByteFormatter.Format` não reconhece a cadeia de caracteres de formato "N0" e retorna uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="dbe90-393">Note that the [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method is called more than once in the second [String.Format(IFormatProvider, String, Object[])](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) method call, and that the default [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) provider is used in the third method call because the `.ByteByByteFormatter.Format` method does not recognize the "N0" format string and returns a null reference.</span></span>

```csharp
public class Example
{
   public static void Main()
   {
      long value = 3210662321; 
      byte value1 = 214;
      byte value2 = 19;

      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X}", value));
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 & value2));                                
      Console.WriteLine(String.Format(new ByteByByteFormatter(), "{0,10:N0}", value));
   }
}
// The example displays the following output:
//       00 00 00 00 BF 5E D1 B1
//       00 D6 And 00 13 = 00 12 (018)
//       3,210,662,321
```

```vb
Public Module Example
   Public Sub Main()
      Dim value As Long = 3210662321 
      Dim value1 As Byte = 214
      Dim value2 As Byte = 19

      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X}", value)))
      Console.WriteLine((String.Format(New ByteByByteFormatter(), "{0:X} And {1:X} = {2:X} ({2:000})", 
                                      value1, value2, value1 And value2)))                                
      Console.WriteLine(String.Format(New ByteByByteFormatter(), "{0,10:N0}", value))
   End Sub
End Module
' The example displays the following output:
'       00 00 00 00 BF 5E D1 B1
'       00 D6 And 00 13 = 00 12 (018)
'       3,210,662,321
```

## <a name="related-topics"></a><span data-ttu-id="dbe90-394">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="dbe90-394">Related topics</span></span>

<span data-ttu-id="dbe90-395">Título</span><span class="sxs-lookup"><span data-stu-id="dbe90-395">Title</span></span> | <span data-ttu-id="dbe90-396">Definição</span><span class="sxs-lookup"><span data-stu-id="dbe90-396">Definition</span></span>
----- | ----------
[<span data-ttu-id="dbe90-397">Cadeias de caracteres de formato numérico padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-397">Standard numeric format strings</span></span>](standard-numeric.md) | <span data-ttu-id="dbe90-398">Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores numéricos frequentemente usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-398">Describes standard format strings that create commonly used string representations of numeric values.</span></span> 
[<span data-ttu-id="dbe90-399">Cadeias de caracteres de formato numérico personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-399">Custom numeric format strings</span></span>](custom-numeric.md) | <span data-ttu-id="dbe90-400">Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores numéricos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-400">Describes custom format strings that create application-specific formats for numeric values.</span></span>
[<span data-ttu-id="dbe90-401">Cadeias de caracteres de formato de data e hora padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-401">Standard date and time format strings</span></span>](standard-datetime.md) |  <span data-ttu-id="dbe90-402">Descreve cadeias de caracteres de formato padrão que criam representações de cadeia de caracteres de valores [DateTime](xref:System.DateTime) frequentemente usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-402">Describes standard format strings that create commonly used string representations of [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="dbe90-403">Cadeias de caracteres de formato de data e hora personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-403">Custom date and time format strings</span></span>](custom-datetime.md) | <span data-ttu-id="dbe90-404">Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para valores [DateTime](xref:System.DateTime).</span><span class="sxs-lookup"><span data-stu-id="dbe90-404">Describes custom format strings that create application-specific formats for [DateTime](xref:System.DateTime) values.</span></span>
[<span data-ttu-id="dbe90-405">Cadeias de caracteres de formato TimeSpan padrão</span><span class="sxs-lookup"><span data-stu-id="dbe90-405">Standard TimeSpan format strings</span></span>](standard-timespan.md) | <span data-ttu-id="dbe90-406">Descreve cadeias de caracteres de formato padrão que criam representações de intervalos de tempo frequentemente usadas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-406">Describes standard format strings that create commonly used string representations of time intervals.</span></span>
[<span data-ttu-id="dbe90-407">Cadeias de caracteres de formato TimeSpan personalizado</span><span class="sxs-lookup"><span data-stu-id="dbe90-407">Custom TimeSpan format strings</span></span>](custom-timespan.md) | <span data-ttu-id="dbe90-408">Descreve cadeias de caracteres de formato personalizado que criam formatos específicos de aplicativo para intervalos de tempo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-408">Describes custom format strings that create application-specific formats for time intervals.</span></span>
[<span data-ttu-id="dbe90-409">Cadeias de caracteres de formato de enumeração</span><span class="sxs-lookup"><span data-stu-id="dbe90-409">Enumeration format strings</span></span>](enumeration-format.md) | <span data-ttu-id="dbe90-410">Descreve cadeias de caracteres de formato padrão que são usadas para criar representações de cadeia de caracteres de valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="dbe90-410">Describes standard format strings that are used to create string representations of enumeration values.</span></span>
[<span data-ttu-id="dbe90-411">Formatação de composição</span><span class="sxs-lookup"><span data-stu-id="dbe90-411">Composite formatting</span></span>](composite-format.md) | <span data-ttu-id="dbe90-412">Descreve como inserir um ou mais valores formatados em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="dbe90-412">Describes how to embed one or more formatted values in a string.</span></span> <span data-ttu-id="dbe90-413">A cadeia de caracteres pode posteriormente ser exibida no console ou gravada em um fluxo.</span><span class="sxs-lookup"><span data-stu-id="dbe90-413">The string can subsequently be displayed on the console or written to a stream.</span></span>
[<span data-ttu-id="dbe90-414">Executando operações de formatação</span><span class="sxs-lookup"><span data-stu-id="dbe90-414">Performing formatting operations</span></span>](performing-formatting-operations.md) | <span data-ttu-id="dbe90-415">Lista os tópicos que fornecem instruções passo a passo para executar operações de formatação específicas.</span><span class="sxs-lookup"><span data-stu-id="dbe90-415">Lists topics that provide step-by-step instructions for performing specific formatting operations.</span></span>
[<span data-ttu-id="dbe90-416">Analisando cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="dbe90-416">Parsing strings</span></span>](parsing-strings.md) | <span data-ttu-id="dbe90-417">Descreve como inicializar objetos para os valores descritos pelas representações de cadeia de caracteres desses objetos.</span><span class="sxs-lookup"><span data-stu-id="dbe90-417">Describes how to initialize objects to the values described by string representations of those objects.</span></span> <span data-ttu-id="dbe90-418">A análise é a operação inversa da formatação.</span><span class="sxs-lookup"><span data-stu-id="dbe90-418">Parsing is the inverse operation of formatting.</span></span>

## <a name="reference"></a><span data-ttu-id="dbe90-419">Referência</span><span class="sxs-lookup"><span data-stu-id="dbe90-419">Reference</span></span>

[<span data-ttu-id="dbe90-420">System.IFormattable</span><span class="sxs-lookup"><span data-stu-id="dbe90-420">System.IFormattable</span></span>](xref:System.IFormattable)

[<span data-ttu-id="dbe90-421">System.IFormatProvider</span><span class="sxs-lookup"><span data-stu-id="dbe90-421">System.IFormatProvider</span></span>](xref:System.IFormatProvider)

[<span data-ttu-id="dbe90-422">System.ICustomFormatter</span><span class="sxs-lookup"><span data-stu-id="dbe90-422">System.ICustomFormatter</span></span>](xref:System.ICustomFormatter)

