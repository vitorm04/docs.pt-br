---
title: Comparação XPath e de LINQ to XML1
ms.date: 07/20/2015
ms.assetid: c3fd07c1-6761-4e4b-8eb1-ddd780ed8d44
ms.openlocfilehash: fe6b0b77f82a9fcb5475e31e096a636211faa578
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644141"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Comparação XPath e de LINQ to XML
O XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornecer alguma funcionalidade semelhante. Ambos podem ser usados para ver uma árvore XML, retornando resultados como uma coleção de elementos, uma coleção de atributos, uma coleção de nós, ou o valor de um elemento ou de um atributo. No entanto, também há algumas diferenças.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Diferenças entre o XPath e o LINQ to XML  
 O XPath não permite a projeção de novos tipos. Só pode retornar coleções de nós de árvore, enquanto [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pode executar uma consulta e projetar um grafo de objeto ou uma árvore XML em uma nova forma. consultas de[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] abrangem muito mais funcionalidade e são muito mais avançados de expressões XPath.  
  
 As expressões XPath existem no isolamento dentro de uma cadeia de caracteres. O compilador do Visual Basic não pode ajudar a analisar a expressão XPath em tempo de compilação. Por outro lado, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] consultas são analisadas e compiladas pelo compilador de Visual Basic. O compilador pode capturar muitos erros de consulta.  
  
 Os resultados XPath não são altamente digitados. Em um número das circunstâncias, o resultado para avaliar uma expressão XPath é um objeto, e até o desenvolvedor para determinar o tipo apropriado e conforme necessário para converter o resultado. Por outro lado, as projeções de uma consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] são fortemente tipadas.  
  
## <a name="result-ordering"></a>Ordenação de resultado  
 O XPath 1,0 estados de recomendação que uma coleção que é o resultado de avaliar uma expressão XPath é não ordenada.  
  
 Entretanto, ao fazer iterações por uma coleção retornada por um método do eixo XPath [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , os nós na coleção são retornados em ordem do documento. Este é o caso mesmo quando acessando os eixos XPath onde os predicados são expressos em termos de ordem inversa de documento, como `preceding` e `preceding-sibling`.  
  
 Por outro lado, a maioria das coleções de retorno os eixos [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] na ordem de documento, mas por dois deless, por <xref:System.Xml.Linq.XNode.Ancestors%2A> e por <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, coleções de retorno na ordem inversa do documento. A tabela a seguir enumera os eixos, e indica a ordem de coleção para cada:  
  
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
  
 Observe que a abordagem anterior materializa toda a coleção. Isso não é a maneira mais eficiente de escrever a consulta. Escreveu-se nessa maneira para demonstrar o comportamento de predicados posicionais. Uma maneira mais apropriado de escrever a mesma consulta é usar o método de <xref:System.Linq.Enumerable.First%2A> , como segue: `anElement.ElementsBeforeSelf().First()`.  
  
 Se você desejar localizar imediatamente antes o elemento em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], escreva a expressão a seguir:  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>Diferenças de desempenho  
 As consultas XPath que usam a funcionalidade XPath em [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] não serão tão bem executadas como as consultas de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="comparison-of-composition"></a>Comparação de composição  
 A composição de uma consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é um pouco paralela a composição de uma expressão XPath, embora muito diferente na sintaxe.  
  
 Por exemplo, se você tiver um elemento em uma variável chamada `customers`, e você desejar localizar um elemento de neto chamado `CompanyName` em todos os elementos filho chamados `Customer`, escreva uma expressão XPath como segue:  
  
```vb  
customers.XPathSelectElements("./Customer/CompanyName")  
```  
  
 A consulta de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] do equivalente realiza-se:  
  
```vb  
customers.Element("Customer").Elements("CompanyName")  
```  
  
 Há paralelas semelhantes para cada um dos eixos XPath.  
  
|O eixo XPath|O eixo LINQ to XML|  
|----------------|----------------------|  
|o eixo filho (padrão)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Pai (.).|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|o eixo de atributo (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|o eixo de ancestral|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|o eixo de antepassado-ou- auto|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|o eixo descendente (/)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendente-ou-auto|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|seguir-irmão|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|acima-irmão|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|após|Nenhum equivalente direto.|  
|precedência|Nenhum equivalente direto.|  
  
## <a name="see-also"></a>Consulte também  
 [LINQ to XML para XPath usuários (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
