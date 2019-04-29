---
title: 'Como: Criar uma variável que não se altera no valor (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 7180e5141572d219ed02c57103e9d4b80cde536e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938223"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Como: Criar uma variável que não se altera no valor (Visual Basic)
A noção de uma variável que não altera seu valor pode parecer contraditório. Mas há situações quando uma constante não é viável e é útil ter uma variável com um valor fixo. Nesse caso, você pode definir uma variável de membro com o [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) palavra-chave.  
  
 Não é possível usar o [instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md) declarar e atribuir um valor constante nas seguintes circunstâncias:  
  
- O `Const` instrução não aceita o tipo de dados que você deseja usar  
  
- Você não souber o valor no tempo de compilação  
  
- Você não conseguir calcular o valor da constante em tempo de compilação  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Para criar uma variável que não se altera no valor  
  
1. No nível de módulo, declare uma variável de membro com o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)e incluem o [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) palavra-chave.  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     Você pode especificar `ReadOnly` apenas em uma variável de membro. Isso significa que você deve definir a variável no nível de módulo, fora de qualquer procedimento.  
  
2. Se você pode calcular o valor em uma única instrução em tempo de compilação, use uma cláusula de inicialização no `Dim` instrução. Siga as [como](../../../../visual-basic/language-reference/statements/as-clause.md) cláusula com um sinal de igual (`=`), seguido por uma expressão. Certifique-se de que o compilador pode avaliar esta expressão para um valor constante.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Você pode atribuir um valor para um `ReadOnly` variável somente uma vez. Quando você fizer isso, nenhum código pode alterar seu valor.  
  
     Se você não souber o valor no tempo de compilação, ou não pode computar em tempo de compilação em uma única instrução, você ainda pode atribui-lo em tempo de execução em um construtor. Para fazer isso, você deve declarar o `ReadOnly` variável no nível de classe ou estrutura. No construtor de classe ou estrutura, calcular o valor da variável fixa e atribua-o à variável antes de retornar do construtor.  
  
## <a name="see-also"></a>Consulte também

- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)
