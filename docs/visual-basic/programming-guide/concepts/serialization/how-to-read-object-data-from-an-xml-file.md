---
title: 'Como: ler dados de objeto de um arquivo XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: fa8623abeebfa413677b4b68d6ab6b7a0547ccd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646052"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Como: ler dados de objeto de um arquivo XML (Visual Basic)
Este exemplo lê dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Exemplo  
  
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
  
## <a name="compiling-the-code"></a>Compilando o código  
 Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" pelo nome do arquivo que contém os dados serializados. Para obter mais informações sobre a serialização de dados, consulte [como: gravar dados de objeto para um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 A classe deve ter um construtor público sem parâmetros.  
  
 Somente propriedades e campos públicos são desserializados.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   A classe que está sendo serializada não tem um construtor público sem parâmetros.  
  
-   Os dados no arquivo não representam dados da classe a ser desserializada.  
  
-   O arquivo não existe (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre verifique as entradas e nunca desserialize dados de uma fonte não confiável. O objeto recriado é executado em um computador local com as permissões do código que o desserializou. Verifique todas as entradas antes de usar os dados no seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamWriter>  
 [Como gravar dados de objeto em um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [Serialização (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Guia de programação do Visual Basic](../../../../visual-basic/programming-guide/index.md)
