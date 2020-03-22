---
title: Resolução de sobrecarga
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
ms.openlocfilehash: 84d52bbbfb34c2e5d67ed6a1810ab3e32fafda22
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266866"
---
# <a name="overload-resolution-visual-basic"></a>Resolução de sobrecarga (Visual Basic)
Quando o compilador Visual Basic encontra uma chamada para um procedimento definido em várias versões sobrecarregadas, o compilador deve decidir qual das sobrecargas chamar. Ele faz isso realizando as seguintes etapas:  
  
1. **Acessibilidade.** Elimina qualquer sobrecarga com um nível de acesso que impeça o código de chamada de chamá-lo.  
  
2. **Número de parâmetros.** Elimina qualquer sobrecarga que defina um número diferente de parâmetros do que são fornecidos na chamada.  
  
3. **Tipos de dados de parâmetros.** O compilador dá aos métodos de exemplo preferência sobre métodos de extensão. Se for encontrado qualquer método de instância que exija apenas a ampliação das conversões para corresponder à chamada do procedimento, todos os métodos de extensão serão descartados e o compilador continua apenas com os candidatos ao método de ocorrência. Se nenhum método de ocorrência for encontrado, ele continuará com métodos de instância e extensão.  
  
     Nesta etapa, elimina qualquer sobrecarga para a qual os tipos de dados dos argumentos de chamada não podem ser convertidos para os tipos de parâmetros definidos na sobrecarga.  
  
4. **Estreitando conversões.** Elimina qualquer sobrecarga que exija uma conversão estreita dos tipos de argumento de chamada para os tipos de parâmetros definidos. Isso é verdade se o interruptor de verificação `Off`de tipo[(Option Strict Statement)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)é `On` ou .  
  
5. **Pelo menos ampliando.** O compilador considera as sobrecargas restantes em pares. Para cada par, ele compara os tipos de dados dos parâmetros definidos. Se os tipos em uma das sobrecargas se expandirem para os tipos correspondentes no outro, o compilador elimina este último. Ou seja, retém a sobrecarga que requer a menor quantidade de alargamento.  
  
6. **Candidato único.** Ele continua considerando sobrecargas em pares até que apenas uma sobrecarga permaneça, e resolve a chamada para essa sobrecarga. Se o compilador não puder reduzir as sobrecargas a um único candidato, ele gerará um erro.  
  
 A ilustração a seguir mostra o processo que determina qual de um conjunto de versões sobrecarregadas a serem chamadas.  
  
 ![Diagrama de fluxo do processo de resolução de sobrecarga](./media/overload-resolution/determine-overloaded-version.gif "Resolução entre versões sobrecarregadas")
  
 O exemplo a seguir ilustra este processo de resolução de sobrecarga.  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 Na primeira chamada, o compilador elimina a primeira sobrecarga porque`Short`o tipo do primeiro argumento (`Byte`) se restringe ao tipo do parâmetro correspondente ( ). Em seguida, elimina a terceira sobrecarga porque cada`Short` `Single`tipo de argumento na segunda sobrecarga`Integer` (e ) aumenta para o tipo correspondente na terceira sobrecarga (e `Single`). A segunda sobrecarga requer menos ampliação, de modo que o compilador usa-o para a chamada.  
  
 Na segunda chamada, o compilador não pode eliminar nenhuma das sobrecargas com base no estreitamento. Elimina a terceira sobrecarga pelo mesmo motivo da primeira chamada, pois pode chamar a segunda sobrecarga com menos ampliação dos tipos de argumentos. No entanto, o compilador não pode resolver entre a primeira e a segunda sobrecargas. Cada um tem um tipo de parâmetro definido que`Byte` se `Short`amplia `Single` `Double`para o tipo correspondente no outro (para, mas para ). O compilador gera, portanto, um erro de resolução de sobrecarga.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Argumentos opcionais e paramarray sobrecarregados  
 Se duas sobrecargas de um procedimento tiverem assinaturas idênticas, exceto que o último parâmetro é declarado [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para esse procedimento da seguinte forma:  
  
|Se a chamada fornece o último argumento como|O compilador resolve a chamada para a sobrecarga declarando o último argumento como|  
|---|---|  
|Sem valor (argumento omitido)|`Optional`|  
|Um único valor|`Optional`|  
|Dois ou mais valores em uma lista separada por comma|`ParamArray`|  
|Uma matriz de qualquer comprimento (incluindo uma matriz vazia)|`ParamArray`|  
  
## <a name="see-also"></a>Confira também

- [Parâmetros opcionais](./optional-parameters.md)
- [Matrizes de parâmetros](./parameter-arrays.md)
- [Sobrecarga de procedimento](./procedure-overloading.md)
- [Solucionando problemas de procedimentos](./troubleshooting-procedures.md)
- [Como definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)
- [Como chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)
- [Como sobrecarregar um procedimento que usa parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md)
- [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Métodos de extensão](./extension-methods.md)
