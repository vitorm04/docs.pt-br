---
title: "Quando usar uma enumeração (Visual Basic) | Documentos do Microsoft"
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
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
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
ms.openlocfilehash: f22102a2e1e7eafd7fcf4db1f46af2cc622eba70
ms.lasthandoff: 03/13/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Quando usar uma enumeração (Visual Basic)
Enumerações oferecem uma maneira fácil de trabalhar com conjuntos de constantes relacionadas. Uma enumeração, ou `Enum`, é um nome simbólico para um conjunto de valores. Enumerações são tratadas como tipos de dados, e você pode usá-las para criar conjuntos de constantes para uso com variáveis e propriedades.  
  
## <a name="when-to-use-an-enumeration"></a>Quando usar uma enumeração  
 Sempre que um procedimento aceita um conjunto limitado de variáveis, considere usar uma enumeração. Enumerações fazem para código mais claro e mais legível, especialmente quando são utilizados nomes significativos.  
  
 Os benefícios de usar enumerações incluem:  
  
-   Reduz erros causados por transpondo ou números de erros de digitação.  
  
-   É fácil alterar os valores no futuro.  
  
-   Torna o código mais fácil de ler, que significa que é menos provável que os erros serão surgir dentro dele.  
  
-   Garante a compatibilidade com versões posteriores. Com enumerações, seu código é menor probabilidade de falhar se futuramente alguém altera os valores correspondentes aos nomes de membro.  
  
## <a name="naming-enumerations"></a>Enumerações de nomenclatura  
 Use uma convenção de nomenclatura para membros de enumeração. Quando [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encontra um nome de membro de enumeração, uma exceção pode ser disparada se outras bibliotecas de tipo referenciado com o mesmo nome. Use um prefixo exclusivo que identifica os valores do seu aplicativo ou componente.  
  
 Ao fazer referência a um membro de uma enumeração, você deve qualificar o nome do membro com o nome da enumeração ou então usar o `Imports` instrução. Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Enumerações predefinidas  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Fornece um número de enumerações predefinidos, como `FirstDayOfWeek` e `MsgBoxResul`t, para facilitar o seu código. Para obter uma lista desses consulte [constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Consulte também  
 [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)
