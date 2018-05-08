---
title: Como inserir e remover dados de uma variável (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
ms.openlocfilehash: bfda451cefff699561253910715d8450414b00ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>Como inserir e remover dados de uma variável (Visual Basic)
Você pode armazenar um valor em uma variável, colocando o nome da variável no lado esquerdo de uma instrução de atribuição.  
  
## <a name="putting-data-in-a-variable"></a>Colocar dados em uma variável  
  
#### <a name="to-store-a-value-in-a-variable"></a>Para armazenar um valor em uma variável  
  
-   Use o nome da variável no lado esquerdo de uma instrução de atribuição.  
  
     O exemplo a seguir define o valor da variável `alpha`.  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     O valor gerado no lado direito da instrução de atribuição é armazenado na variável.  
  
## <a name="getting-data-from-a-variable"></a>Obtendo dados de uma variável  
 Recuperar o valor da variável, incluindo o nome da variável em uma expressão.  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>Para recuperar um valor de uma variável  
  
-   Use o nome da variável em uma expressão. Você pode usar uma variável em qualquer lugar você pode usar uma constante ou um literal, exceto em uma expressão que define o valor de uma constante.  
  
     -ou-  
  
-   Use o nome de variável seguido de igual (`=`) entrar em uma instrução de atribuição.  
  
     O exemplo a seguir lê o valor da variável `startValue` e, em seguida, usa o valor da variável `counter` em uma expressão.  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     O valor da variável participa na expressão apenas como uma constante seria e, em seguida, ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.  
  
## <a name="see-also"></a>Consulte também  
 [Variáveis](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Declaração de Variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Variáveis de Objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
