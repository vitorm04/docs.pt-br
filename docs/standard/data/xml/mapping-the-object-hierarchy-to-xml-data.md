---
title: Mapeando a hierarquia do objeto para dados XML
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
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1bf43922fb702988e9057f541833cd58d33c820a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a>Mapeando a hierarquia do objeto para dados XML
Quando um documento XML está na memória, a representação conceitual é uma árvore. Para programar, você tem uma hierarquia de objeto para acessar os nós da árvore. O exemplo a seguir mostra como o conteúdo XML torna-se nós.  
  
 Como o XML é lido no DOM (Document Object Model) XML, as partes são traduzidas em nós e esses nós mantêm metadados adicionais sobre si mesmos, como seu tipo de nó e valores. O tipo de nó é seu objeto e é o que determina quais ações podem ser executadas e quais propriedades podem ser definidas ou recuperadas.  
  
 Se você tiver o XML simples a seguir:  
  
 **Entrada**  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 A entrada é representada na memória como a árvore de nó a seguir com a propriedade de tipo de nó atribuída:  
  
 ![árvore de nós de exemplo](../../../../docs/standard/data/xml/media/simple-xml.gif "Simple_XML")  
Representação da árvore do nó do livro e do título  
  
 O `book` elemento se torna um **XmlElement** objeto, o próximo elemento, `title`, também se torna um **XmlElement**, enquanto o conteúdo do elemento se torna um **XmlText** objeto. Olhando o **XmlElement** métodos e propriedades, métodos e propriedades são diferentes de métodos e propriedades disponíveis em um **XmlText** objeto. Portanto, saber qual tipo de nó a marcação XML se torna é vital, porque o tipo de nó determina as ações que podem ser executadas.  
  
 O exemplo a seguir lê dados XML e remove o texto diferente, dependendo do tipo de nó. Usando o seguinte arquivo de dados XML como entrada, **items.xml**:  
  
 **Entrada**  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 Leituras de exemplo de código a seguir a **items.xml** de arquivos e exibe informações de cada tipo de nó.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and   
            'ignore all white space nodes.   
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore   
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 A saída do exemplo revela o mapeamento dos dados para os tipos de nó.  
  
 **Saída**  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>  
```  
  
 Utilizando a entrada uma linha de cada vez e usando a saída gerada do código, você poderá usar a tabela a seguir para analisar qual teste do nó gerou as linhas de saída, entendendo, portanto, quais dados XML se transformaram em qual tipo de nó.  
  
|Entrada|Saída|Teste de tipo de nó|  
|-----------|------------|--------------------|  
|\<? versão xml = "1.0"? >|\<? versão xml ='1.0 '? >|XmlNodeType.XmlDeclaration|  
|\<! – Este é um exemplo de documento XML-->|\<! – Este é um exemplo de documento XML-->|XmlNodeType.Comment|  
|\<! Itens DOCTYPE [\<! Número de entidade "123" >] >|\<! Itens DOCTYPE [\<! Número de entidade "123" >]|XmlNodeType.DocumentType|  
|\<Itens >|\<Itens >|XmlNodeType.Element|  
|\<Item>|\<Item>|XmlNodeType.Element|  
|Teste com uma entidade:&number;|Teste com uma entidade: 123|XmlNodeType.Text|  
|\</ Item >|\</ Item >|XmlNodeType.EndElement|  
|\<Item>|\<Item>|XmNodeType.Element|  
|teste com um elemento filho|teste com um elemento filho|XmlNodeType.Text|  
|\<mais >|\<mais >|XmlNodeType.Element|  
|material|material|XmlNodeType.Text|  
|\</ Item >|\</ Item >|XmlNodeType.EndElement|  
|\<Item>|\<Item>|XmlNodeType.Element|  
|teste com uma seção CDATA|teste com uma seção CDATA|XmlTest.Text|  
|<! [CDATA [\<456 >]]\>|<! [CDATA [\<456 >]]\>|XmlTest.CDATA|  
|def|def|XmlNodeType.Text|  
|\</ Item >|\</ Item >|XmlNodeType.EndElement|  
|\<Item>|\<Item>|XmlNodeType.Element|  
|Teste com uma entidade de caractere: &\#65;|Teste com uma entidade de caracteres: A|XmlNodeType.Text|  
|\</ Item >|\</ Item >|XmlNodeType.EndElement|  
|\<!---> 14 caracteres neste elemento.|\<---> 14 caracteres neste elemento.|XmlNodeType.Comment|  
|\<Item>|\<Item>|XmlNodeType.Element|  
|1234567890ABCD|1234567890ABCD|XmlNodeType.Text|  
|\</ Item >|\</ Item >|XmlNodeType.EndElement|  
|\</ Itens >|\</ Itens >|XmlNodeType.EndElement|  
  
 Você deve saber qual tipo de nó é atribuído, porque o tipo de nó controla quais tipos de ações são válidos e qual tipo de propriedades você pode definir e recuperar.  
  
 Criação do nó de espaço em branco é controlada quando os dados forem carregados no DOM, o **PreserveWhitespace** sinalizador. Para obter mais informações, consulte [espaço em branco e o espaço em branco significativo tratamento durante o carregamento de DOM](../../../../docs/standard/data/xml/white-space-and-significant-white-space-handling-when-loading-the-dom.md).  
  
 Para adicionar novos nós no DOM, consulte [inserindo nós em um documento XML](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md). Para remover nós do DOM, consulte [remover nós, conteúdo e os valores de um documento XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md). Para modificar o conteúdo de nós no DOM, consulte [modificando nós, conteúdo e os valores em um documento XML](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md).  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
