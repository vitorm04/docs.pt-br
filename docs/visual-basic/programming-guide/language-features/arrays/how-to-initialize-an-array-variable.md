---
title: 'Como: Inicializar uma variável de matriz no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: 4aa783d6179c72760a12d0259d587b5b38bb9140
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053646"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>Como: Inicializar uma variável de matriz no Visual Basic
Inicializar uma variável de matriz incluindo um literal de matriz em um `New` cláusula e especificando os valores iniciais da matriz. Você pode especificar o tipo ou permitir que ele seja inferido dos valores no literal de matriz. Para obter mais informações sobre como o tipo é inferido, consulte "Preencher uma matriz com valores iniciais" em [matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>Para inicializar uma variável de matriz usando um literal de matriz  
  
- No `New` cláusula, ou quando você atribui o valor da matriz, forneça os valores de elemento entre chaves (`{}`). O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz com elementos do tipo `Char`.  
  
     [!code-vb[VbVbalrArrays#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#16)]  
  
     Depois de cada instrução é executada, a matriz criada tem um comprimento igual a 3, com elementos no índice 0 até índice 2 que contém os valores iniciais. Se você fornecer o limite superior e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior.  
  
     Observe que você não precisa especificar o limite superior do índice se você fornecer valores de elemento em um literal de matriz. Se nenhum limite superior é especificado, o tamanho da matriz é inferido com base no número de valores no literal de matriz.  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>Para inicializar uma variável de matriz multidimensional usando literais de matriz  
  
- Aninhar valores dentro de chaves (`{}`) entre chaves. Verifique se os literais de matriz aninhados que todos inferidos como matrizes do mesmo tipo e comprimento. O exemplo de código a seguir mostra vários exemplos de inicialização de matriz multidimensional.  
  
     [!code-vb[VbVbalrArrays#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#17)]  
  
- Você pode explicitamente especificam os limites de matriz, ou omiti-los e fazer com que o compilador inferir os limites da matriz com base nos valores no literal de matriz. Se você fornecer os limites superiores e os valores, você deve incluir um valor para cada elemento do índice 0 até o limite superior de cada dimensão. O exemplo a seguir mostra várias maneiras de declarar, criar e inicializar uma variável para conter uma matriz bidimensional com elementos do tipo `Short`  
  
     [!code-vb[VbVbalrArrays#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#18)]  
  
     Depois de cada instrução é executada, a matriz criada contém seis elementos inicializados que têm índices `(0,0)`, `(0,1)`, `(0,2)`, `(1,0)`, `(1,1)`, e `(1,2)`. Cada local da matriz contém o valor `10`.  
  
- O exemplo a seguir itera por meio de uma matriz multidimensional. Em um aplicativo de console do Windows que é escrito em Visual Basic, cole o código dentro de `Sub Main()` método. Os últimos comentários mostram a saída.  
  
     [!code-vb[VbVbalrArrays#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#31)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>Para inicializar uma variável de matriz denteada usando literais de matriz  
  
- Aninhar valores de objeto dentro de chaves (`{}`). Embora você também possa aninhar literais de matriz que especificam matrizes de comprimentos diferentes, no caso de uma matriz denteada, certifique-se de que os literais de matriz aninhados estão entre parênteses (`()`). Os parênteses forçam a avaliação de literais de matriz aninhadas e as matrizes resultantes são usadas como os valores iniciais da matriz denteada. O exemplo de código a seguir mostra dois exemplos de inicialização de matriz denteada.  
  
     [!code-vb[VbVbalrArrays#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#19)]  
  
- O exemplo a seguir itera por meio de uma matriz denteada. Em um aplicativo de console do Windows que é escrito em Visual Basic, cole o código dentro de `Sub Main()` método.  Os últimos comentários no código mostram a saída.  
  
     [!code-vb[VbVbalrArrays#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrArrays/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>Consulte também

- [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Solução de problemas de matrizes](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
