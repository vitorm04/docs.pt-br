---
title: "Como: gravar dados de objeto para um arquivo XML (Visual Basic) | Microsoft Docs"
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
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: gravar dados de objeto para um arquivo XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Teste de exemplo grava o objeto de uma classe para um arquivo XML usando o <xref:System.Xml.Serialization.XmlSerializer> classe.  
  
## Exemplo  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## Compilando o código  
 A classe deve ter um construtor público sem parâmetros.  
  
## Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   A classe sendo serializada não tem um construtor público, sem parâmetro.  
  
-   O arquivo existe e é somente leitura \(<xref:System.IO.IOException>\).  
  
-   O caminho é muito longo \(<xref:System.IO.PathTooLongException>\).  
  
-   O disco está cheio \(<xref:System.IO.IOException>\).  
  
## Segurança do .NET Framework  
 Este exemplo cria um novo arquivo, se o arquivo ainda não existir. Se um aplicativo precisar criar um arquivo, o aplicativo precisa `Create` acesso para a pasta. Se o arquivo já existir, o aplicativo precisa apenas `Write` acessar, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder `Read` acesso a um único arquivo, em vez de `Create` acesso para uma pasta.  
  
## Consulte também  
 <xref:System.IO.StreamWriter>   
 [Como: ler dados de objeto de um arquivo XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [Serialização \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)