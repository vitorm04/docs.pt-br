---
title: "Comparação XPath e de LINQ to XML1 | Documentos do Microsoft"
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
ms.assetid: c3fd07c1-6761-4e4b-8eb1-ddd780ed8d44
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e9601c51468fdf5adab8e521f8f89ee7f2e12869
ms.lasthandoff: 03/13/2017


---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Comparação XPath e de LINQ to XML
O XPath e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fornecer alguma funcionalidade semelhante. Ambos podem ser usados para ver uma árvore XML, retornando resultados como uma coleção de elementos, uma coleção de atributos, uma coleção de nós, ou o valor de um elemento ou de um atributo. No entanto, também há algumas diferenças.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Diferenças entre o XPath e o LINQ to XML  
 O XPath não permite a projeção de novos tipos. Só pode retornar coleções de nós de árvore, enquanto [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] pode executar uma consulta e projetar um objeto gráfico ou uma árvore XML em uma nova forma. consultas de[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] abrangem muito mais funcionalidade e são muito mais avançados de expressões XPath.  
  
 As expressões XPath existem no isolamento dentro de uma cadeia de caracteres. O compilador do Visual Basic não pode ajudar a analisar a expressão XPath em tempo de compilação. Por outro lado, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] consultas são analisadas e compiladas pelo Visual Basic compiler. O compilador pode capturar muitos erros de consulta.  
  
 Os resultados XPath não são altamente digitados. Em um número das circunstâncias, o resultado para avaliar uma expressão XPath é um objeto, e até o desenvolvedor para determinar o tipo apropriado e conforme necessário para converter o resultado. Por outro lado, as projeções de uma consulta de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] são fortemente tipadas.  
  
## <a name="result-ordering"></a>Ordenação de resultado  
 O XPath 1,0 estados de recomendação que uma coleção que é o resultado de avaliar uma expressão XPath é não ordenada.  
  
 Entretanto, ao fazer iterações por uma coleção retornada por um método do eixo XPath [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] , os nós na coleção são retornados em ordem do documento. Este é o caso mesmo quando acessando os eixos XPath onde os predicados são expressos em termos de ordem inversa de documento, como `preceding` e `preceding-sibling`.  
  
 Por outro lado, a maioria do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] eixos retornam coleções na ordem do documento, mas dois deles, <xref:System.Xml.Linq.XNode.Ancestors%2A>e <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, retornam coleções na ordem inversa do documento.</xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> </xref:System.Xml.Linq.XNode.Ancestors%2A> A tabela a seguir enumera os eixos, e indica a ordem de coleção para cada:  
  
|O eixo LINQ to XML|Ordenando|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Ordem de documento|  
|XContainer.Descendants|Ordem de documento|  
|XContainer.Elements|Ordem de documento|  
|XContainer.Nodes|Ordem de documento|  
|XContainer.NodesAfterSelf|Ordem de documento|  
|XContainer.NodesBeforeSelf|Ordem de documento|  
|XElement.AncestorsAndSelf|Ordem inversa de documento|  
|XElement.Attributes|Ordem de documento|  
|XElement.DescendantNodesAndSelf|Ordem de documento|  
|XElement.DescendantsAndSelf|Ordem de documento|  
|XNode.Ancestors|Ordem inversa de documento|  
|XNode.ElementsAfterSelf|Ordem de documento|  
|XNode.ElementsBeforeSelf|Ordem de documento|  
|XNode.NodesAfterSelf|Ordem de documento|  
|XNode.NodesBeforeSelf|Ordem de documento|  
  
## <a name="positional-predicates"></a>Predicados posicionais  
 Em uma expressão XPath, os predicados posicionais são expressos em termos de pedido de documento para muitos eixos, mas expressos na ordem inversa de documento para os eixos invertidos, que são `preceding`, `preceding-sibling`, `ancestor`, e `ancestor-or-self`. Por exemplo, a expressão XPath `preceding-sibling::*[1]` retorna imediatamente antes o irmão. Este é o caso mesmo que o conjunto de resultados final é apresentado na ordem de documento.  
  
 Por outro lado, todos os predicados posicionais em LINQ to XML sempre são expressos em termos de pedido do eixo. Por exemplo, `anElement.ElementsBeforeSelf().ToList()[0]` retorna o primeiro elemento filho do pai do elemento consultado, não irmão anterior imediato. Outro exemplo: `anElement.Ancestors().ToList()[0]` retorna o elemento pai.  
  
 Observe que a abordagem anterior materializa toda a coleção. Isso não é a maneira mais eficiente de escrever a consulta. Escreveu-se nessa maneira para demonstrar o comportamento de predicados posicionais. Uma maneira mais apropriada para escrever a mesma consulta é usar o <xref:System.Linq.Enumerable.First%2A>método, da seguinte maneira: `anElement.ElementsBeforeSelf().First()`.</xref:System.Linq.Enumerable.First%2A>  
  
 Se você desejar localizar imediatamente antes o elemento em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], escreva a expressão a seguir:  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>Diferenças de desempenho  
 Consultas XPath que usam funcionalidade XPath em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] não executará, bem como [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] consultas.  
  
## <a name="comparison-of-composition"></a>Comparação de composição  
 A composição de uma consulta de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é um pouco paralela a composição de uma expressão XPath, embora muito diferente na sintaxe.  
  
 Por exemplo, se você tiver um elemento em uma variável chamada `customers`, e você desejar localizar um elemento de neto chamado `CompanyName` em todos os elementos filho chamados `Customer`, escreva uma expressão XPath como segue:  
  
```vb  
customers.XPathSelectElements("./Customer/CompanyName")  
```  
  
 A consulta de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] do equivalente realiza-se:  
  
```vb  
customers.Element("Customer").Elements("CompanyName")  
```  
  
 Há paralelas semelhantes para cada um dos eixos XPath.  
  
|O eixo XPath|O eixo LINQ to XML|  
|----------------|----------------------|  
|o eixo filho (padrão)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName>|  
|Pai (.).|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=fullName></xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=fullName>|  
|o eixo de atributo (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=fullName>|  
|o eixo de ancestral|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=fullName>|  
|o eixo de antepassado-ou- auto|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=fullName>|  
|o eixo descendente (/)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=fullName>|  
|descendente-ou-auto|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=fullName><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=fullName>|  
|seguir-irmão|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=fullName><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=fullName>|  
|acima-irmão|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=fullName><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=fullName>|  
|após|Nenhum equivalente direto.|  
|precedência|Nenhum equivalente direto.|  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to XML para XPath usuários (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
