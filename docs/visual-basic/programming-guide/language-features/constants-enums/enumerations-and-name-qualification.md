---
title: Enumerações e qualificação de nome
ms.date: 07/20/2015
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
ms.openlocfilehash: 4121266447b771ba954ad52a46e0d8b88de3f9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347493"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>Enumerações e qualificação de nome (Visual Basic)
Normalmente, ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração. Por exemplo, para fazer referência ao membro de `Sunday` de sua enumeração de `Days`, você usaria a seguinte sintaxe:  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a>Usando a instrução Imports  
 Você pode evitar o uso de nomes totalmente qualificados adicionando uma instrução `Imports` à seção de declarações de namespace do seu código, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 Uma instrução `Imports` importa nomes de namespace de projetos e assemblies referenciados e de dentro do mesmo projeto como o módulo no qual a instrução é exibida. Depois que essa instrução for adicionada, você poderá consultar seus membros de enumeração sem qualificação, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 Ao organizar conjuntos de constantes relacionadas em enumerações, você pode usar os mesmos nomes de constantes em diferentes contextos. Por exemplo, você pode usar os mesmos nomes para as constantes do dia da semana nas enumerações `Days` e `WorkDays`. Se você usar a instrução `Imports` com suas enumerações, deverá ter cuidado para evitar referências ambíguas. Considere o exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 Supondo que `Monday` seja membro da enumeração `Days` e da enumeração `Workdays`, esse código gera um erro do compilador. Para evitar referências ambíguas ao fazer referência a uma constante individual, qualifique o nome da constante com sua enumeração. O código a seguir refere-se às constantes `Saturday` nas enumerações `Days` e `WorkDays`.  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a>Consulte também

- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Como: iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Tipos de Dados Constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Tipos de Dados](../../../../visual-basic/language-reference/data-types/index.md)
