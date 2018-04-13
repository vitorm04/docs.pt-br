---
title: Quando usar uma enumeração (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3b2937cc71c0c31bd8dce3d77fb33f48e1b5750
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Quando usar uma enumeração (Visual Basic)
Enumerações oferecem uma maneira fácil de trabalhar com conjuntos de constantes relacionadas. Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores. Enumerações são tratadas como tipos de dados, e você pode usá-los para criar conjuntos de constantes para uso com variáveis e propriedades.  
  
## <a name="when-to-use-an-enumeration"></a>Quando usar uma enumeração  
 Sempre que um procedimento aceita um conjunto limitado de variáveis, considere o uso de uma enumeração. Enumerações tornar código mais clara e mais legível, especialmente quando são usados nomes significativos.  
  
 Os benefícios do uso de enumerações incluem:  
  
-   Reduz os erros causados por Transpor ou números de erros de digitação.  
  
-   É fácil alterar os valores no futuro.  
  
-   Torna o código mais fácil de ler, o que significa que é menos provável que os erros serão surgir nele.  
  
-   Garante a compatibilidade com versões posteriores. Com enumerações, seu código tem menos probabilidade de falhar se futuramente alguém altera os valores correspondentes aos nomes de membros.  
  
## <a name="naming-enumerations"></a>Enumerações de nomenclatura  
 Use uma convenção de nomenclatura para os membros da enumeração. Quando [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] encontra um nome de membro de enumeração, uma exceção pode ser acionada se outras bibliotecas de tipo referenciado com o mesmo nome. Use um prefixo exclusivo que identifica os valores do seu aplicativo ou componente.  
  
 Ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome de enumeração ou então usar o `Imports` instrução. Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Enumerações predefinidas  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Fornece um número de enumerações predefinidos, como `FirstDayOfWeek` e `MsgBoxResult`, para facilitar o seu código. Para obter uma lista delas, consulte [constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Enumerações e Qualificação de Nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Como: iterar por meio de uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
