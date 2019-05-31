---
title: 'Como: Sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 4374a229392d51b67c99210da91ae05dd3342e96
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66424063"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Como: Sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)
Se um procedimento tem um ou mais [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetros, você não pode definir uma versão sobrecarregada de correspondência de qualquer uma de suas sobrecargas implícitas. Para obter mais informações, consulte "Sobrecargas implícitas para parâmetros opcionais" em [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Um parâmetro opcional  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Para sobrecarregar um procedimento que recebe um parâmetro opcional  
  
1. Gravar uma `Sub` ou `Function` instrução de declaração que inclua o parâmetro opcional na lista de parâmetros. Não use o `Optional` palavra-chave nesta versão sobrecarregada.  
  
2. Preceda a `Sub` ou `Function` palavra-chave com o [sobrecarrega](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.  
  
3. Escreva o código de procedimento que deve ser executado quando o código de chamada fornece o argumento opcional.  
  
4. Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
5. Escreva uma segunda instrução de declaração é idêntica à primeira declaração, exceto que ele não inclui o parâmetro opcional na lista de parâmetros.  
  
6. Escreva o código de procedimento que deve ser executado quando o código de chamada não fornece o argumento opcional. Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
     O exemplo a seguir mostra um procedimento definido com um parâmetro opcional, um conjunto equivalente de dois procedimentos sobrecarregados e, finalmente, exemplos de versões sobrecarregadas válidos e inválidos.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Vários parâmetros opcionais  
 Para obter um procedimento com mais de um parâmetro opcional, você normalmente precisa de mais de duas versões sobrecarregadas. Por exemplo, se houver dois parâmetros opcionais e o código de chamada pode fornecer ou omitir cada um deles independentemente da outra, você precisa de quatro versões sobrecarregadas, uma para cada combinação possível de argumentos fornecidos.  
  
 À medida que aumenta o número de parâmetros opcionais, aumenta a complexidade do sobrecarregamento. A menos que algumas combinações de argumentos fornecidos não forem aceitáveis, para parâmetros opcionais de N, você precisa 2 ^ versões sobrecarregadas de N. Dependendo da natureza do procedimento, você pode achar que a clareza da lógica justifica o esforço extra de definir todas as versões sobrecarregadas.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Para sobrecarregar um procedimento que usa mais de um parâmetro opcional  
  
1. Determine quais combinações de argumentos opcionais fornecidos são aceitáveis para a lógica do procedimento. Uma combinação inaceitável pode surgir se um parâmetro opcional depende de outro. Por exemplo, se um parâmetro aceita um nome de uma pessoa e outro aceita a idade da pessoa, uma combinação de argumentos fornecendo a idade mas omitindo o nome é inaceitável.  
  
2. Para cada combinação aceitável de argumentos opcionais fornecidos, escreva uma `Sub` ou `Function` instrução de declaração que define a lista de parâmetro correspondente. Não use o `Optional` palavra-chave.  
  
3. Em cada declaração, preceda a `Sub` ou `Function` palavra-chave com o [sobrecarrega](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.  
  
4. Após cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece uma lista de argumentos correspondentes à lista de parâmetros da declaração.  
  
5. Encerrar cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Matrizes de Parâmetros](./parameter-arrays.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Como: Definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)
- [Como: Chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)
- [Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Resolução de Sobrecarga](./overload-resolution.md)
