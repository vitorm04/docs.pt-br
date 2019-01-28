---
title: Convertendo cadeias de caracteres em tipos de dados do .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 376dd9df4666193f8e5a6be83f3fcaf5dc32f1a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544595"
---
# <a name="converting-strings-to-net-framework-data-types"></a><span data-ttu-id="936b2-102">Convertendo cadeias de caracteres em tipos de dados do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="936b2-102">Converting Strings to .NET Framework Data Types</span></span>
<span data-ttu-id="936b2-103">Se você quiser converter uma cadeia de caracteres para um tipo de dados do .NET Framework, use o método **XmlConvert** que se adapta aos requisitos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="936b2-103">If you want to convert a string to a .NET Framework data type, use the **XmlConvert** method that fits the application requirements.</span></span> <span data-ttu-id="936b2-104">Para obter uma lista de todos os métodos de conversão disponíveis na classe **XmlConvert**, confira <xref:System.Xml.XmlConvert>.</span><span class="sxs-lookup"><span data-stu-id="936b2-104">For a list of all conversion methods available in the **XmlConvert** class, see <xref:System.Xml.XmlConvert>.</span></span>  
  
 <span data-ttu-id="936b2-105">A cadeia de caracteres retornada do método **ToString** é uma versão da cadeia de caracteres dos dados que são passados.</span><span class="sxs-lookup"><span data-stu-id="936b2-105">The string returned from the **ToString** method is a string version of the data that is passed in.</span></span> <span data-ttu-id="936b2-106">Além disso, há vários tipos do .NET Framework que são convertidos usando a classe **XmlConvert** e, ainda assim, não usam os métodos na classe **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="936b2-106">Additionally, there are several .NET Framework types that convert using the **XmlConvert** class yet they do not use the methods in the **System.Convert** class.</span></span> <span data-ttu-id="936b2-107">A classe **XmlConvert** segue a especificação do tipo de dados XSD (XML Schema) e tem um tipo de dados para o qual o **XmlConvert** pode ser mapeado.</span><span class="sxs-lookup"><span data-stu-id="936b2-107">The **XmlConvert** class follows the XML Schema (XSD) data type specification and has a data type that the **XmlConvert** can map to.</span></span>  
  
 <span data-ttu-id="936b2-108">A tabela a seguir lista os tipos de dados do .NET Framework e os tipos de cadeia de caracteres que são retornados usando o mapeamento do tipo de dados do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="936b2-108">The following table lists .NET Framework data types and the string types that are returned using XML Schema (XSD) data type mapping.</span></span> <span data-ttu-id="936b2-109">Esses tipos do .NET Framework não podem ser processados usando **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="936b2-109">These .NET Framework types cannot be processed using **System.Convert**.</span></span>  
  
|<span data-ttu-id="936b2-110">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="936b2-110">.NET Framework type</span></span>|<span data-ttu-id="936b2-111">Cadeia de caracteres retornada</span><span class="sxs-lookup"><span data-stu-id="936b2-111">String returned</span></span>|  
|-------------------------|---------------------|  
|<span data-ttu-id="936b2-112">Boolean</span><span class="sxs-lookup"><span data-stu-id="936b2-112">Boolean</span></span>|<span data-ttu-id="936b2-113">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="936b2-113">"true", "false"</span></span>|  
|<span data-ttu-id="936b2-114">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-114">Single.PositiveInfinity</span></span>|<span data-ttu-id="936b2-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-115">"INF"</span></span>|  
|<span data-ttu-id="936b2-116">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-116">Single.NegativeInfinity</span></span>|<span data-ttu-id="936b2-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-117">"-INF"</span></span>|  
|<span data-ttu-id="936b2-118">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-118">Double.PositiveInfinity</span></span>|<span data-ttu-id="936b2-119">"INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-119">"INF"</span></span>|  
|<span data-ttu-id="936b2-120">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-120">Double.NegativeInfinity</span></span>|<span data-ttu-id="936b2-121">"-INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-121">"-INF"</span></span>|  
|<span data-ttu-id="936b2-122">DateTime</span><span class="sxs-lookup"><span data-stu-id="936b2-122">DateTime</span></span>|<span data-ttu-id="936b2-123">O formato é "yyyy-MM-ddTHH:mm:sszzzzzz" e seus subconjuntos.</span><span class="sxs-lookup"><span data-stu-id="936b2-123">Format is "yyyy-MM-ddTHH:mm:sszzzzzz" and its subsets.</span></span>|  
|<span data-ttu-id="936b2-124">Timespan</span><span class="sxs-lookup"><span data-stu-id="936b2-124">Timespan</span></span>|<span data-ttu-id="936b2-125">O formato é PnYnMnTnHnMnS isto é, `P2Y10M15DT10H30M20S` é uma duração de 2 anos, 10 meses, 15 dias, 10 horas, 30 minutos e 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="936b2-125">Format is PnYnMnTnHnMnS that is, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10 hours, 30 minutes, and 20 seconds.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="936b2-126">Se estiver convertendo algum dos tipos do .NET Framework listados na tabela para uma cadeia de caracteres usando o método **ToString**, a cadeia de caracteres retornada não será o tipo base, mas o tipo de cadeia de caracteres do esquema XSD.</span><span class="sxs-lookup"><span data-stu-id="936b2-126">If converting any of the .NET Framework types listed in the table to a string using the **ToString** method, the returned string is not the base type, but the XML Schema (XSD) string type.</span></span>  
  
 <span data-ttu-id="936b2-127">O tipo de valor **DateTime** e **Timespan** diferem porque **DateTime** representa um momento no tempo, enquanto **TimeSpan** representa um intervalo de tempo.</span><span class="sxs-lookup"><span data-stu-id="936b2-127">The **DateTime** and **Timespan** value type differs in that a **DateTime** represents an instant in time, whereas a **TimeSpan** represents a time interval.</span></span> <span data-ttu-id="936b2-128">Os formatos **DateTime** e **Timespan** são definidos na especificação dos tipos de dados do esquema XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="936b2-128">The **DateTime** and **Timespan** formats are specified in the XML Schema (XSD) data types specification.</span></span> <span data-ttu-id="936b2-129">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="936b2-129">For example:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim [date] As New DateTime(2001, 8, 4)  
