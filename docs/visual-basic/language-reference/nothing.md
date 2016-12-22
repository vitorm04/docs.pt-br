---
title: "Nada (Visual Basic) | Microsoft Docs"
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
  - "Nothing"
  - "vb.Nothing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Nothing"
  - "palavra-chave Nothing, sintaxe"
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nada (Visual Basic)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Representa o valor padrão de qualquer tipo de dados.  Para tipos de referência, o valor padrão é o `null` referência.  Para tipos de valor, o valor padrão depende se o tipo de valor é anulável.  
  
> [!NOTE]
>  Para tipos de valor não nulo, `Nothing` Visual Basic difere de `null` em C\#.  No Visual Basic, se você definir uma variável de um tipo de valor não\-nulo para `Nothing`, a variável é definida como o valor padrão para seu tipo declarado.  No C\#, se você atribuir uma variável de um tipo de valor não\-nulo para `null`, ocorrerá um erro em tempo de compilação.  
  
## Comentários  
 `Nothing`representa o valor padrão de um tipo de dados.  O valor padrão depende de se encontrar a variável de um tipo de valor ou de um tipo de referência.  
  
 Uma variável de um  *tipo de valor* contém diretamente de seu valor.  Os tipos de valor incluem todos os tipos de dados numéricos, `Boolean`, `Char`, `Date`, todas as estruturas e todas as enumerações.  Uma variável de um  *tipo de referência* armazena uma referência a uma instância do objeto na memória.  Tipos de referência incluem classes, matrizes, delegados e seqüências de caracteres.  Para obter mais informações, consulte [Tipos de valor e referência](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Se uma variável é de um valor de tipo, o comportamento de `Nothing` depende se a variável é um tipo de dados anulável.  Para representar um tipo de valor nulo, adicione um `?` o modificador do nome de tipo.  A atribuição de `Nothing` a uma variável anulável define o valor para `null`.  Para mais informações e exemplos, consulte [Tipos de valor que permitem valor nulo](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Se uma variável é de um tipo de valor não é anulável, atribuindo `Nothing` para ele define como o valor padrão para seu tipo declarado.  Se o tipo contém membros variáveis, eles são definidos para seus valores padrão.  O exemplo a seguir ilustra isso para tipos escalares.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Se uma variável é de um tipo de referência, atribuindo `Nothing` à variável define\-o como um `null` referência do tipo da variável.  Uma variável que está definida como um `null` referência não está associada a qualquer objeto.  O exemplo a seguir demonstra isso.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Ao verificar se uma referência \(ou um valor nulo digite\) é a variável `null`, não use `= Nothing` ou `<> Nothing`.  Always use `Is Nothing` or `IsNot Nothing`.  
  
 Seqüências de caracteres em Visual Basic, a seqüência de caracteres vazia é igual a `Nothing`.  Portanto, `"" = Nothing` é verdadeiro.  
  
 O exemplo a seguir mostra as comparações que usam o `Is` e `IsNot` operadores.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Se você declarar uma variável sem usar um `As` cláusula e defina\-o como `Nothing`, a variável tem um tipo de `Object`.  Um exemplo disso é `Dim something = Nothing`.  Nesse caso ocorre de um erro de tempo de compilação quando `Option Strict` está ativado e `Option Infer` está desativado.  
  
 Quando você atribui `Nothing` a um variável de objeto, ela não mais se refere a qualquer instância do objeto.  Se a variável tivesse anteriormente referenciado uma instância, defini\-la como `Nothing` não finaliza a instância em si.  A instância é finalizada, e os recursos de memória e do sistema associados a ela são liberados, somente após o coletor de lixo \(GC\) detectar que não há mais referências ativas restantes.  
  
 `Nothing`difere do <xref:System.DBNull> objeto que representa um variant não inicializado ou uma coluna de banco de dados inexistente.  
  
## Consulte também  
 [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)   
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Tempo de vida no Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Operador Is](../../visual-basic/language-reference/operators/is-operator.md)   
 [Operador IsNot](../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Tipos de valor que permitem valor nulo](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)