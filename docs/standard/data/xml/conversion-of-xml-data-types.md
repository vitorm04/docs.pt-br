---
title: Conversão de tipos de dados XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56b5b51848858b7f1240059ca30eb48474650b73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555122"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="0ec94-102">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="0ec94-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="0ec94-103">A maioria dos métodos localizados em uma classe **XmlConvert** é usada para converter dados entre cadeias de caracteres e formatos fortemente tipados.</span><span class="sxs-lookup"><span data-stu-id="0ec94-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="0ec94-104">Os métodos são independentes de localidade.</span><span class="sxs-lookup"><span data-stu-id="0ec94-104">Methods are locale independent.</span></span> <span data-ttu-id="0ec94-105">Isso significa que não levam em conta as configurações de localidade ao fazer a conversão.</span><span class="sxs-lookup"><span data-stu-id="0ec94-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="0ec94-106">Lê a cadeia de caracteres como tipos</span><span class="sxs-lookup"><span data-stu-id="0ec94-106">Reading String as types</span></span>  
 <span data-ttu-id="0ec94-107">O exemplo a seguir lê uma cadeia de caracteres e convertê-lo para um tipo de **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="0ec94-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="0ec94-108">Dado seguinte XML entre:</span><span class="sxs-lookup"><span data-stu-id="0ec94-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="0ec94-109">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="0ec94-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="0ec94-110">Este código converte a cadeia de caracteres o formato **DateTime**:</span><span class="sxs-lookup"><span data-stu-id="0ec94-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="0ec94-111">Escrevendo cadeias de caracteres como tipos</span><span class="sxs-lookup"><span data-stu-id="0ec94-111">Writing Strings as types</span></span>  
 <span data-ttu-id="0ec94-112">O exemplo a seguir lê um **Int32** e o converte em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0ec94-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="0ec94-113">Dado seguinte XML entre:</span><span class="sxs-lookup"><span data-stu-id="0ec94-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="0ec94-114">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="0ec94-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="0ec94-115">Este código converte **Int32** em uma **Cadeia de caracteres**:</span><span class="sxs-lookup"><span data-stu-id="0ec94-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ec94-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0ec94-116">See also</span></span>

- [<span data-ttu-id="0ec94-117">Convertendo cadeias de caracteres para tipos de dados do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0ec94-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="0ec94-118">Convertendo tipos do .NET Framework em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="0ec94-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
