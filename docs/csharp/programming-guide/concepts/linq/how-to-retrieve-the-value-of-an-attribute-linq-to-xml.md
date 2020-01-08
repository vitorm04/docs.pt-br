---
title: Como recuperar o valor de um atributo (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347430"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Como recuperar o valor de um atributo (LINQ to XML) (C#)
Este tópico mostra como obter o valor de atributos. Existem duas maneiras principais: converter <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte o conteúdo do elemento ou do atributo no tipo especificado. Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>. No entanto, a conversão geralmente é a abordagem recomendada. Se você converter o atributo em um tipo anulável, o código será mais simples de criar ao recuperar o valor de um atributo que pode ou não existir. Para obter exemplos dessa técnica, consulte [como recuperar o valor de um elemento (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Exemplo  
 Para recuperar o valor de um atributo, basta converter o objeto <xref:System.Xml.Linq.XAttribute> no tipo desejado.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como recuperar o valor de um atributo em que o atributo está em um namespace. Para obter mais informações, consulte [Visão geral de namespaces (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```output  
abcde  
```  
  
## <a name="see-also"></a>Veja também

- [Eixos do LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
