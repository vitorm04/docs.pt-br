---
title: Resolução de sobrecarga (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- overload resolution
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedure overloading [Visual Basic], overload resolution
- signatures [Visual Basic], procedure
- overloads [Visual Basic], resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e62560d853c95bc4bba6ba829d8579ee4388858e
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="overload-resolution-visual-basic"></a>Resolução de sobrecarga (Visual Basic)
Quando o compilador do Visual Basic encontra uma chamada para um procedimento que é definido em várias versões sobrecarregadas, o compilador deve decidir qual das sobrecargas para chamar. Ele faz isso executando as seguintes etapas:  
  
1.  **Acessibilidade.** Elimina qualquer sobrecarregamento com um nível de acesso que impede que o código de chamada chamando-o.  
  
2.  **Número de parâmetros.** Elimina qualquer sobrecarregamento que define um número diferente de parâmetros que são fornecidos na chamada.  
  
3.  **Tipos de dados do parâmetro.** O compilador dá preferência de métodos de instância sobre métodos de extensão. Se qualquer método de instância que requer somente conversões para corresponder a chamada de procedimento de expansão, todos os métodos de extensão são descartados e o compilador continua com apenas os candidatos de método de instância. Se esse método de instância não for encontrado, ele continuará com a instância e métodos de extensão.  
  
     Nesta etapa, ela elimina qualquer sobrecarga para o qual os tipos de dados dos argumentos de chamada não podem ser convertidos para tipos de parâmetro definido na sobrecarga.  
  
4.  **Conversões de estreitamento.** Elimina qualquer sobrecarregamento que requer uma conversão de estreitamento dos tipos de argumento de chamada para os tipos de parâmetro definido. Isso é verdadeiro se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `On` ou `Off`.  
  
5.  **Mínimo de ampliação.** O compilador considera as sobrecargas restantes em pares. Para cada par, ele compara os tipos de dados dos parâmetros definidos. Se os tipos em uma das sobrecargas todos ampliam para os tipos correspondentes no outro, o compilador elimina o último. Ou seja, ele retém a sobrecarga que exige o mínimo de ampliação.  
  
6.  **Candidato único.** Continua considerando sobrecargas em pares até que somente uma sobrecarga permanece e resolve a chamada para essa sobrecarga. Se o compilador não pode reduzir as sobrecargas a um candidato único, ele gera um erro.  
  
 A ilustração a seguir mostra o processo que determina que um conjunto de versões sobrecarregadas para chamar.  
  
 ![Diagrama de fluxo do processo de resolução de sobrecarga](./media/overloadres.gif "OverloadRes")  
Resolução entre versões sobrecarregadas  
  
 O exemplo a seguir ilustra esse processo de resolução de sobrecarga.  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 Na primeira chamada, o compilador elimina a primeira sobrecarga porque o tipo do primeiro argumento (`Short`) estreita ao tipo do parâmetro correspondente (`Byte`). Em seguida, elimina o terceiro sobrecarregamento porque cada tipo de argumento na segunda sobrecarga (`Short` e `Single`) será ampliada para o tipo correspondente no terceiro sobrecarregamento (`Integer` e `Single`). A segunda sobrecarga requer menos widening, para que o compilador usa para a chamada.  
  
 A segunda chamada, o compilador não pode eliminar qualquer uma das sobrecargas com base na restrição. Elimina o terceiro sobrecarregamento pela mesma razão que na primeira chamada, porque ele pode chamar a segunda sobrecarga com menos de ampliação dos tipos de argumento. No entanto, o compilador não pode resolver entre as primeiro e segundo sobrecargas. Cada um tem um tipo definido de parâmetro que será ampliada para o tipo correspondente no outro (`Byte` para `Short`, mas `Single` para `Double`). Portanto, o compilador gerará um erro de resolução de sobrecarga.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Sobrecarregado opcional e argumentos ParamArray  
 Se duas sobrecargas de um procedimento tenham assinaturas idênticas, exceto que o último parâmetro é declarado [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para o procedimento como a seguir:  
  
|Se a chamada fornecer o último argumento como|O compilador resolve a chamada para a sobrecarga declarando o último argumento como|  
|---|---|  
|Nenhum valor (argumento omitido)|`Optional`|  
|um único valor|`Optional`|  
|Dois ou mais valores em uma lista separada por vírgulas|`ParamArray`|  
|Uma matriz de qualquer comprimento (incluindo uma matriz vazia)|`ParamArray`|  
  
## <a name="see-also"></a>Consulte também  
 [Parâmetros Opcionais](./optional-parameters.md)  
 [Matrizes de Parâmetros](./parameter-arrays.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Solução de problemas de Procedimentos](./troubleshooting-procedures.md)  
 [Como definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)  
 [Como chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)  
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Considerações sobre Procedimentos de Sobrecarga](./considerations-in-overloading-procedures.md)  
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Métodos de Extensão](./extension-methods.md)
