---
title: Como transmitir fragmentos XML de um XmlReader (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 06e2cf4b350fecf8e8310519c573ac140f05267a
ms.contentlocale: pt-br
ms.lasthandoff: 03/24/2017

---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Como transmitir fragmentos XML de um XmlReader (C#)
Quando você tem que processa grandes arquivos XML, talvez não seja possível carregar a árvore inteira XML na memória. Este tópico mostra como transmitir fragmentos usando um <xref:System.Xml.XmlReader>.  
  
 Uma das maneiras mais eficazes de se usar um <xref:System.Xml.XmlReader> para ler objetos <xref:System.Xml.Linq.XElement> é escrever seu próprio método personalizado de eixo. Um método de eixo normalmente retorna uma coleção, como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, conforme mostrado no exemplo neste tópico. No método de eixo personalizado, depois de criar o fragmento XML chamando o método <xref:System.Xml.Linq.XNode.ReadFrom%2A>, retorne a coleção, usando `yield return`. Isso fornece a semântica de execução adiada ao método personalizado do eixo.  
  
 Quando você cria uma árvore XML de um objeto <xref:System.Xml.XmlReader>, o <xref:System.Xml.XmlReader> deve ser posicionado em um elemento. O método <xref:System.Xml.Linq.XNode.ReadFrom%2A> não retorna até que a marca do elemento seja lida por ele.  
  
 Se quiser criar uma árvore parcial, você pode instanciar um <xref:System.Xml.XmlReader>, posicionar o leitor no nó que você deseja converter em uma árvore de <xref:System.Xml.Linq.XElement> e, em seguida, criar o objeto <xref:System.Xml.Linq.XElement>.  
  
 O tópico [Como transmitir fragmentos XML com acesso a informações de cabeçalho (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) contém informações e um exemplo de como transmitir um documento mais complexo.  
  
 O tópico [Como executar a transformação de streaming de grandes documentos XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) contém um exemplo do uso de LINQ to XML para transformar documentos XML muito grandes, mantendo uma pegada de memória pequena.  
  
## <a name="example"></a>Exemplo  
 Este exemplo cria um método personalizado do eixo. Você pode consultá-lo usando uma consulta [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]. O método de eixo personalizado `StreamRootChildDoc` é um método que foi projetado especificamente para ler um documento que tenha um elemento `Child` de repetição.  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
bbb  
ccc  
```  
  
 Nesse exemplo, o documento de origem é muito pequeno. No entanto, mesmo se houver milhões de elementos de `Child` , este exemplo ainda terá uma pegada pequena de memória.  
  
## <a name="see-also"></a>Consulte também  
 [Analisando XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
