---
title: "Como: inicializar uma variável de matriz no Visual Basic | Documentos do Microsoft"
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
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
caps.latest.revision: 42
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
ms.openlocfilehash: 0793eafe0c5dc22b4b35f4c2913dfe7151a09379
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Como inicializar uma variável de matriz no Visual Basic
Você deve inicializar uma variável de matriz, incluindo uma matriz literal em uma `New` cláusula e especificando os valores iniciais da matriz. Você pode especificar o tipo ou permitir que ele ser inferidos dos valores na matriz de literal. Para obter mais informações sobre como o tipo é inferido, consulte "Preencher uma matriz com valores iniciais" [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Para inicializar uma variável de matriz usando um literal de matriz  
  
-   No `New` cláusula, ou quando você atribui o valor de matriz, forneça os valores dos elementos dentro de chaves (`{}`). O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz com elementos do tipo `Char`.  
  
     [!code-vb[VbVbalrArrays n º&16;](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     Após cada instrução é executada, a matriz que é criada tem um comprimento igual a 3, com elementos no índice 0 até índice 2 que contém os valores iniciais. Se você fornecer o limite superior e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior.  
  
     Observe que você não precisa especificar o limite superior do índice se você fornecer valores de elemento em um literal de matriz. Se nenhum limite superior for especificado, o tamanho da matriz é inferido com base no número de valores na matriz literal.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Para inicializar uma variável de matriz multidimensional usando literais de matriz  
  
-   Aninhar valores entre chaves (`{}`) entre chaves. Certifique-se de que os literais de matriz aninhada que todos inferir como matrizes do mesmo tipo e comprimento. O exemplo de código a seguir mostra vários exemplos de inicialização de matriz multidimensional.  
  
     [!code-vb[17 VbVbalrArrays](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   Explicitamente você pode especificar os limites da matriz, ou omiti-los e que o compilador inferir os limites de matriz com base nos valores do literal de matriz. Se você fornecer os limites superiores e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior de cada dimensão. O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz bidimensional com elementos do tipo`Short`  
  
     [!code-vb[VbVbalrArrays n º&18;](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     Após cada instrução é executada, a matriz criada contém seis elementos inicializados com índices `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, e `(1,2)`. Cada local da matriz contém o valor `10`.  
  
-   O exemplo a seguir itera em uma matriz multidimensional. Em um aplicativo de console do Windows que é escrito em Visual Basic, cole o código dentro de `Sub Main()` método. Os comentários do último mostram a saída.  
  
     [!code-vb[VbVbalrArrays&#31;](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Para inicializar uma variável de matriz denteada usando literais de matriz  
  
-   Aninhar valores de objeto entre chaves (`{}`). Embora você também pode aninhar literais de matriz que especificam matrizes de tamanhos diferentes, no caso de uma matriz denteada, certifique-se que os literais de matriz aninhados são colocados entre parênteses (`()`). Os parênteses forçam a avaliação dos literais de matriz aninhada e os conjuntos resultantes são usados como os valores iniciais da matriz denteada. O exemplo de código a seguir mostra dois exemplos de inicialização de matriz denteada.  
  
     [!code-vb[19 VbVbalrArrays](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   O exemplo a seguir itera em uma matriz denteada. Em um aplicativo de console do Windows que é escrito em Visual Basic, cole o código dentro de `Sub Main()` método.  Os último comentários no código mostram a saída.  
  
     [!code-vb[32 VbVbalrArrays](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
