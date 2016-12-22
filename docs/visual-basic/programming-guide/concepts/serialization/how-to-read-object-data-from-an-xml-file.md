---
title: "Como: ler dados de objeto de um arquivo XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: ler dados de objeto de um arquivo XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este exemplo lê objeto dados que foram previamente gravados em um arquivo XML usando o <xref:System.Xml.Serialization.XmlSerializer> classe.  
  
## Exemplo  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## Compilando o código  
 Substitua o nome de arquivo "c:\\temp\\SerializationOverview.xml" com o nome do arquivo que contém os dados serializados. Para obter mais informações sobre serialização de dados, consulte [Como: gravar dados de objeto para um arquivo XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 A classe deve ter um construtor público sem parâmetros.  
  
 Apenas propriedades públicas e campos estão desserializados.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   A classe sendo serializada não tem um construtor público, sem parâmetro.  
  
-   Os dados no arquivo não representam dados da classe a ser desserializado.  
  
-   O arquivo não existe \(<xref:System.IO.IOException>\).  
  
## Segurança do .NET Framework  
 Sempre verifique se as entradas e nunca desserializar dados de uma fonte não confiável. O objeto recriado é executado em um computador local com as permissões do código que desserializado\-lo. Verifique se todas as entradas antes de usar os dados em seu aplicativo.  
  
## Consulte também  
 <xref:System.IO.StreamWriter>   
 [Como: gravar dados de objeto para um arquivo XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)   
 [Serialização \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)