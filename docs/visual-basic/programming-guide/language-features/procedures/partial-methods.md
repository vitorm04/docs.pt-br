---
title: "M&#233;todos parciais (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.PartialMethod"
  - "PartialMethod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "lógica personalizada em código [Visual Basic]"
  - "inserindo lógica personalizada em código"
  - "métodos [Visual Basic], métodos parciais"
  - "métodos parciais [Visual Basic]"
  - "parcial, métodos [Visual Basic]"
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# M&#233;todos parciais (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Métodos parciais permitem que desenvolvedores insiram lógica personalizada no código.  Normalmente, o código é parte de uma classe gerada pelo designer.  Métodos parciais são definidos em um classe parcial que é criado por um gerador de código, e são normalmente usados para fornecer uma notificação informando que algo foi alterado.  Eles permitem o desenvolvedor especificar o comportamento personalizado na resposta para a alteração.  
  
 O designer do gerador de código define apenas a assinatura de método e um ou mais chamadas para o método.  Os desenvolvedores podem, então, fornecer implementações para o método se desejarem personalizar o comportamento do código gerado.  Quando nenhuma implementação for fornecida, chamadas ao método são removidas pelo compilador, resultando em nenhuma sobrecarga adicional de desempenho.  
  
## Declaração  
 O código gerado marca a definição de um método parcial, colocando a palavra\-chave `Partial` no início da linha de assinatura.  
  
```vb#  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 A definição deve atender a estas condições:  
  
-   O método deve ser um `Sub`, não um `Function`.  
  
-   O corpo do método deve ser deixado vazio.  
  
-   O modificador de acesso deve ser `Private`.  
  
## Implementação  
 A implementação consiste principalmente preencher o corpo do método parcial.  A implementação está normalmente em um classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.  
  
```vb#  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 O exemplo anterior duplica a assinatura na declaração exatamente, mas são variações possíveis.  Em particular, outros modificadores podem ser adicionados, como `Overloads` ou `Overrides`.  Somente um modificador `Overrides` é permitido.  Para obter mais informações sobre o método modificadores, consulte [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## Uso  
 Você chamar um método parcial como você poderia chamar qualquer outro procedimento `Sub`.  Se o método foi implementado, os argumentos são avaliados e o corpo do método é executado.  No entanto, lembre\-se de que implementar um método parcial é opcional.  Se o método não está implementado, uma chamada para ele não tem efeito, e expressões passados como argumentos para o método não são avaliadas.  
  
## Exemplo  
 Em um arquivo denominado Product.Designer.vb, defina uma classe `Product` que tenha uma propriedade `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 Em um arquivo denominado Product.vb, forneça uma implementação de `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Finalmente, no método principal de um projeto, declare uma instância `Product` e forneça um valor inicial para sua propriedade `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#6](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Um caixa de mensagem deve aparecer, a qual que exibe esta mensagem:  
  
 `Quantity was changed to 100`  
  
## Consulte também  
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Subprocedimentos](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Parâmetros opcionais](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Code Generation in LINQ to SQL](../Topic/Code%20Generation%20in%20LINQ%20to%20SQL.md)   
 [Adding Business Logic By Using Partial Methods](../Topic/Adding%20Business%20Logic%20By%20Using%20Partial%20Methods.md)