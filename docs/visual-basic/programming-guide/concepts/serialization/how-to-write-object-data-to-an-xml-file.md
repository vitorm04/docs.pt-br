---
title: Como gravar dados de objeto em um arquivo XML
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: b2181a74c83782cf4737b2a94fc5fb08fee28a10
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345449"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a>Como: gravar dados de objeto em um arquivo XML (Visual Basic)
Este exemplo grava o objeto de uma classe para um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
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
  
## <a name="compiling-the-code"></a>Compilando o Código  
 A classe deve ter um construtor público sem parâmetros.  
  
## <a name="robust-programming"></a>Programação Robusta  
 As seguintes condições podem causar uma exceção:  
  
- A classe que está sendo serializada não tem um construtor público sem parâmetros.  
  
- O arquivo existe e é somente leitura (<xref:System.IO.IOException>).  
  
- O caminho é muito longo (<xref:System.IO.PathTooLongException>).  
  
- O disco está cheio (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Este exemplo cria um novo arquivo, se o arquivo ainda não existe. Se um aplicativo precisar criar um arquivo, ele precisará de acesso `Create` para a pasta. Se o arquivo já existe, o aplicativo precisa apenas de acesso `Write`, um privilégio menor. Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso `Read` a um único arquivo, em vez de acesso `Create` a uma pasta.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IO.StreamWriter>
- [Como ler dados de objeto de um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Serialização (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
