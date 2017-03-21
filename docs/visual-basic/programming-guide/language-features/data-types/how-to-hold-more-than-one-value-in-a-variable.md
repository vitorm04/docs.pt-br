---
title: "Como: armazenar mais de um valor em uma variável (Visual Basic) | Documentos do Microsoft"
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
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
caps.latest.revision: 16
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
ms.openlocfilehash: ed7ffd8f530135036acf0572a0046ed0d0df6de4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Como manter mais de um valor em uma variável (Visual Basic)
Uma variável contém mais de um valor se você declará-la para ser de um *tipo de dados composto*.  
  
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) incluem classes, matrizes e estruturas. Uma variável de um tipo de dados composto pode conter uma combinação de tipos de dados elementares e outros tipos compostos. Estruturas e classes podem armazenar código bem como dados.  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a>Para manter mais de um valor em uma variável  
  
1.  Determine que tipo de dados compostos que você deseja usar para sua variável.  
  
2.  Se o tipo de dados compostos já não estiver definido, defini-lo para que sua variável possa usá-lo.  
  
    -   Defina uma estrutura com um [declaração de estrutura](../../../../visual-basic/language-reference/statements/structure-statement.md).  
  
    -   Definir uma matriz com um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
    -   Definir uma classe com um [instrução Class](../../../../visual-basic/language-reference/statements/class-statement.md).  
  
3.  Declare a variável com um `Dim` instrução.  
  
4.  Siga o nome da variável com um `As` cláusula.  
  
5.  Execute o `As` palavra-chave com o nome do tipo de dados compostos apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Caracteres de tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
