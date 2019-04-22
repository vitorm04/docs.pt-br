---
title: Quando usar uma enumeração (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: ff2d8c324aee8bbccef050c020e5392368b05b1c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825089"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Quando usar uma enumeração (Visual Basic)
Enumerações oferecem uma maneira fácil de trabalhar com conjuntos de constantes relacionadas. Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores. Enumerações são tratadas como tipos de dados, e você pode usá-los para criar conjuntos de constantes para uso com variáveis e propriedades.  
  
## <a name="when-to-use-an-enumeration"></a>Quando usar uma enumeração  
 Sempre que um procedimento aceita um conjunto limitado de variáveis, considere o uso de uma enumeração. Enumerações Certifique-se para o código mais claro e mais legível, especialmente quando os nomes significativos são usados.  
  
 Os benefícios de usar enumerações incluem:  
  
-   Reduz erros causados por Transpor ou números de erros de digitação.  
  
-   Torna mais fácil alterar os valores no futuro.  
  
-   Torna o código mais fácil de ler, que significa que é menos provável que os erros serão surgir nele.  
  
-   Garante a compatibilidade com versões posteriores. Com enumerações, seu código tem menos probabilidade de falhar se futuramente alguém altera os valores correspondentes aos nomes de membros.  
  
## <a name="naming-enumerations"></a>Enumerações de nomenclatura  
 Use uma convenção de nomenclatura para os membros de enumeração. Quando o Visual Basic encontra um nome de membro de enumeração, uma exceção pode ser lançada se outras bibliotecas de tipo referenciado contêm o mesmo nome. Use um prefixo exclusivo que identifica os valores do seu aplicativo ou componente.  
  
 Ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome de enumeração ou então, use o `Imports` instrução. Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Enumerações predefinidas  
 Visual Basic fornece um número de enumerações predefinidos, como `FirstDayOfWeek` e `MsgBoxResult`, para facilitar o seu código. Para obter uma lista delas, consulte [constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Consulte também

- [Como: Declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Como: Fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Como: Iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [Como: Determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)
- [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
