---
title: "Como: transmitir fragmentos XML com acesso a informa&#231;&#245;es de cabe&#231;alho (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: transmitir fragmentos XML com acesso a informa&#231;&#245;es de cabe&#231;alho (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Às vezes você precisa ler arbitrariamente grandes arquivos XML e escrever seu aplicativo para que a superfície de memória do aplicativo é previsível. Se você tentar preencher uma árvore XML com um arquivo XML grande, seu uso de memória será proporcional ao tamanho do arquivo — isto é, excessivo. Portanto, você deve usar uma técnica de streaming.  
  
 Uma opção é escrever seu aplicativo usando <xref:System.Xml.XmlReader>. No entanto, você talvez queira usar [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] para consultar a árvore XML. Se esse for o caso, você pode escrever seu próprio método personalizado do eixo. Para obter mais informações, consulte [How to: Write a LINQ to XML Axis Method \(C\#\)](../Topic/How%20to:%20Write%20a%20LINQ%20to%20XML%20Axis%20Method%20\(C%23\).md).  
  
 Para escrever seu próprio método de eixo, você escreve um método pequeno que usa o <xref:System.Xml.XmlReader> para ler nós até atingir um de nós no qual você está interessado. Em seguida, chama o método <xref:System.Xml.Linq.XNode.ReadFrom%2A>, que lê a partir do <xref:System.Xml.XmlReader> e instancia um fragmento XML. Resulta em cada fragmento por meio de `yield return` para o método que está enumerando o método personalizado do eixo. Em seguida, você pode escrever consultas LINQ no método personalizado do eixo.  
  
 As técnicas de streaming são melhor aplicadas em situações em que você precisa processar o documento de origem apenas uma vez, e você pode processar os elementos na ordem do documento. Determinados operadores de consulta padrão, como <xref:System.Linq.Enumerable.OrderBy%2A>, iteram sua origem, coletar todos os dados, classificá\-los e, em seguida, geram finalmente o primeiro item na sequência. Observe que se você usar um operador de consulta que materializa sua origem antes de gerar o primeiro item, você não manterá uma pegada pequena de memória.  
  
## Exemplo  
 Às vezes, o problema fica um pouco mais interessante. No seguinte documento XML, o consumidor do método personalizado do eixo também precisa saber o nome do cliente que cada item pertence.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 A abordagem que este exemplo usa é Inspecione também para essas informações de cabeçalho, salvar as informações de cabeçalho e, em seguida, criar uma árvore XML pequena que contém as informações de cabeçalho e os detalhes que você está enumerando. O método do eixo resulta nessa árvore XML pequeno. A consulta, em seguida, tem acesso a informações de cabeçalho, bem como as informações detalhadas.  
  
 Essa abordagem tem uma pegada pequena de memória. Como cada fragmento XML de detalhe é rendido, nenhuma referência é mantido para o fragmento anterior, e está disponível para coleta de lixo. Observe que essa técnica cria uma breve muitos objetos no heap.  
  
 O exemplo a seguir mostra como implementar e usar um método personalizado do eixo que passa fragmentos XML do arquivo especificado pelo URI. Esse eixo personalizado é escrito especificamente para que ele espera um documento que tem `Customer`, `Name`, e `Item` elementos, e que esses elementos serão organizados como acima `Source.xml` documento. É uma implementação simples. Uma implementação mais robusta seria preparada para analisar um documento inválido.  
  
```c#  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 Esse código produz a seguinte saída:  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
  
## Consulte também  
 [Advanced LINQ to XML Programming \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)