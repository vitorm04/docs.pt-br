---
title: Métodos parciais (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 765a667f18340c53909c3ff1e9fcc5f2ffc0f9bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791931"
---
# <a name="partial-methods-visual-basic"></a>Métodos parciais (Visual Basic)
Métodos parciais permitem que os desenvolvedores insiram lógica personalizada no código. Normalmente, o código é parte de uma classe gerado pelo designer. Métodos parciais são definidos em uma classe parcial que é criada por um gerador de código, e elas são usadas para fornecer uma notificação de que algo foi alterado. Eles permitem ao desenvolvedor especificar o comportamento personalizado em resposta à alteração.  
  
 O designer do gerador de código define apenas a assinatura do método e uma ou mais chamadas para o método. Os desenvolvedores, em seguida, podem fornecer implementações para o método se desejar personalizar o comportamento do código gerado. Quando nenhuma implementação for fornecida, chamadas ao método são removidas pelo compilador, resultando em nenhuma sobrecarga de desempenho adicional.  
  
## <a name="declaration"></a>Declaração  
 O código gerado marca a definição de um método parcial, colocando a palavra-chave `Partial` no início da linha de assinatura.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 A definição deve atender aos seguintes condições:  
  
- O método deve ser um `Sub`, e não um `Function`.  
  
- O corpo do método deve ser deixado vazio.  
  
- O modificador de acesso deve ser `Private`.  
  
## <a name="implementation"></a>Implementação  
 A implementação consiste basicamente em preencher o corpo do método parcial. A implementação é normalmente em uma classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 O exemplo anterior duplica a assinatura na declaração exatamente, mas variações são possíveis. Em particular, outros modificadores podem ser adicionados, tais como `Overloads` ou `Overrides`. Apenas um `Overrides` modificador é permitido. Para obter mais informações sobre o método modificadores, consulte [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Use  
 Chamar um método parcial como você poderia chamar qualquer outro `Sub` procedimento. Se o método tiver sido implementado, os argumentos são avaliados e o corpo do método é executado. No entanto, lembre-se de que a implementação de um método parcial é opcional. Se o método não está implementado, uma chamada para que ele não tem nenhum efeito e expressões passadas como argumentos para o método não são avaliadas.  
  
## <a name="example"></a>Exemplo  
 Em um arquivo denominado Product.Designer.vb, defina uma `Product` classe que tem um `Quantity` propriedade.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 Em um arquivo denominado Product vb, fornecer uma implementação para `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Por fim, no método principal de um projeto, declarar uma `Product` da instância e fornecer um valor inicial para sua `Quantity` propriedade.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Deve aparecer uma caixa de mensagem que exibe esta mensagem:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Consulte também

- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Subprocedimentos](./sub-procedures.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Geração de código em LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Adicionando a lógica de negócios usando métodos parciais](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
