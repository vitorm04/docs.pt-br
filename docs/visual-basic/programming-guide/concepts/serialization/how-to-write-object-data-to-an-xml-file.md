---
title: 'Como: gravar dados de objeto para um arquivo XML (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 146ccb7b1999049106d5f0be1ce78e740dfcf060
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Como: gravar dados de objeto para um arquivo XML (Visual Basic)
Teste de exemplo grava o objeto de uma classe para um arquivo XML usando a <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer>  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
 A classe deve ter um construtor público sem parâmetros.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   A classe sendo serializada não tem um construtor público, sem parâmetro.  
  
-   O arquivo existe e é somente leitura (<xref:System.IO.IOException>).</xref:System.IO.IOException>  
  
-   O caminho é muito longo (<xref:System.IO.PathTooLongException>).</xref:System.IO.PathTooLongException>  
  
-   O disco está cheio (<xref:System.IO.IOException>).</xref:System.IO.IOException>  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Este exemplo cria um novo arquivo, se o arquivo ainda não existir. Se um aplicativo precisar criar um arquivo, o aplicativo precisa `Create` acesso para a pasta. Se o arquivo já existir, o aplicativo precisa apenas `Write` acessar, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder `Read` acesso a um único arquivo, em vez de `Create` acesso para uma pasta.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamWriter></xref:System.IO.StreamWriter>   
 [Como: ler dados de objeto de um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)   
 [Serialização (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
