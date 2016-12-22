---
title: "MustInherit (Visual Basic) | Microsoft Docs"
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
  - "MustInherit"
  - "vb.MustInherit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes abstratas, Classe MustInherit"
  - "classes [Visual Basic], abstrata"
  - "Classes MustInherit, Palavra-chave MustInherit"
  - "Palavra-chave MustInherit"
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# MustInherit (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que uma classe pode ser usada apenas como uma classe base e que não pode possível criar um objeto diretamente a partir dele.  
  
## Comentários  
 A finalidade de um  *classe base* \(também conhecido como um  *classe abstrata*\) é definir a funcionalidade comum a todas as classes que derivado dele.  Isso evita que as classes derivadas ter que redefinir os elementos comuns.  Em alguns casos, essa funcionalidade comum não é suficientemente completa para tornar um objeto utilizável e cada classe derivada define a funcionalidade ausente.  Nesse caso, você deseja que o código toma para criar objetos somente a partir de classes derivadas.  Você pode usar `MustInherit` na classe base para impor isso.  
  
 Outro uso de um `MustInherit` classe é restringir uma variável de um conjunto de classes relacionadas.  Você pode definir uma classe base e derivam todas essas classes relacionadas.  A classe base não precisa fornecer qualquer funcionalidade comum a todas as classes derivadas, mas ele pode servir como um filtro para atribuir valores às variáveis.  Se seu código consumindo declara uma variável como a classe base, o Visual Basic permite que você atribuir apenas um objeto de uma das classes derivadas para essa variável.  
  
 A.NET Framework define vários `MustInherit` classes, entre eles <xref:System.Array>, <xref:System.Enum>, e <xref:System.ValueType>.  <xref:System.ValueType>é um exemplo de uma classe base que restringe a uma variável.  Derivam de todos os tipos de valor de <xref:System.ValueType>.  Se você declarar uma variável como <xref:System.ValueType>, você pode atribuir somente os tipos de valor para a variável.  
  
## Regras  
  
-   **Contexto da Declaração.** Você pode usar `MustInherit` somente em um `Class` instrução.  
  
-   **Modificadores Combinados.** Não é possível especificar `MustInherit` em conjunto com `NotInheritable` na mesma declaração.  
  
## Exemplo  
 O exemplo a seguir ilustra a herança forçada e substituindo forçada.  A classe base `shape` define uma variável `acrossLine`.  As classes `circle` e `square` derivam de `shape`.  Eles herdam a definição de `acrossLine`, mas eles devem definir a função `area` porque esse cálculo é diferente para cada tipo de forma.  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 Você pode declarar `shape1` e `shape2` ser do tipo `shape`.  Entretanto, você não pode criar um objeto de `shape` porque ele não possui a funcionalidade da função `area` e está marcado como `MustInherit`.  
  
 Porque elas são declaradas como `shape`, as variáveis `shape1` e `shape2` não tem permissão para objetos de classes derivadas `circle` e `square`.  Visual Basic não permite atribuir qualquer outro objeto a essas variáveis, que lhe oferece um alto nível de segurança de tipos.  
  
## Uso  
 O modificador `MustInherit` pode ser utilizado neste contexto:  
  
 [Declaração de Classe](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## Consulte também  
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)   
 [Noções básicas de herança](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)