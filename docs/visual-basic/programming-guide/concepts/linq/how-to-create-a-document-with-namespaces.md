---
title: 'Como: criar um documento com Namespaces (LINQ to XML) (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 761967351cfc6292eb60a5941e213bfd90036f65
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-document-with-namespaces-linq-to-xml-visual-basic"></a>Como: Crie um documento com namespaces (LINQ to XML) (Visual Basic)
Este tópico mostra como criar um documento com namespaces no Visual Basic.  
  
 Ao usar literais XML no Visual Basic, os usuários podem definir um namespace XML global padrão. Este namespace é o namespace padrão para literais XML e propriedades XML. O namespace XML padrão pode ser definida no nível de projeto ou nível de arquivo. Se for definida em nível de arquivo, substitui o namespace padrão no nível do projeto.  
  
 Você também pode definir namespaces, e especifica os prefixos de namespace para esses namespaces.  
  
 Você define dois namespaces padrão e namespaces com um prefixo usando a palavra-chave `Imports` .  
  
 Para obter mais informações, consulte [Introdução a literais XML no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-xml-literals.md).  
  
 Observe que o namespace XML padrão se aplica somente aos elementos e não a atributos. Atributos são sempre por padrão em qualquer namespace. No entanto, você pode usar um prefixo de namespace para colocar um atributo em um namespace.  
  
## <a name="example"></a>Exemplo  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child aw:Att="attvalue" />  
</aw:Root>  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo cria um documento que contém dois namespaces, uma que é o namespace padrão.  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">  
  <Child Att="attvalue" />  
  <fc:Child2>child2 content</fc:Child2>  
</Root>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria um documento que contém vários namespaces, tanto com prefixos de namespace.  
  
 Quando serializar uma árvore XML, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] emite-se declarações namespace como necessário para que cada elemento está no namespace designada.  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
