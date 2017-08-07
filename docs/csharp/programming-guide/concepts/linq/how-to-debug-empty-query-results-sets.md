---
title: Como depurar conjuntos de resultados de consultas vazios (C#)
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
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 78c6d612e11f50bedf8f1c2e9826775494faa465
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Como depurar conjuntos de resultados de consultas vazios (C#)
Um dos problemas mais comuns para o consulte árvores XML é que se a árvore tem um namespace XML padrão, o desenvolvedor escreve às vezes a consulta como se o XML não estar em um namespace.  
  
 Definir primeiro exemplos neste tópico mostra uma maneira comum que XML em um namespace padrão é carregado, e deduzido de modo inadequado.  
  
 O segundo conjunto de exemplos a seguir mostra as correções necessárias para que você possa ver XML em um namespace.  
  
 Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar XML em um namespace, e uma consulta que retorna um conjunto de resultados vazia.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Este exemplo gerencia o resultado seguinte:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como criar XML em um namespace, e uma consulta que é codificado corretamente.  
  
 A solução é declarar e inicializar um objeto de <xref:System.Xml.Linq.XNamespace> e usá-lo para especificar <xref:System.Xml.Linq.XName> objetos. Nesse caso, o argumento para o método de <xref:System.Xml.Linq.XElement.Elements%2A> é um objeto de <xref:System.Xml.Linq.XName> .  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Este exemplo gerencia o resultado seguinte:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a>Consulte também  
 [Consultas básicas (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)

