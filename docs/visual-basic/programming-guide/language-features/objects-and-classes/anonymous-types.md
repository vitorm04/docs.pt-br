---
title: "Tipos an&#244;nimos (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.AnonymousType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipos anônimos [Visual Basic]"
  - "tipos anônimos [Visual Basic], sobre tipos anônimos"
  - "tipos [Visual Basic], anônimos"
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
caps.handback.revision: 46
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos an&#244;nimos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Visual Basic oferece suporte a tipos anônimos, que permitem criar objetos sem escrever uma definição de classe para o tipo de dados.  Em vez disso, o compilador gera uma classe para você.  A classe não possui um nome utilizável, herda diretamente da <xref:System.Object> e contém as propriedades que você especificar no declarar o objeto.  Porque não foi especificado o nome do tipo de dados, ele é conhecido como um  *tipo*  anônimo.  
  
 O exemplo a seguir declara e cria variável `product` como uma instância de um tipo que possui duas propriedades, `Name` anônimo e `Price`.  
  
 [!CODE [VbVbalrAnonymousTypes#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#1)]  
  
 Uma expressão de consulta  Usa tipos anônimos para combinar as colunas de dados selecionados por uma consulta.  Não é possível definir o tipo de resultado com antecedência, porque você não pode prever as uma determinada consulta pode selecionar colunas.  Tipos anônimos permitem que você escrever uma consulta que seleciona qualquer número de colunas, em qualquer ordem.  O compilador cria um tipo de dados que corresponde a ordem especificada e as propriedades especificadas.  
  
 Nos exemplos a seguir, `products` é uma lista de objetos do produto, cada um deles tem várias propriedades.  Variável `namePriceQuery` contém a definição de uma consulta que, quando ele é executado, retorna uma coleção de instâncias de um tipo que possui duas propriedades, `Name` anônimo e `Price`.  
  
 [!CODE [VbVbalrAnonymousTypes#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#2)]  
  
 Variável `nameQuantityQuery` contém a definição de uma consulta que, quando ele é executado, retorna uma coleção de instâncias de um tipo que possui duas propriedades, `Name` anônimo e `OnHand`.  
  
 [!CODE [VbVbalrAnonymousTypes#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#3)]  
  
 Para obter mais informações sobre o código criado pelo compilador para um tipo anônimo, consulte [Definição do tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
> [!CAUTION]
>  O nome do tipo anônimo é compilador gerado e pode variar de compilação a compilação.  Seu código não deve usar ou contar com o nome de um tipo anônimo porque o nome pode mudar quando um projeto é recompilado.  
  
## Declarar um tipo anônimo  
 A declaração de uma instância de um tipo anônimo usa um inicializador lista para especificar as propriedades do tipo.  Você pode especificar propriedades somente quando você declarar um tipo anônimo, não outros elementos de classe como métodos ou eventos.  No exemplo a seguir, `product1` é uma instância de um tipo anônimo que tem duas propriedades: `Name` e `Price`.  
  
 [!CODE [VbVbalrAnonymousTypes#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#4)]  
  
 Se você designar propriedades como propriedades chave, você poderá usá\-los para comparar duas instâncias tipo anônimo de igualdade.  No entanto, os valores das propriedades de chave não podem ser alterados.  Consulte a seção Propriedades de chave posteriormente neste tópico para obter mais informações.  
  
 Observe que declarar uma instância de um tipo anônimo é como declarar uma instância de um tipo nomeado usando um inicializador de objeto:  
  
 [!CODE [VbVbalrAnonymousTypes#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#5)]  
  
 Para obter mais informações sobre outras maneiras para especificar propriedades de tipo anônimo, consulte [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## Propriedades de chave  
 Chave propriedades diferem de não\-chave propriedades de várias maneiras fundamentais:  
  
-   Somente os valores das propriedades de chave são comparados para determinar se duas instâncias são iguais.  
  
-   Os valores das propriedades de chave são somente leitura e não podem ser alterados.  
  
-   Somente valores de propriedade de chave estão incluídos no algoritmo Compiler\-generated código hash para um tipo anônimo.  
  
### Igualdade  
 Instâncias de tipos anônimos podem ser iguais somente se eles forem instâncias do mesmo tipo anônimo.  O compilador trata duas instâncias como instâncias do mesmo tipo se eles atendam às seguintes condições:  
  
-   Eles são declarados no mesmo assembly.  
  
-   As propriedades são declaradas na mesma ordem, com os mesmos nomes e os mesmos inferidos tipos.  Nome comparações não diferenciam maiúsculas de minúsculas.  
  
-   As mesmas propriedades em cada são marcadas como propriedades de chave.  
  
-   Pelo menos uma propriedade em cada declaração é uma propriedade de chave.  
  
 Uma instância de um anônimo tipos que tem propriedades nenhuma chave é igual somente a si mesmo.  
  
 [!CODE [VbVbalrAnonymousTypes#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#6)]  
  
 Duas instâncias do mesmo tipo anônimo são iguais se os valores de suas propriedades de chave forem iguais.  Os exemplos a seguir ilustram como igualdade é testada.  
  
 [!CODE [VbVbalrAnonymousTypes#7](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#7)]  
  
### Valores somente leitura  
 No entanto, os valores das propriedades de chave não podem ser alterados.  Por exemplo, em `prod8` No exemplo anterior, o `Name` `Price` campos e `read-only`,mas `OnHand` pode ser alterado.  
  
 [!CODE [VbVbalrAnonymousTypes#8](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#8)]  
  
## Tipos de expressões de consulta anônimos  
 Expressões de consulta nem sempre não necessário a criação de tipos anônimos.  Quando possível, eles usar um tipo existente para manter os dados da coluna.  Isso ocorre quando a consulta retorna registros qualquer inteiros do fonte de dados, ou apenas um campo de cada registro.  Nos exemplos de código a seguir, `customers` é uma coleção de objetos de uma classe `Customer`.  A classe tem várias propriedades, e você pode incluir uma ou mais no resultado da consulta, em qualquer ordem.  Nos dois primeiros exemplos, não anônimos tipos são necessários porque as consultas selecionar elementos de tipos nomeados:  
  
-   `custs1` Contém uma coleção de cadeias de caracteres, pois `cust.Name` é uma cadeia de caracteres.  
  
     [!CODE [VbVbalrAnonymousTypes#30](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#30)]  
  
-   `custs2` Contém uma coleção de objetos `Customer`,porque cada elemento do `customers` é um objeto `Customer`, e o elemento inteiro é selecionado pela consulta.  
  
     [!CODE [VbVbalrAnonymousTypes#31](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#31)]  
  
 No entanto, tipos nomeados apropriados não estão sempre disponíveis.  Convém selecionar nomes de clientes e endereços para uma finalidade, números de identificação do cliente e locais para outro e os nomes dos clientes, endereços e históricos pedido para um terceiro.  Anônimos tipos permitem que você selecionar qualquer combinação de propriedades, em qualquer ordem, sem primeiro declarar um novo tipo nomeado para armazenar o resultado.  Em vez disso, o compilador cria um tipo anônimo para cada compilação de propriedades.  A consulta a seguir seleciona somente o cliente do nome e número de identificação de cada objeto `Customer` no `customers`.  Portanto, o compilador cria um tipo anônimo que contém somente essas duas propriedades.  
  
 [!CODE [VbVbalrAnonymousTYpes#32](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#32)]  
  
 Tanto os nomes e os tipos de dados das propriedades no tipo anônimo são tirados dos argumentos para `Select`,`cust.Name` e `cust.ID`.  As propriedades em um tipo anônimo que é criado por uma consulta são sempre propriedades chave.  Quando `custs3` é executado no loop `For Each` a seguir, o resultado é um conjunto de instâncias de um tipo com duas propriedades chave, `Name` anônimo e `ID`.  
  
 [!CODE [VbVbalrAnonymousTypes#33](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#33)]  
  
 Os elementos da coleção representado por `custs3` são altamente digitados, e você pode usar o IntelliSense para navegar através das propriedades disponíveis e para verificar seus tipos.  
  
 Para mais informações, consulte [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md).  
  
## Decidir se usar tipos anônimos  
 Antes de criar um objeto como uma instância de uma classe anônima, considere se que é a melhor opção.  Por exemplo, se você deseja criar um objeto temporário para conter dados relacionados, e tiver nenhuma necessidade de outros campos e métodos que pode conter uma classe concluída, um tipo anônimo é uma boa solução.  Tipos anônimos são também convenientes se você desejar uma seleção diferente de propriedades para cada declaração, ou se você quiser alterar a ordem das propriedades.  No entanto, se seu projeto inclui vários objetos que têm as mesmas propriedades, em uma ordem fixa, você pode declará\-las mais facilmente usando um tipo nomeado com um construtor de classe.  Por exemplo, com um construtor apropriado, é mais fácil várias instâncias de uma classe `Product` declarar que ele é para declarar várias instâncias de um tipo anônimo.  
  
 [!CODE [VbVbalrAnonymousTypes#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#9)]  
  
 Outra vantagem dos tipos nomeados é que o compilador pode pegar um acidental Digitação incorreta de propriedade Nome.  Nos exemplos a anteriores, `firstProd2`,`secondProd2` e `thirdProd2` pretendem ser instâncias do mesmo tipo anônimo.  No entanto, se você fosse acidentalmente declarar `thirdProd2` em uma das maneiras a seguir, seu tipo deve ser diferente do `firstProd2` e `secondProd2`.  
  
 [!CODE [VbVbalrAnonymousTypes#10](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes#10)]  
  
 Além disso, há limitações no uso dos tipos anônimos que não se aplicam às instâncias dos tipos nomeados.  `firstProd2``secondProd2` e `thirdProd2` são instâncias do mesmo tipo anônimo.  No entanto, o nome para o tipo anônimo compartilhado não está disponível e não pode aparecer em um nome de tipo é esperado no seu código.  Por exemplo, um tipo anônimo não pode ser usado para definir uma assinatura método, para declarar outra variável do campo ou em qualquer declaração de tipo.  Um resultado, anônimos tipos são não apropriados quando você tem que compartilhar informações entre os métodos.  
  
## Definição tipo anônimo  
 Em resposta para a declaração de uma instância de um tipo anônimo, o compilador cria um novo definição de classe que contém as propriedades para o tipo especificadas.  
  
 Se um declaração de tipo anônimo contém pelo menos uma propriedade de chave, o definição de tipo substitui três membros herdados <xref:System.Object>:<xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A> e <xref:System.Object.ToString%2A>.  O código produzido para teste de igualdade e determinar que o valor código hash considera apenas as propriedades da chave.  Se o tipo anônimo contiver sem propriedades chave, somente <xref:System.Object.ToString%2A> é substituído.  Propriedades explicitamente nomeadas de um tipo anônimo não é possível entrar em conflito com esses métodos gerados.  Ou seja, não é possível usar `.Equals`, `.GetHashCode`, ou `.ToString` para nomear uma propriedade.  
  
 Tipo anônimo definições que incluem pelo menos uma propriedade de chave também implementa a interface <xref:System.IEquatable%601?displayProperty=fullName>, onde `T` é o tipo do tipo anônimo.  
  
 Para obter mais informações sobre o código criado pelo compilador e a funcionalidade dos métodos substituídos, consulte [Definição do tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md).  
  
## Consulte também  
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Definição do tipo anônimo](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [Chave](../../../../visual-basic/language-reference/modifiers/key.md)