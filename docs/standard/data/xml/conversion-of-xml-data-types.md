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
# <a name="conversion-of-xml-data-types"></a>Conversão de tipos de dados XML
A maioria dos métodos localizados em uma classe **XmlConvert** é usada para converter dados entre cadeias de caracteres e formatos fortemente tipados. Os métodos são independentes de localidade. Isso significa que não levam em conta as configurações de localidade ao fazer a conversão.  
  
## <a name="reading-string-as-types"></a>Lê a cadeia de caracteres como tipos  
 O exemplo a seguir lê uma cadeia de caracteres e convertê-lo para um tipo de **DateTime**.  
  
 Dado seguinte XML entre:  
  
 **Entrada**  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 Este código converte a cadeia de caracteres o formato **DateTime**:  
  
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
  
## <a name="writing-strings-as-types"></a>Escrevendo cadeias de caracteres como tipos  
 O exemplo a seguir lê um **Int32** e o converte em uma cadeia de caracteres.  
  
 Dado seguinte XML entre:  
  
 **Entrada**  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 Este código converte **Int32** em uma **Cadeia de caracteres**:  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a>Consulte também

- [Convertendo cadeias de caracteres para tipos de dados do .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [Convertendo tipos do .NET Framework em cadeias de caracteres](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
