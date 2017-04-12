---
title: 'Como: declarar uma estrutura (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declarations, structures
- structure statements
- statements [Visual Basic], structure
- structures, declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: ee69335557e7618810982f93ab2d62e1ad64e0f9
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-a-structure-visual-basic"></a>Como declarar uma estrutura (Visual Basic)
Começar com uma declaração de estrutura de [instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md), e termina com o `End` `Structure` instrução. Entre essas duas instruções, você deve declarar pelo menos um *elemento*. Os elementos podem ser de qualquer tipo de dados, mas pelo menos um deve ser uma variável não compartilhada ou um evento não compartilhado, não personalizado.  
  
 Você não pode inicializar qualquer um dos elementos de estrutura na declaração da estrutura. Quando você declara uma variável para ser de um tipo de estrutura, atribuir valores para os elementos, acessando-los por meio da variável.  
  
 Para uma discussão sobre as diferenças entre as estruturas e classes, consulte [estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Para fins de demonstração, considere uma situação em que você deseja manter o controle de nome, ramal e salário do funcionário. Uma estrutura permite que você faça isso em uma única variável.  
  
### <a name="to-declare-a-structure"></a>Para declarar uma estrutura  
  
1.  Crie o início e final instruções para a estrutura.  
  
     Você pode especificar o nível de acesso de uma estrutura usando o [pública](../../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../../visual-basic/language-reference/modifiers/friend.md), ou [particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra-chave, ou você pode permitir que ele padrão `Public`.  
  
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
  
     O `salary` campo no exemplo anterior é `Private`, que significa que não está acessível fora da estrutura, até mesmo de classe que contém. No entanto, o `giveRaise` procedimento é `Public`, portanto, ele pode ser chamado de fora da estrutura. Da mesma forma, você pode gerar o `salaryReviewTime` evento de fora da estrutura.  
  
     Além de variáveis, `Sub` procedimentos e eventos, você também pode definir constantes, `Function` procedimentos e propriedades em uma estrutura. Você pode designar no máximo uma propriedade como o *propriedade padrão*, desde que ela tem pelo menos um argumento. Você pode manipular um evento com um [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento. Para obter mais informações, consulte [como: declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Variáveis de estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Estruturas e Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Tipo de Dados Definido pelo Usuário](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
