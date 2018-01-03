---
title: "Métodos parciais (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33e34c63988e74be2c22cb7b1358f5e8b04048c6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="partial-methods-visual-basic"></a>Métodos parciais (Visual Basic)
Métodos parciais permitem aos desenvolvedores inserir a lógica personalizada em código. Normalmente, o código é parte de uma classe gerado pelo designer. Métodos parciais são definidos em uma classe parcial que é criada por um gerador de código, e eles são usados para fornecer notificação de que algo foi alterado. Elas permitem que o desenvolvedor especificar o comportamento personalizado em resposta a alterações.  
  
 O designer do gerador de código define apenas a assinatura de método e uma ou mais chamadas para o método. Os desenvolvedores poderá fornecer implementações para o método se desejar personalizar o comportamento do código gerado. Quando nenhuma implementação for fornecida, chamadas ao método são removidas pelo compilador, resultando em nenhuma sobrecarga de desempenho adicionais.  
  
## <a name="declaration"></a>Declaração  
 O código gerado marca a definição de um método parcial, colocando a palavra-chave `Partial` no início da linha de assinatura.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 A definição deve atender aos seguintes condições:  
  
-   O método deve ser um `Sub`, não um `Function`.  
  
-   O corpo do método deve ser deixado vazio.  
  
-   O modificador de acesso deve ser `Private`.  
  
## <a name="implementation"></a>Implementação  
 A implementação consiste principalmente preencher o corpo do método parcial. A implementação normalmente é uma classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 O exemplo anterior duplica a assinatura na declaração exatamente, mas são variações possíveis. Em particular, outros modificadores podem ser adicionados, como `Overloads` ou `Overrides`. Apenas um `Overrides` modificador é permitido. Para obter mais informações sobre o método modificadores, consulte [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Use  
 Chamar um método parcial como você poderia chamar qualquer outro `Sub` procedimento. Se o método tiver sido implementado, os argumentos são avaliados e o corpo do método é executado. No entanto, lembre-se de que a implementação de um método parcial é opcional. Se o método não está implementado, uma chamada para que ele não tem nenhum efeito e expressões passadas como argumentos para o método não são avaliadas.  
  
## <a name="example"></a>Exemplo  
 Em um arquivo denominado Product.Designer.vb, defina um `Product` classe que tem um `Quantity` propriedade.  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 Em um arquivo denominado Product vb, forneça uma implementação para `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Finalmente, o método principal de um projeto, declare um `Product` instância e forneça um valor inicial para sua `Quantity` propriedade.  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Deve aparecer uma caixa de mensagem que exibe esta mensagem:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Parâmetros Opcionais](./optional-parameters.md)  
 [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Geração de código em LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Adicionando a lógica de negócios usando métodos parciais](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
