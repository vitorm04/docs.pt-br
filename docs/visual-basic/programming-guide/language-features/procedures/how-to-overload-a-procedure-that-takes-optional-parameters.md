---
title: Como sobrecarregar um procedimento que usa parâmetros opcionais
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
ms.openlocfilehash: 4d31980e4b968cff274091ba4f307dffddab1100
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350860"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Como sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)
Se um procedimento tiver um ou mais parâmetros [opcionais](../../../../visual-basic/language-reference/modifiers/optional.md) , você não poderá definir uma versão sobrecarregada que corresponda a qualquer uma de suas sobrecargas implícitas. Para obter mais informações, consulte "sobrecargas implícitas para parâmetros opcionais" em [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Um parâmetro opcional  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Para sobrecarregar um procedimento que recebe um parâmetro opcional  
  
1. Escreva uma instrução de declaração de `Sub` ou `Function` que inclua o parâmetro opcional na lista de parâmetros. Não use a palavra-chave `Optional` nesta versão sobrecarregada.  
  
2. Preceda a palavra-chave `Sub` ou `Function` com a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .  
  
3. Escreva o código de procedimento que deve ser executado quando o código de chamada fornecer o argumento opcional.  
  
4. Encerre o procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.  
  
5. Escreva uma segunda declaração de declaração que seja idêntica à primeira declaração, exceto que ela não inclui o parâmetro opcional na lista de parâmetros.  
  
6. Escreva o código de procedimento que deve ser executado quando o código de chamada não fornecer o argumento opcional. Encerre o procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.  
  
     O exemplo a seguir mostra um procedimento definido com um parâmetro opcional, um conjunto equivalente de dois procedimentos sobrecarregados e, por fim, exemplos de versões sobrecarregadas válidas e válidas.  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a>Vários parâmetros opcionais  
 Para um procedimento com mais de um parâmetro opcional, normalmente você precisa de mais de duas versões sobrecarregadas. Por exemplo, se houver dois parâmetros opcionais e o código de chamada puder fornecer ou omitir cada um independente do outro, você precisará de quatro versões sobrecarregadas, uma para cada combinação possível de argumentos fornecidos.  
  
 À medida que aumenta o número de parâmetros opcionais, a complexidade da sobrecarga aumenta. A menos que algumas combinações de argumentos fornecidos não sejam aceitáveis, para N parâmetros opcionais, você precisará de 2 ^ N versões sobrecarregadas. Dependendo da natureza do procedimento, você pode achar que a clareza da lógica justifica o esforço extra de definir todas as versões sobrecarregadas.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Para sobrecarregar um procedimento que usa mais de um parâmetro opcional  
  
1. Determine quais combinações de argumentos opcionais fornecidos são aceitáveis para a lógica do procedimento. Uma combinação inaceitável pode surgir se um parâmetro opcional depender de outro. Por exemplo, se um parâmetro aceitar o nome de uma pessoa e outro aceitar a idade da pessoa, uma combinação de argumentos que fornece a idade, mas omitir o nome, será inaceitável.  
  
2. Para cada combinação aceitável de argumentos opcionais fornecidos, escreva uma instrução de declaração de `Sub` ou de `Function` que define a lista de parâmetros correspondente. Não use a palavra-chave `Optional`.  
  
3. Em cada declaração, preceda a palavra-chave `Sub` ou `Function` com a palavra-chave [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .  
  
4. Após cada declaração, escreva o código do procedimento que deve ser executado quando o código de chamada fornecer uma lista de argumentos correspondente à lista de parâmetros da declaração.  
  
5. Encerre cada procedimento com a instrução `End Sub` ou `End Function`, conforme apropriado.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Parâmetros Opcionais](./optional-parameters.md)
- [Matrizes de Parâmetros](./parameter-arrays.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Como definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)
- [Como chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)
- [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Resolução de Sobrecarga](./overload-resolution.md)
