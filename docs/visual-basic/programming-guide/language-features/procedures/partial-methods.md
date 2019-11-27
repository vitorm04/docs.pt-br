---
title: Métodos parciais
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
ms.openlocfilehash: 7abf0565a985f1fb44fcf2bb91b9220d57a10f20
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352631"
---
# <a name="partial-methods-visual-basic"></a>Métodos parciais (Visual Basic)
Os métodos parciais permitem que os desenvolvedores insiram lógica personalizada no código. Normalmente, o código faz parte de uma classe gerada pelo designer. Os métodos parciais são definidos em uma classe parcial que é criada por um gerador de código e são comumente usadas para fornecer notificações de que algo foi alterado. Eles permitem que o desenvolvedor especifique o comportamento personalizado em resposta à alteração.  
  
 O designer do gerador de código define apenas a assinatura do método e uma ou mais chamadas para o método. Os desenvolvedores podem então fornecer implementações para o método se desejarem personalizar o comportamento do código gerado. Quando nenhuma implementação é fornecida, as chamadas para o método são removidas pelo compilador, resultando em nenhuma sobrecarga adicional de desempenho.  
  
## <a name="declaration"></a>Declaração  
 O código gerado marca a definição de um método parcial colocando a palavra-chave `Partial` no início da linha de assinatura.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 A definição deve atender às seguintes condições:  
  
- O método deve ser um `Sub`, não um `Function`.  
  
- O corpo do método deve ser deixado vazio.  
  
- O modificador de acesso deve ser `Private`.  
  
## <a name="implementation"></a>Implementação  
 A implementação consiste principalmente em preencher o corpo do método parcial. A implementação normalmente está em uma classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 O exemplo anterior duplica a assinatura na declaração exatamente, mas as variações são possíveis. Em particular, outros modificadores podem ser adicionados, como `Overloads` ou `Overrides`. Somente um modificador de `Overrides` é permitido. Para obter mais informações sobre modificadores de método, consulte [sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Uso  
 Você chama um método parcial como você chamaria qualquer outro procedimento `Sub`. Se o método tiver sido implementado, os argumentos serão avaliados e o corpo do método será executado. No entanto, lembre-se de que a implementação de um método parcial é opcional. Se o método não for implementado, uma chamada para ele não terá efeito e as expressões passadas como argumentos para o método não serão avaliadas.  
  
## <a name="example"></a>Exemplo  
 Em um arquivo chamado Product. designer. vb, defina uma classe `Product` que tenha uma propriedade `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#4)]  
  
 Em um arquivo chamado Product. vb, forneça uma implementação para `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#5)]  
  
 Por fim, no método principal de um projeto, declare uma instância de `Product` e forneça um valor inicial para sua propriedade `Quantity`.  
  
 [!code-vb[VbVbalrPartialMeths#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrPartialMeths/VB/Class1.vb#6)]  
  
 Será exibida uma caixa de mensagem que exibe esta mensagem:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Consulte também

- [Instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Subprocedimentos](./sub-procedures.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)
- [Geração de código em LINQ to SQL](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Adicionando a lógica de negócios usando métodos parciais](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
