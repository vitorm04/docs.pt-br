---
title: "Como declarar uma estrutura (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarações, estruturas"
  - "instruções [Visual Basic], Estrutura "
  - "instruções structure"
  - "estruturas, declarando"
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como declarar uma estrutura (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Começar com uma declaração de estrutura de [Instrução Structure](../../../../visual-basic/language-reference/statements/structure-statement.md), e o termina com o `End``Structure` instrução.   Entre essas duas instruções, você deve declarar pelo menos um  *elemento*.  Os elementos podem ser de qualquer tipo de dados, mas pelo menos um deve ser uma variável compartilhada ou um evento de campos que não seja compartilhado.  
  
 Você não pode inicializar qualquer um dos elementos de estrutura na declaração da estrutura.  Quando você declara uma variável para ser de um tipo de estrutura, atribuir valores aos elementos, acessando\-los através da variável.  
  
 Para uma discussão sobre as diferenças entre as estruturas e classes, consulte [Estruturas e classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 Para fins de demonstração, considere uma situação onde você deseja manter o controle de nome, extensão telefônica e salário do funcionário.  Uma estrutura permite que você faça isso em uma única variável.  
  
### Para declarar uma estrutura  
  
1.  Crie o início e término de instruções para a estrutura.  
  
     Você pode especificar o nível de acesso de uma estrutura usando o [Público](../../../../visual-basic/language-reference/modifiers/public.md), [Protegido](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), ou [Particular](../../../../visual-basic/language-reference/modifiers/private.md) palavra\-chave, ou você pode deixar o padrão `Public`.  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  Adicione elementos ao corpo da estrutura.  
  
     Uma estrutura deve ter pelo menos um elemento.  Você deve declarar todos os elementos e especificar um nível de acesso para ele.  Se você usar o [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) sem quaisquer palavras\-chave, padrões de acessibilidade para `Public`.  
  
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
  
     O `salary` campo no exemplo anterior é `Private`, que significa que não está acessível fora da estrutura, até mesmo a partir da classe que o contém.  No entanto, o `giveRaise` procedimento é `Public`, portanto, podem ser chamado de fora da estrutura.  Da mesma forma, você pode aumentar a `salaryReviewTime` eventos de fora da estrutura.  
  
     Além da variáveis, `Sub` procedimentos e eventos, você também pode definir constantes, `Function` procedimentos e propriedades em uma estrutura.  Você pode designar a no máximo uma propriedade como o  *propriedade padrão*, desde que ele tem pelo menos um argumento.  Você pode manipular um evento com um [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedimento.  Para mais informações, consulte [Como declarar e chamar uma propriedade padrão no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md).  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Variáveis de estrutura](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Estruturas e classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Tipo de dados definido pelo usuário](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)