writer.WriteElementString("Date", XmlConvert.ToString([date]))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
DateTime date = new DateTime (2001, 08, 04);  
writer.WriteElementString("Date", XmlConvert.ToString(date));  
```  
  
 <span data-ttu-id="936b2-130">**Saída**</span><span class="sxs-lookup"><span data-stu-id="936b2-130">**Output**</span></span>  
  
 <span data-ttu-id="936b2-131">`<Date>2001-08-04T00:00:00</Date>`.</span><span class="sxs-lookup"><span data-stu-id="936b2-131">`<Date>2001-08-04T00:00:00</Date>`.</span></span>  
  
 <span data-ttu-id="936b2-132">O código a seguir converte um inteiro para uma cadeia de caracteres:</span><span class="sxs-lookup"><span data-stu-id="936b2-132">The following code converts an integer to a string:</span></span>  
  
```vb  
Dim writer As New XmlTextWriter("myfile.xml", Nothing)  
Dim value As Int32 = 200  
writer.WriteElementString("Number", XmlConvert.ToString(value))  
```  
  
```csharp  
XmlTextWriter writer = new XmlTextWriter("myfile.xml", null);  
Int32 value = 200;  
writer.WriteElementString("Number", XmlConvert.ToString(value));  
```  
  
 <span data-ttu-id="936b2-133">**Saída**</span><span class="sxs-lookup"><span data-stu-id="936b2-133">**Output**</span></span>  
  
 `<Number>200</Number>`  
  
 <span data-ttu-id="936b2-134">Entretanto, se você estiver convertendo uma cadeia de caracteres para **Boolean**, **Single** ou **Double**, o tipo do .NET Framework que é retornado não será igual ao tipo retornado ao usar a classe **System.Convert**.</span><span class="sxs-lookup"><span data-stu-id="936b2-134">However, if you are converting a string to **Boolean**, **Single**, or **Double**, the .NET Framework type that is returned is not the same as the type returned when using the **System.Convert** class.</span></span>  
  
## <a name="string-to-boolean"></a><span data-ttu-id="936b2-135">String para Boolean</span><span class="sxs-lookup"><span data-stu-id="936b2-135">String to Boolean</span></span>  
 <span data-ttu-id="936b2-136">A tabela a seguir mostra qual o tipo gerado para cadeias de caracteres de entradas consideradas, ao converter uma cadeia de caracteres para **Boolean** usando o método **ToBoolean**.</span><span class="sxs-lookup"><span data-stu-id="936b2-136">The following table shows what type is generated for the given input strings, when converting a string to **Boolean** using the **ToBoolean** method.</span></span>  
  
|<span data-ttu-id="936b2-137">Parâmetro de entrada válida de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="936b2-137">Valid string input parameter</span></span>|<span data-ttu-id="936b2-138">Tipo de saída do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="936b2-138">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="936b2-139">"true"</span><span class="sxs-lookup"><span data-stu-id="936b2-139">"true"</span></span>|<span data-ttu-id="936b2-140">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="936b2-140">Boolean.True</span></span>|  
|<span data-ttu-id="936b2-141">"1"</span><span class="sxs-lookup"><span data-stu-id="936b2-141">"1"</span></span>|<span data-ttu-id="936b2-142">Boolean.True</span><span class="sxs-lookup"><span data-stu-id="936b2-142">Boolean.True</span></span>|  
|<span data-ttu-id="936b2-143">"false"</span><span class="sxs-lookup"><span data-stu-id="936b2-143">"false"</span></span>|<span data-ttu-id="936b2-144">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="936b2-144">Boolean.False</span></span>|  
|<span data-ttu-id="936b2-145">"0"</span><span class="sxs-lookup"><span data-stu-id="936b2-145">"0"</span></span>|<span data-ttu-id="936b2-146">Boolean.False</span><span class="sxs-lookup"><span data-stu-id="936b2-146">Boolean.False</span></span>|  
  
 <span data-ttu-id="936b2-147">Por exemplo, considerando o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="936b2-147">For example, given the following XML:</span></span>  
  
 <span data-ttu-id="936b2-148">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="936b2-148">**Input**</span></span>  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 <span data-ttu-id="936b2-149">Ambos podem ser compreendidos pelo código a seguir e **bvalue** é **System.Boolean.True**:</span><span class="sxs-lookup"><span data-stu-id="936b2-149">Both can be understood by the following code, and **bvalue** is **System.Boolean.True**:</span></span>  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a><span data-ttu-id="936b2-150">String para Single</span><span class="sxs-lookup"><span data-stu-id="936b2-150">String to Single</span></span>  
 <span data-ttu-id="936b2-151">A tabela a seguir mostra qual o tipo gerado para cadeias de caracteres de entradas consideradas, ao converter uma cadeia de caracteres para **Single** usando o método **ToSingle**.</span><span class="sxs-lookup"><span data-stu-id="936b2-151">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToSingle** method.</span></span>  
  
|<span data-ttu-id="936b2-152">Parâmetro de entrada válida de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="936b2-152">Valid string input parameter</span></span>|<span data-ttu-id="936b2-153">Tipo de saída do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="936b2-153">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="936b2-154">"INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-154">"INF"</span></span>|<span data-ttu-id="936b2-155">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-155">Single.PositiveInfinity</span></span>|  
|<span data-ttu-id="936b2-156">"-INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-156">"-INF"</span></span>|<span data-ttu-id="936b2-157">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-157">Single.NegativeInfinity</span></span>|  
  
## <a name="string-to-double"></a><span data-ttu-id="936b2-158">String para Double</span><span class="sxs-lookup"><span data-stu-id="936b2-158">String to Double</span></span>  
 <span data-ttu-id="936b2-159">A tabela a seguir mostra qual o tipo gerado para cadeias de caracteres de entradas consideradas, ao converter uma cadeia de caracteres para **Single** usando o método **ToDouble**.</span><span class="sxs-lookup"><span data-stu-id="936b2-159">The following table shows what type is generated for the given input strings, when converting a string to a **Single** using the **ToDouble** method.</span></span>  
  
|<span data-ttu-id="936b2-160">Parâmetro de entrada válida de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="936b2-160">Valid string input parameter</span></span>|<span data-ttu-id="936b2-161">Tipo de saída do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="936b2-161">.NET Framework output type</span></span>|  
|----------------------------------|--------------------------------|  
|<span data-ttu-id="936b2-162">"INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-162">"INF"</span></span>|<span data-ttu-id="936b2-163">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-163">Double.PositiveInfinity</span></span>|  
|<span data-ttu-id="936b2-164">"-INF"</span><span class="sxs-lookup"><span data-stu-id="936b2-164">"-INF"</span></span>|<span data-ttu-id="936b2-165">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="936b2-165">Double.NegativeInfinity</span></span>|  
  
 <span data-ttu-id="936b2-166">O código a seguir grava `<Infinity>INF</Infinity>`:</span><span class="sxs-lookup"><span data-stu-id="936b2-166">The following code writes `<Infinity>INF</Infinity>`:</span></span>  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a><span data-ttu-id="936b2-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="936b2-167">See also</span></span>

- [<span data-ttu-id="936b2-168">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="936b2-168">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="936b2-169">Convertendo tipos do .NET Framework em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="936b2-169">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
