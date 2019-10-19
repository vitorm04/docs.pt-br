---
title: Como declarar uma estrutura (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: c3090b5b8e53e5a5a990ae11c91464797bde9803
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582299"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>Como declarar uma estrutura (Visual Basic)
Você começa uma declaração de estrutura com a [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)e a encerra com a instrução `End Structure`. Entre essas duas instruções, você deve declarar pelo menos um *elemento*. Os elementos podem ser de qualquer tipo de dados, mas pelo menos um deve ser uma variável não compartilhada ou um evento não compartilhado e não-personalizado.  
  
 Você não pode inicializar nenhum dos elementos de estrutura na declaração de estrutura. Quando você declara uma variável para ser de um tipo de estrutura, você atribui valores aos elementos acessando-os por meio da variável.  
  
 Para obter uma discussão sobre as diferenças entre estruturas e classes, consulte [estruturas e classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Para fins de demonstração, considere uma situação em que você deseja acompanhar o nome, a extensão do telefone e o salário de um funcionário. Uma estrutura permite que você faça isso em uma única variável.  
  
### <a name="to-declare-a-structure"></a>Para declarar uma estrutura  
  
1. Crie as instruções inicial e final para a estrutura.  
  
     Você pode especificar o nível de acesso de uma estrutura usando a palavra-chave [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)ou [Private](../../../../visual-basic/language-reference/modifiers/private.md) , ou pode deixar que ela seja padronizada para `Public`.  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. Adicione elementos ao corpo da estrutura.  
  
     Uma estrutura deve ter pelo menos um elemento. Você deve declarar todos os elementos e especificar um nível de acesso para ele. Se você usar a [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sem nenhuma palavra-chave, o padrão de acessibilidade será `Public`.  
  
    ```vb  
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
  
     O campo `salary` no exemplo anterior é `Private`, o que significa que ele está inacessível fora da estrutura, mesmo da classe que a contém. No entanto, o procedimento de `giveRaise` é `Public`, portanto, ele pode ser chamado de fora da estrutura. Da mesma forma, você pode gerar o evento `salaryReviewTime` de fora da estrutura.  
  
     Além de variáveis, procedimentos de `Sub` e eventos, você também pode definir constantes, `Function` procedimentos e propriedades em uma estrutura. Você pode designar, no máximo, uma propriedade como a *propriedade padrão*, desde que ela aceite pelo menos um argumento. Você pode manipular um evento com um procedimento de `Sub` [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) . Para obter mais informações, consulte [como: declarar e chamar uma propriedade padrão em Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Variáveis de Estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [Estruturas e Outros Elementos de Programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Tipo de Dados Definido pelo Usuário](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
