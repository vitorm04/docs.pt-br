---
title: "Como: Crie um documento com namespaces (LINQ to XML) (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: Crie um documento com namespaces (LINQ to XML) (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como criar um documento com namespaces no Visual Basic.  
  
 Ao usar literais XML no Visual Basic, os usuários podem definir um namespace XML global padrão. Este namespace é o namespace padrão para literais XML e propriedades XML. O namespace XML padrão pode ser definido no nível do projeto ou no nível de arquivo. Se ele é definido no nível de arquivo, ele substitui o namespace padrão no nível do projeto.  
  
 Você também pode definir outros namespaces e especificar os prefixos de namespace para esses namespaces.  
  
 Definir namespaces padrão e namespaces com um prefixo usando o `Imports` palavra\-chave.  
  
 Para obter mais informações, consulte [Introdução a literais XML no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Observe que o namespace XML padrão se aplica somente aos elementos e não a atributos. Os atributos são sempre por padrão em nenhum namespace. No entanto, você pode usar um prefixo de namespace para colocar um atributo em um namespace.  
  
## Exemplo  
 Este exemplo cria um documento que contém um namespace.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child aw:Att="attvalue"/>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## Exemplo  
 Este exemplo cria um documento que contém dois namespaces, um dos quais é o namespace padrão.  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child Att="attvalue"/>  
                <fc:Child2>child2 content</fc:Child2>  
            </Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## Exemplo  
 O exemplo a seguir cria um documento que contém vários namespaces, ambos com prefixos de namespace.  
  
 Ao serializar uma árvore XML, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] emite declarações de namespace, conforme necessário, para que cada elemento está no namespace designada.  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)