---
title: "Conversão de tipos de dados XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="e2d28-102">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="e2d28-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="e2d28-103">A maioria dos métodos encontrado em uma **XmlConvert** classe são usadas para converter dados de cadeias de caracteres e formatos fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="e2d28-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="e2d28-104">Os métodos são independentes de localidade.</span><span class="sxs-lookup"><span data-stu-id="e2d28-104">Methods are locale independent.</span></span> <span data-ttu-id="e2d28-105">Isso significa que não levam em conta as configurações de localidade ao fazer a conversão.</span><span class="sxs-lookup"><span data-stu-id="e2d28-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="e2d28-106">Lê a cadeia de caracteres como tipos</span><span class="sxs-lookup"><span data-stu-id="e2d28-106">Reading String as types</span></span>  
 <span data-ttu-id="e2d28-107">O exemplo a seguir lê uma cadeia de caracteres e o converte em uma **DateTime** tipo.</span><span class="sxs-lookup"><span data-stu-id="e2d28-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="e2d28-108">Dado seguinte XML entre:</span><span class="sxs-lookup"><span data-stu-id="e2d28-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="e2d28-109">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="e2d28-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="e2d28-110">Esse código converte a cadeia de caracteres para o **DateTime** formato:</span><span class="sxs-lookup"><span data-stu-id="e2d28-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="e2d28-111">Escrevendo cadeias de caracteres como tipos</span><span class="sxs-lookup"><span data-stu-id="e2d28-111">Writing Strings as types</span></span>  
 <span data-ttu-id="e2d28-112">O exemplo a seguir lê um **Int32** e o converte em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="e2d28-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="e2d28-113">Dado seguinte XML entre:</span><span class="sxs-lookup"><span data-stu-id="e2d28-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="e2d28-114">**Entrada**</span><span class="sxs-lookup"><span data-stu-id="e2d28-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="e2d28-115">Esse código converte o **Int32** em uma **cadeia de caracteres**:</span><span class="sxs-lookup"><span data-stu-id="e2d28-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2d28-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2d28-116">See Also</span></span>  
 [<span data-ttu-id="e2d28-117">Convertendo cadeias de caracteres para tipos de dados do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e2d28-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="e2d28-118">Convertendo tipos do .NET Framework para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="e2d28-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
