---
title: Resolução de sobrecarga (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
ms.openlocfilehash: 734cc521fe2e8b7af5ca594ced8c3a0a22603af7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525944"
---
# <a name="overload-resolution-visual-basic"></a>Resolução de sobrecarga (Visual Basic)
Quando o compilador do Visual Basic encontra uma chamada para um procedimento que é definido em várias versões sobrecarregadas, o compilador deve decidir qual das sobrecargas para chamar. Ele faz isso executando as seguintes etapas:  
  
1.  **Acessibilidade.** Ele elimina qualquer sobrecarga com um nível de acesso que impede que o código de chamada chamando-o.  
  
2.  **Número de parâmetros.** Ele elimina qualquer sobrecarga que define um número diferente de parâmetros que são fornecidos na chamada.  
  
3.  **Tipos de dados do parâmetro.** O compilador dá preferência de métodos de instância sobre métodos de extensão. Se qualquer método de instância for encontrado que requer somente conversões de acordo com a chamada de procedimento de expansão, todos os métodos de extensão são descartados e o compilador continua com apenas os candidatos a método de instância. Se nenhum método de instância desse tipo for encontrado, ele continua com a instância e métodos de extensão.  
  
     Nesta etapa, ele elimina qualquer sobrecarga para o qual os tipos de dados dos argumentos de chamada não podem ser convertidos para os tipos de parâmetro definidos na sobrecarga.  
  
4.  **Conversões de estreitamento.** Ele elimina qualquer sobrecarga que requer uma conversão redutora entre os tipos de argumento de chamada para os tipos de parâmetro definidas. Isso é verdadeiro se a verificação de tipo alternar ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `On` ou `Off`.  
  
5.  **Mínimo de ampliação.** O compilador considera as sobrecargas restantes em pares. Para cada par, ele compara os tipos de dados dos parâmetros definidos. Se os tipos em uma das sobrecargas todos são ampliados com os tipos correspondentes no outro, o compilador elimina o último. Ou seja, ele retém a sobrecarga que exige o mínimo de ampliação.  
  
6.  **Única de candidato.** Ele continua considerando sobrecargas em pares até que apenas uma sobrecarregam permanece, além de resolver a chamada para essa sobrecarga. Se o compilador não é possível reduzir as sobrecargas a um candidato único, ele gera um erro.  
  
 A ilustração a seguir mostra o processo que determina que um conjunto de versões sobrecarregadas para chamar.  
  
 ![Diagrama de fluxo do processo de resolução de sobrecarga](./media/overloadres.gif "OverloadRes")  
Resolução entre versões sobrecarregadas  
  
 O exemplo a seguir ilustra esse processo de resolução de sobrecarga.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 Na primeira chamada, o compilador elimina a primeira sobrecarga porque o tipo do primeiro argumento (`Short`) restringe-se para o tipo do parâmetro correspondente (`Byte`). Em seguida, ele elimina a terceira sobrecarga porque cada tipo de argumento na segunda sobrecarga (`Short` e `Single`) é ampliado para o tipo correspondente no terceiro sobrecarregamento (`Integer` e `Single`). A segunda sobrecarga requer menos alargamento, portanto, o compilador usa para a chamada.  
  
 Na segunda chamada, o compilador não pode eliminar qualquer uma das sobrecargas com base na restrição. Elimina a terceira sobrecarga pela mesma razão que na primeira chamada, pois ele pode chamar a segunda sobrecarga com menos alargamento dos tipos de argumento. No entanto, o compilador não pode resolver entre as primeiros e segunda sobrecargas. Cada um tem um tipo de parâmetro definidas se expande para o tipo correspondente no outro (`Byte` à `Short`, mas `Single` para `Double`). Portanto, o compilador gera um erro de resolução de sobrecarga.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Sobrecarregado opcional e argumentos ParamArray  
 Se duas sobrecargas de um procedimento possuem assinaturas idênticas, exceto pelo fato de que o último parâmetro é declarado [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para o procedimento como a seguir:  
  
|Se a chamada fornece o último argumento como|O compilador resolve a chamada para a sobrecarga declarando o último argumento como|  
|---|---|  
|Nenhum valor (argumento omitido)|`Optional`|  
|Um único valor|`Optional`|  
|Dois ou mais valores em uma lista separada por vírgulas|`ParamArray`|  
|Uma matriz de qualquer comprimento (incluindo uma matriz vazia)|`ParamArray`|  
  
## <a name="see-also"></a>Consulte também
- [Parâmetros Opcionais](./optional-parameters.md)
- [Matrizes de Parâmetros](./parameter-arrays.md)
- [Sobrecarga de Procedimento](./procedure-overloading.md)
- [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)
- [Como: Definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)
- [Como: Chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)
- [Como: Sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Como: Sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)
- [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Métodos de Extensão](./extension-methods.md)
