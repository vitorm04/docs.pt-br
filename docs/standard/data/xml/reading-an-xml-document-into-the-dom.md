---
title: Lendo um documento XML no DOM
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
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b8844705b492574443ff4f37de33ccaf1f5fedd7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="reading-an-xml-document-into-the-dom"></a>Lendo um documento XML no DOM
As informações XML são lidas na memória em diferentes formatos. Podem ser lidas de uma cadeia de caracteres, de um fluxo, de uma URL, de um leitor de texto ou de uma classe derivada de <xref:System.Xml.XmlReader>.  
  
 O método <xref:System.Xml.XmlDocument.Load%2A> leva o documento para a memória e tem métodos sobrecarregados disponíveis para utilizar dados de cada um dos diferentes formatos. Existe também um método <xref:System.Xml.XmlDocument.LoadXml%2A> que lê XML de uma cadeia de caracteres.  
  
 Diferentes métodos de <xref:System.Xml.XmlDocument.Load%2A> afetam os nós que são criados quando o DOM (Document Object Model) é carregado. A tabela a seguir lista as diferenças entre alguns dos métodos de <xref:System.Xml.XmlDocument.Load%2A> e os tópicos que os abordam.  
  
|Assunto|Tópico|  
|-------------|-----------|  
|Criação de nós de espaços em branco|O objeto usado para carregar o DOM tem um efeito no espaço em branco e nos nós de espaço em branco significativos gerados no DOM. Para obter mais informações, consulte [espaço em branco e o espaço em branco significativo tratamento durante o carregamento de DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).|  
|Carregando o XML a partir de um nó específico ou carregando todo o documento XML|Usando o <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> dados de método podem ser carregados de um nó específico no DOM. Para obter mais informações, consulte [carregar dados de um leitor](../../../../docs/standard/data/xml/load-data-from-a-reader.md).|  
|Validando o XML à medida que é carregado|Os dados XML carregados no DOM podem ser validados à medida que são carregados. Isso é feito usando um <xref:System.Xml.XmlReader> de validação. Para obter mais informações sobre como validar XML quando ele é carregado, consulte [Validando um documento XML no DOM](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md).|  
  
 O exemplo a seguir mostra o XML que está sendo carregado com o método <xref:System.Xml.XmlDocument.LoadXml%2A> e os dados salvos subsequentemente em um arquivo de texto chamado `data.xml`.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
