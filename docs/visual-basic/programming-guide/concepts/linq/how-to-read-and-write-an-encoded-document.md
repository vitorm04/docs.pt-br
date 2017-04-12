---
title: 'Como: ler e gravar um documento codificado (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
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
ms.openlocfilehash: 3247af177066e9b50d5028766f99e7bf6589050f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>Como: ler e gravar um documento codificado (Visual Basic)
Para criar um documento XML codificado, adicione um <xref:System.Xml.Linq.XDeclaration>à árvore XML, definindo a codificação para o nome da página de código desejada.</xref:System.Xml.Linq.XDeclaration>  
  
 Qualquer valor retornado por <xref:System.Text.Encoding.WebName%2A>é um valor válido.</xref:System.Text.Encoding.WebName%2A>  
  
 Se você ler um documento codificado, o <xref:System.Xml.Linq.XDeclaration.Encoding%2A>propriedade será definida como o nome da página de código.</xref:System.Xml.Linq.XDeclaration.Encoding%2A>  
  
 Se você definir <xref:System.Xml.Linq.XDeclaration.Encoding%2A>para um nome de página de código válida, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] serializará com a codificação especificada.</xref:System.Xml.Linq.XDeclaration.Encoding%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria dois documentos, um com codificação utf-8 e um com codificação utf-16. Ele em seguida carrega os documentos e imprime a codificação para o console.  
  
```vb  
Console.WriteLine("Creating a document with utf-8 encoding")  
Dim encodedDoc8 As XDocument = _  
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>  
        <Root>Content</Root>   
  
encodedDoc8.Save("EncodedUtf8.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Console.WriteLine("Creating a document with utf-16 encoding")  
Dim encodedDoc16 As XDocument = _  
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>  
        <Root>Content</Root>  
  
encodedDoc16.Save("EncodedUtf16.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=fullName></xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=fullName>   
 [Avançada LINQ to XML programação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
