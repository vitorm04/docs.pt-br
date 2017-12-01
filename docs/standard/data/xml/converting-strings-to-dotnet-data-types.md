---
title: Convertendo cadeias de caracteres em tipos de dados do .NET Framework
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
ms.assetid: 65455ef3-9120-412c-819b-d0f59f88ac09
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce594234e601cd8feb4723bbc383db9e3ed40522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-strings-to-net-framework-data-types"></a>Convertendo cadeias de caracteres em tipos de dados do .NET Framework
Se você quiser converter uma cadeia de caracteres em um tipo de dados do .NET Framework, use o **XmlConvert** método que atenda às necessidades do aplicativo. Para obter uma lista de todos os métodos de conversão disponíveis no **XmlConvert** de classe, consulte <xref:System.Xml.XmlConvert>.  
  
 A cadeia de caracteres retornada do **ToString** método é uma versão de cadeia de caracteres dos dados que são transmitidos. Além disso, há vários tipos de .NET Framework que convertem usando o **XmlConvert** ainda não usam os métodos de classe a **System. Convert** classe. O **XmlConvert** classe segue a especificação de tipo de dados de esquema XML (XSD) e tem dados de um tipo que o **XmlConvert** pode ser mapeado para.  
  
 A tabela a seguir lista os tipos de dados do .NET Framework e os tipos de cadeia de caracteres que são retornados usando o mapeamento do tipo de dados do esquema XSD. Esses tipos do .NET Framework não podem ser processados usando **System. Convert**.  
  
|Tipo do .NET Framework|Cadeia de caracteres retornada|  
|-------------------------|---------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|O formato é "yyyy-MM-ddTHH:mm:sszzzzzz" e seus subconjuntos.|  
|Timespan|O formato é PnYnMnTnHnMnS isto é, `P2Y10M15DT10H30M20S` é uma duração de 2 anos, 10 meses, 15 dias, 10 horas, 30 minutos e 20 segundos.|  
  
> [!NOTE]
>  Se a conversão de qualquer um dos tipos do .NET Framework listadas na tabela para uma cadeia de caracteres usando o **ToString** método, a cadeia de caracteres retornada não é o tipo base, mas o tipo de cadeia de caracteres do esquema XML (XSD).  
  
 O **DateTime** e **Timespan** difere do tipo de valor em que um **DateTime** representa um momento no tempo, enquanto um **TimeSpan** representa um intervalo de tempo. O **DateTime** e **Timespan** formatos são especificados na especificação de tipos de dados de esquema XML (XSD). Por exemplo:  
  
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
  
 **Saída**  
  
 `<Date>2001-08-04T00:00:00</Date>`.  
  
 O código a seguir converte um inteiro para uma cadeia de caracteres:  
  
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
  
 **Saída**  
  
 `<Number>200</Number>`  
  
 No entanto, se você estiver convertendo uma cadeia de caracteres para **booliano**, **único**, ou **duplo**, o tipo do .NET Framework que é retornado não é o mesmo que o tipo retornado ao usar o **System. Convert** classe.  
  
## <a name="string-to-boolean"></a>String para Boolean  
 A tabela a seguir mostra o tipo é gerado para as cadeias de caracteres de entrada fornecidas, ao converter uma cadeia de caracteres para **booliano** usando o **ToBoolean** método.  
  
|Parâmetro de entrada válida de cadeia de caracteres|Tipo de saída do .NET Framework|  
|----------------------------------|--------------------------------|  
|"true"|Boolean.True|  
|"1"|Boolean.True|  
|"false"|Boolean.False|  
|"0"|Boolean.False|  
  
 Por exemplo, considerando o seguinte XML:  
  
 **Entrada**  
  
```xml  
<Boolean>true</Boolean>  
<Boolean>1</Boolean>   
```  
  
 Ambos podem ser compreendidas pelo código a seguir, e **bDados do valor** é **System.Boolean.True**:  
  
```vb  
Dim bvalue As Boolean = _  
   XmlConvert.ToBoolean(reader.ReadElementString())  
Console.WriteLine(bvalue)  
```  
  
```csharp  
Boolean bvalue = XmlConvert.ToBoolean(reader.ReadElementString());  
Console.WriteLine(bvalue);  
```  
  
## <a name="string-to-single"></a>String para Single  
 A tabela a seguir mostra o tipo é gerado para as cadeias de caracteres de entrada fornecidas, ao converter uma cadeia de caracteres para um **único** usando o **ToSingle** método.  
  
|Parâmetro de entrada válida de cadeia de caracteres|Tipo de saída do .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Single.PositiveInfinity|  
|"-INF"|Single.NegativeInfinity|  
  
## <a name="string-to-double"></a>String para Double  
 A tabela a seguir mostra o tipo é gerado para as cadeias de caracteres de entrada fornecidas, ao converter uma cadeia de caracteres para um **único** usando o **ToDouble** método.  
  
|Parâmetro de entrada válida de cadeia de caracteres|Tipo de saída do .NET Framework|  
|----------------------------------|--------------------------------|  
|"INF"|Double.PositiveInfinity|  
|"-INF"|Double.NegativeInfinity|  
  
 O código a seguir grava `<Infinity>INF</Infinity>`:  
  
```vb  
Dim value As Double = Double.PositiveInfinity  
writer.WriteElementString("Infinity", XmlConvert.ToString(value))  
```  
  
```csharp  
Double value = Double.PositiveInfinity;  
writer.WriteElementString("Infinity", XmlConvert.ToString(value));  
```  
  
## <a name="see-also"></a>Consulte também  
 [Conversão de tipos de dados XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [Convertendo tipos do .NET Framework para cadeias de caracteres](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
