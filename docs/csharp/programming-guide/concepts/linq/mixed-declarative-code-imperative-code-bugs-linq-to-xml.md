---
title: "Misto Bugs de c&#243;digo imperativo c&#243;digo declarativo (LINQ to XML) (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Declarativo misturado c&#243;digo/c&#243;digo obrigat&#243;rias (LINQ to XML) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] contém vários métodos que permitem que você modifique uma árvore XML diretamente. Você pode adicionar elementos, excluir elementos, alterar o conteúdo de um elemento, adicionar atributos e assim por diante. Essa interface de programação é descrito em [Modifying XML Trees \(LINQ to XML\) \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md). Se você estiver Iterando através de um dos eixos, como <xref:System.Xml.Linq.XContainer.Elements%2A>, e você está modificando a árvore XML como você itera através do eixo, você pode acabar com alguns erros estranhas.  
  
 Às vezes, esse problema é conhecido como "O problema de dia das Bruxas".  
  
## Definição do problema  
 Quando você escreve algum código usando LINQ que itera em uma coleção, você está escrevendo o código em um estilo declarativo. É mais aparentado a descrever *que* desejar, em vez disso, que *como* você deseja realizar. Se você escrever código que 1\) obtém o primeiro elemento, 2\) testes para alguma condição, 3\) altera\- e 4\) coloca novamente no lista, e em seguida, esse código seria obrigatório. Você está solicitando que o computador *como* fazer o que você deseja feito.  
  
 Misturar esses estilos de código na mesma operação é o que leva a problemas. Considere o seguinte:  
  
 Suponha que você tenha uma lista vinculada com três itens nele \(a, b e c\):  
  
 `a -> b -> c`  
  
 Agora, suponha que você deseja mover através da lista vinculada, adicionando novos três itens \(um ', b' e c'\). Você deseja a lista vinculada resultante para ter esta aparência:  
  
 `a -> a' -> b -> b' -> c -> c'`  
  
 Então você escreve código que interage através da lista e para cada item, adiciona um novo item mesmo após ele. O que acontece é que seu código verá primeiro o `a` elemento e inserção `a'` depois dela. Agora, seu código será movido para o próximo nó na lista, que agora é `a'`\! Felizmente adicionar um novo item à lista, `a''`.  
  
 Como você resolveria isso no mundo real? Bem, você pode fazer uma cópia da lista vinculada original e criar uma lista completamente nova. Ou se você estiver escrevendo código puramente obrigatório, você pode encontrar o primeiro item, adicione o novo item e, em seguida, avança duas vezes na lista vinculada, adiantando sobre o elemento que você acabou de adicionar.  
  
## Adicionar a iterar  
 Por exemplo, suponha que você queira escrever um código que, para cada elemento em uma árvore, você deseja criar um elemento duplicado:  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    root.Add(new XElement(e.Name, (string)e));  
```  
  
 Esse código entra em um loop infinito. O `foreach` instrução percorre o `Elements()` eixo, adicionando novos elementos para o `doc` elemento. Ele acaba também iterar através dos elementos que acabou de adicionar. E como atribuir novos objetos com cada iteração do loop, consumirá se toda a memória disponível.  
  
 Você pode corrigir este problema recebendo a coleção na memória usando o <xref:System.Linq.Enumerable.ToList%2A> operador de consulta padrão, da seguinte maneira:  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    root.Add(new XElement(e.Name, (string)e));  
Console.WriteLine(root);  
```  
  
 Agora o código funciona. A árvore XML resultante é o seguinte:  
  
```xml  
<Root>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
  <A>1</A>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
## Excluir para iterar  
 Se você deseja excluir todos os nós em um determinado nível, você pode ficar tentado a escrever código como o seguinte:  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 No entanto, isso não faz o que você deseja. Nessa situação, depois de ter removido o primeiro elemento, A, ele é removido da árvore XML contida na raiz e o código no método dos elementos que está fazendo a iteração não é possível localizar o próximo elemento.  
  
 O código anterior produz a seguinte saída:  
  
```xml  
<Root>  
  <B>2</B>  
  <C>3</C>  
</Root>  
```  
  
 A solução é novamente chamar <xref:System.Linq.Enumerable.ToList%2A> para materializar a coleção, da seguinte maneira:  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
foreach (XElement e in root.Elements().ToList())  
    e.Remove();  
Console.WriteLine(root);  
```  
  
 Isso gera a seguinte saída:  
  
```xml  
<Root />  
```  
  
 Como alternativa, você pode eliminar a iteração completamente chamando <xref:System.Xml.Linq.XElement.RemoveAll%2A> no elemento pai:  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
root.RemoveAll();  
Console.WriteLine(root);  
```  
  
## Por que não pode automaticamente LINQ manipular esse?  
 Uma abordagem seria sempre trazer tudo na memória em vez de fazer a avaliação lenta. No entanto, seria muito cara em termos de desempenho e uso de memória. Na verdade, se LINQ e \(LINQ to XML\) usar essa abordagem, falharia em situações do mundo real.  
  
 Outra abordagem seria colocado em algum tipo de sintaxe de transação em LINQ e o compilador tentar analisar o código e determine se qualquer coleção específica precisa ser materializada. No entanto, tentar determinar qualquer código que tem efeitos colaterais é incrivelmente complexo. Considere o seguinte código:  
  
```c#  
var z =  
    from e in root.Elements()  
    where TestSomeCondition(e)  
    select DoMyProjection(e);  
```  
  
 Esse código de análise precisaria analisar métodos TestSomeCondition e DoMyProjection e todos os métodos que esses métodos são chamados, para determinar se qualquer código tinha efeitos colaterais. Mas o código de análise não pode simplesmente procurar por qualquer código que tem efeitos colaterais. Ele pode precisar selecionar apenas o código que tinha efeitos colaterais em elementos filho de `root` nessa situação.  
  
 O LINQ to XML não tenta fazer uma análise.  
  
 Cabe a você para evitar esses problemas.  
  
## Diretrizes  
 Primeiro, não misture código declarativo e obrigatório.  
  
 Mesmo que você saiba exatamente a semântica das coleções e semântica dos métodos que modificam a árvore XML, se você escreve qualquer código inteligente que evita essas categorias de problemas, seu código precisará ser mantida no futuro por outros desenvolvedores e podem não ser como espaço livre nos problemas. Se você combinar declarativas e imperativas estilos de codificação, seu código será mais frágil.  
  
 Se você escrever código que materializa uma coleção para que esses problemas são impedidos, observá\-la com comentários apropriadas em seu código, para que os desenvolvedores de aplicativos compreendam o problema.  
  
 Em segundo lugar, se permitirem o desempenho e outras considerações, use somente o código declarativo. Não modifique sua árvore XML existente. Gere um novo.  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("A", "1"),  
    new XElement("B", "2"),  
    new XElement("C", "3")  
);  
XElement newRoot = new XElement("Root",  
    root.Elements(),  
    root.Elements()  
);  
Console.WriteLine(newRoot);  
```  
  
## Consulte também  
 [Advanced LINQ to XML Programming \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)