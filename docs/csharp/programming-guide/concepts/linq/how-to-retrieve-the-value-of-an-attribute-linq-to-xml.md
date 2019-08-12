---
title: 'Como: Recuperar o valor de um atributo (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: e099c20a519563eba2a060320b36761ebe54e0f1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710066"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Como: Recuperar o valor de um atributo (LINQ to XML) (C#)
Este tópico mostra como obter o valor de atributos. Há duas maneiras principais: Você pode converter um <xref:System.Xml.Linq.XAttribute> no tipo desejado; o operador de conversão explícita converte então o conteúdo do elemento ou do atributo no tipo especificado. Outra opção é usar a propriedade <xref:System.Xml.Linq.XAttribute.Value%2A>. No entanto, a conversão geralmente é a abordagem recomendada. Se você converter o atributo em um tipo anulável, o código será mais simples de criar ao recuperar o valor de um atributo que pode ou não existir. Para obter exemplos dessa técnica, confira [Como: Recuperar o valor de um elemento (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
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
  
```  
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
  
```  
abcde  
```  
  
## <a name="see-also"></a>Consulte também

- [Eixos do LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)
