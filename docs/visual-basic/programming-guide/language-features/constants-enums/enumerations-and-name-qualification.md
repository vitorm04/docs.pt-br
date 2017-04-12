---
title: "Enumerações e qualificação de nome (Visual Basic) | Documentos do Microsoft"
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
- declarations, enumerations
- Imports statement, namespace declarations
- declaring namespaces, enumerations
- name collisions
- ambiguous names, enumerations
- enumerations [Visual Basic], name qualification
- names, avoiding conflicts
- namespaces, declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references, enumeration members
- naming conventions, naming conflicts
- declarations, namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
caps.latest.revision: 20
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
ms.openlocfilehash: 27c828e89212dcdc140abd20c4628cb81fb19275
ms.lasthandoff: 03/13/2017

---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Enumerações e qualificação de nome (Visual Basic)
Normalmente, ao se referir a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração. Por exemplo, para referir-se a `Sunday` membro do seu `Days` enumeração, você usaria a sintaxe a seguir:  
  
 [!code-vb[VbEnumsTask n º&18;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Usando a instrução Imports  
 Você pode evitar o uso de nomes totalmente qualificados, adicionando uma `Imports` instrução à seção de declarações de namespaces do seu código, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 Um `Imports` instrução importa nomes de namespaces de projetos e assemblies referenciados e do mesmo projeto como o módulo no qual a instrução aparece. Depois que essa instrução é adicionada, você pode consultar os membros da enumeração sem qualificação, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask&#24;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Organizando conjuntos de constantes relacionadas em enumerações, você pode usar os mesmos nomes de constantes em contextos diferentes. Por exemplo, você pode usar os mesmos nomes para as constantes dias da semana no `Days` e `WorkDays` enumerações. Se você usar o `Imports` instrução com suas enumerações, você deve ter cuidado para evitar referências ambíguas. Considere o exemplo a seguir:  
  
 [!code-vb[VbEnumsTask&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[25 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Supondo que `Monday` é um membro de ambos os `Days` enumeração e `Workdays` enumeração, esse código gera um erro do compilador. Para evitar referências ambíguas quando se referir a uma constante individual, qualifica o nome constante com sua enumeração. O código a seguir refere-se para o `Saturday` constantes no `Days` e `WorkDays` enumerações.  
  
 [!code-vb[32 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Tipos de dados constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Instrução Imports (tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Tipos de Dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
