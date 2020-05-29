---
title: Conversão de tipos de dados XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: b6e6f2c4b28e9220727bf0fe1a958a7b69111571
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202154"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="31852-102">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="31852-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="31852-103">A maioria dos métodos encontrados em uma classe **XmlConvert** é usada para converter dados entre cadeias de caracteres e formatos com rigidez de tipos.</span><span class="sxs-lookup"><span data-stu-id="31852-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="31852-104">Os métodos são independentes de localidade.</span><span class="sxs-lookup"><span data-stu-id="31852-104">Methods are locale independent.</span></span> <span data-ttu-id="31852-105">Isso significa que não levam em conta as configurações de localidade ao fazer a conversão.</span><span class="sxs-lookup"><span data-stu-id="31852-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="31852-106">Lê a cadeia de caracteres como tipos</span><span class="sxs-lookup"><span data-stu-id="31852-106">Reading String as types</span></span>  
 <span data-ttu-id="31852-107">O exemplo a seguir lê uma cadeia de caracteres e convertê-lo para um tipo de **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="31852-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="31852-108">Dado seguinte XML entre:</span><span class="sxs-lookup"><span data-stu-id="31852-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="31852-109">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="31852-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="31852-110">Este código converte a cadeia de caracteres o formato **DateTime**:</span><span class="sxs-lookup"><span data-stu-id="31852-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="31852-111">Escrevendo cadeias de caracteres como tipos</span><span class="sxs-lookup"><span data-stu-id="31852-111">Writing Strings as types</span></span>  
 <span data-ttu-id="31852-112">O exemplo a seguir lê um **Int32** e o converte em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="31852-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="31852-113">Dado seguinte XML entre:</span><span class="sxs-lookup"><span data-stu-id="31852-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="31852-114">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="31852-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="31852-115">Este código converte **Int32** em uma **Cadeia de caracteres**:</span><span class="sxs-lookup"><span data-stu-id="31852-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="31852-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="31852-116">See also</span></span>

- [<span data-ttu-id="31852-117">Convertendo cadeias de caracteres em tipos de dados do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="31852-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="31852-118">Convertendo tipos do .NET Framework para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="31852-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
