---
title: Como declarar uma estrutura (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 6128addd60609bfc88a1409648fb320bc7089974
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Como declarar uma estrutura (Visual Basic)
Começar com uma declaração de estrutura de [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md), e você terminar com a `End` `Structure` instrução. Entre essas duas instruções, você deve declarar pelo menos um *elemento*. Os elementos podem ser de qualquer tipo de dados, mas pelo menos um deve ser uma variável não compartilhada ou um evento não compartilhado, não personalizado.  
  
 Você não pode inicializar qualquer um dos elementos de estrutura na declaração da estrutura. Quando você declara uma variável de um tipo de estrutura, atribuir valores para os elementos por acessá-los através da variável.  
  
 Para obter uma discussão das diferenças entre as estruturas e classes, consulte [estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Para fins de demonstração, considere uma situação em que você deseja manter o controle de nome, ramal e salário do funcionário. Uma estrutura permite que você faça isso em uma única variável.  
  
### <a name="to-declare-a-structure"></a>Para declarar uma estrutura  
  
1.  Crie o inicial e final instruções para a estrutura.  
  
     Você pode especificar o nível de acesso de uma estrutura usando a [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegidos](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [privada](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, ou você pode deixá-la o padrão `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Adicione elementos ao corpo da estrutura.  
  
     Uma estrutura deve ter pelo menos um elemento. Você deve declarar cada elemento e especificar um nível de acesso para ele. Se você usar o [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sem quaisquer palavras-chave, a acessibilidade padrão é `Public`.  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     O `salary` campo no exemplo anterior é `Private`, que significa que ele não está acessível fora da estrutura, até mesmo da classe continente. No entanto, o `giveRaise` procedimento é `Public`, portanto, ele pode ser chamado de fora da estrutura. Da mesma forma, você pode gerar o `salaryReviewTime` evento de fora da estrutura.  
  
     Além de variáveis, `Sub` procedimentos e eventos, você também pode definir constantes, `Function` procedimentos e as propriedades em uma estrutura. Você pode designar no máximo uma propriedade como o *propriedade padrão*, desde que ela tem pelo menos um argumento. Você pode manipular um evento com um [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento. Para obter mais informações, consulte [como: declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Variáveis de Estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [Estruturas e Outros Elementos de Programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Tipo de Dados Definido pelo Usuário](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
