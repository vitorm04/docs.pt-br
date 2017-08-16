---
title: 'Como: ler dados de objeto de um arquivo XML (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c448d79a88517925712f79ed061aa90933e3f6d1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Como: ler dados de objeto de um arquivo XML (Visual Basic)
Este exemplo lê objeto dados que foram previamente gravados em um arquivo XML usando a <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer>  
  
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
 Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" com o nome do arquivo que contém os dados serializados. Para obter mais informações sobre serialização de dados, consulte [como: gravar dados de objeto para um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).  
  
 A classe deve ter um construtor público sem parâmetros.  
  
 Apenas propriedades públicas e campos estão desserializados.  
  
## <a name="robust-programming"></a>Programação robusta  
 As seguintes condições podem causar uma exceção:  
  
-   A classe sendo serializada não tem um construtor público, sem parâmetro.  
  
-   Os dados no arquivo não representam dados da classe a ser desserializado.  
  
-   O arquivo não existe (<xref:System.IO.IOException>).</xref:System.IO.IOException>  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Sempre verifique se as entradas e nunca desserializar dados de uma fonte não confiável. O objeto recriado é executado em um computador local com as permissões do código que desserializado-lo. Verifique todas as entradas antes de usar os dados no seu aplicativo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IO.StreamWriter></xref:System.IO.StreamWriter>   
 [Como: gravar dados de objeto para um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)   
 [Serialização (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md)
