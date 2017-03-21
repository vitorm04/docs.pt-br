---
title: "Como: criar uma variável que não se altera em valor (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: 15
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
ms.openlocfilehash: 92370a44ed8c54ad8c2c2a4d48c77d4f8963f2de
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>Como criar uma variável que não se altera no valor (Visual Basic)
A noção de uma variável que não altera seu valor pode parecer contraditório. Mas há situações quando uma constante não é viável e é útil ter uma variável com um valor fixo. Nesse caso, você pode definir uma variável de membro com o [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) palavra-chave.  
  
 Não é possível usar o [instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md) para declarar e atribua um valor constante nas seguintes circunstâncias:  
  
-   O `Const` instrução não aceita o tipo de dados que você deseja usar  
  
-   Você não sabe o valor em tempo de compilação  
  
-   Não for possível computar o valor da constante em tempo de compilação  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>Para criar uma variável que não se altera em valor  
  
1.  No nível de módulo, declare uma variável de membro com o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)e incluem o [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) palavra-chave.  
  
    ```  
  
    Dim ReadOnly timeStarted  
    ```  
  
     Você pode especificar `ReadOnly` apenas em um variável de membro. Isso significa que você deve definir a variável no nível de módulo, fora de qualquer procedimento.  
  
2.  Se você pode calcular o valor em uma única instrução em tempo de compilação, use uma cláusula de inicialização no `Dim` instrução. Execute o [como](../../../../visual-basic/language-reference/statements/as-clause.md) cláusula com um sinal de igual (`=`), seguido por uma expressão. Certifique-se de que o compilador pode avaliar esta expressão para um valor constante.  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     Você pode atribuir um valor para um `ReadOnly` variável somente uma vez. Quando você fizer isso, nenhum código pode alterar seu valor.  
  
     Se você não sabe o valor em tempo de compilação, ou não é possível calcular em tempo de compilação em uma única instrução, você ainda pode atribui-lo em tempo de execução em um construtor. Para fazer isso, você deve declarar o `ReadOnly` variável no nível de classe ou estrutura. No construtor de classe ou estrutura, calcular o valor da variável fixa e atribuí-la à variável antes de retornar do construtor.  
  
## <a name="see-also"></a>Consulte também  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md)
