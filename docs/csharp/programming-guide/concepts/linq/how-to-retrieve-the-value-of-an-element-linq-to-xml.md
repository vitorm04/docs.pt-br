---
title: Como recuperar o valor de um elemento (LINQ para XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: c4bb78e937fe0de08242923cdd7cd638abf571c7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805826"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a>Como recuperar o valor de um elemento (LINQ para XML) (C#)

Este artigo mostra como obter o valor dos elementos. Existem duas maneiras principais de obter o valor:

- Lance <xref:System.Xml.Linq.XElement> um <xref:System.Xml.Linq.XAttribute> ou um para o tipo desejado. O operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado e o atribui à sua variável.

- Use <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> as <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> propriedades ou. Você também pode definir o valor usando essas propriedades.

Com C#, o casting é geralmente a melhor abordagem. Se você lançar o elemento ou atributo a um tipo de valor anulado, o código é mais simples de escrever ao recuperar o valor de um elemento (ou atributo) que pode ou não existir. O [último exemplo](#element-might-not-exist-example) deste artigo demonstra que o casting é mais simples no caso em que o elemento pode não existir. No entanto, você não pode definir o conteúdo de um elemento por meio de conversão, como faria usando a propriedade <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.  
  
## <a name="string-cast-example"></a>Exemplo de elenco de cordas  
 Para recuperar o valor de <xref:System.Xml.Linq.XElement> um elemento, lance o objeto para o tipo desejado. Você pode lançar um elemento para uma seqüência, da seguinte forma:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 Esse exemplo gera a saída a seguir:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="integer-cast-example"></a>Exemplo de elenco inteiro  
 Você também pode converter elementos em tipos que não sejam cadeias de caracteres. Por exemplo, se você tiver um elemento que contenha um número inteiro, poderá convertê-lo em `int`, como mostrado no código a seguir:  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 Esse exemplo gera a saída a seguir:  
  
```output  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornece operadores de conversão explícita para os seguintes tipos de dados: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` e `GUID?`.  
  
 O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] fornece os mesmos operadores de conversão para objetos <xref:System.Xml.Linq.XAttribute>.  
  
## <a name="value-property-example"></a>Exemplo de propriedade de valor  
 É possível usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A> para recuperar o conteúdo de um elemento:  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 Esse exemplo gera a saída a seguir:  
  
```output  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="element-might-not-exist-example"></a>Elemento pode não existir exemplo
 Às vezes você tenta recuperar o valor de um elemento, mesmo que você não tenha certeza se ele existe. Neste caso, quando você atribui o elemento lançado a um tipo de referência nulo ou tipo de valor `null`anulado, se o elemento não existir, a variável atribuída será definida como . O código a seguir mostra que quando o elemento pode ou não existir, é mais fácil de usar a conversão do que usar a propriedade <xref:System.Xml.Linq.XElement.Value%2A>.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 Esse código gera a seguinte saída:  
  
```output  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 Em geral, você pode criar um código mais simples ao usar a conversão para recuperar o conteúdo de elementos e atributos.  
  
## <a name="see-also"></a>Confira também

- [Eixos do LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
