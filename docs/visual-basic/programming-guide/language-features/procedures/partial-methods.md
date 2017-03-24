---
title: "Métodos parciais (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PartialMethod
- PartialMethod
dev_langs:
- VB
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial, methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d9d0c6b2f13f440fafb4fa246d4cd6cfb8d485bc
ms.lasthandoff: 03/13/2017

---
# <a name="partial-methods-visual-basic"></a>Métodos parciais (Visual Basic)
Métodos parciais permitem que desenvolvedores insiram lógica personalizada em código. Normalmente, o código faz parte de uma classe gerada pelo designer. Métodos parciais são definidos em uma classe parcial que é criada por um gerador de código, e elas são usadas para fornecer uma notificação de que algo foi alterado. Elas permitem que o desenvolvedor especificar o comportamento personalizado em resposta à alteração.  
  
 O designer do gerador de código define apenas a assinatura do método e um ou mais chamadas para o método. Os desenvolvedores podem, em seguida, fornecer implementações para o método se desejar personalizar o comportamento do código gerado. Quando nenhuma implementação for fornecida, chamadas ao método são removidas pelo compilador, resultando em nenhuma sobrecarga adicional de desempenho.  
  
## <a name="declaration"></a>Declaração  
 O código gerado marca a definição de um método parcial, colocando a palavra-chave `Partial` no início da linha de assinatura.  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 A definição deve cumprir as condições a seguir:  
  
-   O método deve ser um `Sub`, e não um `Function`.  
  
-   O corpo do método deve ser deixado em branco.  
  
-   O modificador de acesso deve ser `Private`.  
  
## <a name="implementation"></a>Implementação  
 A implementação consiste principalmente preencher o corpo do método parcial. A implementação é normalmente uma classe parcial separada da definição e é escrita por um desenvolvedor que deseja estender o código gerado.  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 O exemplo anterior duplica a assinatura na declaração exatamente, mas são variações possíveis. Em particular, outros modificadores podem ser adicionados, como `Overloads` ou `Overrides`. Apenas um `Overrides` modificador é permitido. Para obter mais informações sobre o método modificadores, consulte [instrução Sub](../../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## <a name="use"></a>Uso  
 Chamar um método parcial como você poderia chamar qualquer outro `Sub` procedimento. Se o método foi implementado, os argumentos são avaliados e o corpo do método é executado. No entanto, lembre-se de que a implementação de um método parcial é opcional. Se o método não está implementado, uma chamada para ele não tem nenhum efeito, e expressões passadas como argumentos para o método não são avaliadas.  
  
## <a name="example"></a>Exemplo  
 Em um arquivo denominado Product.Designer.vb, defina uma `Product` classe que tem um `Quantity` propriedade.  
  
 [!code-vb[VbVbalrPartialMeths n º&4;](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 Em um arquivo denominado Product vb, forneça uma implementação de `QuantityChanged`.  
  
 [!code-vb[VbVbalrPartialMeths n º&5;](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 Finalmente, no método principal de um projeto, declare uma `Product` de instância e forneça um valor inicial para sua `Quantity` propriedade.  
  
 [!code-vb[VbVbalrPartialMeths n º&6;](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 Deve aparecer uma caixa de mensagem que exibe esta mensagem:  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>Consulte também  
 [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Procedimentos Sub](./sub-procedures.md)   
 [Parâmetros opcionais](./optional-parameters.md)   
 [Parcial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Geração de código em LINQ to SQL](https://msdn.microsoft.com/library/bb399400)   
 [Adicionando a lógica comercial usando métodos parciais](https://msdn.microsoft.com/library/bb546176)
