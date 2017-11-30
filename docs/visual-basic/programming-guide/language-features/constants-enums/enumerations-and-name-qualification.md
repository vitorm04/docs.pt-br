---
title: "Enumerações e qualificação de nome (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb97d6a8f4b7e81f2b759010214e200ec63ff21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Enumerações e qualificação de nome (Visual Basic)
Normalmente, ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome de enumeração. Por exemplo, para referir-se a `Sunday` membro do seu `Days` enumeração, você usaria a seguinte sintaxe:  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Usando a instrução Imports  
 Você pode evitar o uso de nomes totalmente qualificados, adicionando uma `Imports` instrução para a seção de declarações de namespace do seu código, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 Um `Imports` instrução importa nomes de namespaces de projetos referenciados e assemblies e do mesmo projeto como o módulo no qual a instrução aparece. Depois que essa instrução é adicionada, você pode consultar os membros da enumeração sem qualificação, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Organizando conjuntos de constantes relacionadas em enumerações, você pode usar os mesmos nomes de constantes em diferentes contextos. Por exemplo, você pode usar os mesmos nomes para as constantes de dia da semana no `Days` e `WorkDays` enumerações. Se você usar o `Imports` instrução com suas enumerações, você deve ter cuidado para evitar referências ambíguas. Considere o exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Supondo que `Monday` é um membro de ambos os `Days` enumeração e o `Workdays` enumeração, esse código gera um erro do compilador. Para evitar referências ambíguas quando se referem a uma constante individual, qualifica o nome constante com sua enumeração. O código a seguir refere-se para o `Saturday` constantes no `Days` e `WorkDays` enumerações.  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Como: iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Instrução Imports (Tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
