---
title: "Resolução de sobrecarga (Visual Basic) | Documentos do Microsoft"
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
- Visual Basic code, procedures
- overload resolution
- procedures, overloading
- procedures, calling
- procedure overloading, overload resolution
- signatures, procedure
- overloads, resolution
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 0de3a603fa84a72018a566f6e7182b45e53ec89e
ms.lasthandoff: 03/13/2017

---
# <a name="overload-resolution-visual-basic"></a>Resolução de sobrecarga (Visual Basic)
Quando o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador encontra uma chamada para um procedimento que é definido em várias versões sobrecarregadas, o compilador deve decidir qual das sobrecargas para chamar. Ele faz isso executando as seguintes etapas:  
  
1.  **Acessibilidade.** Elimina qualquer sobrecarregamento com um nível de acesso que impede o código de chamada de chamá-lo.  
  
2.  **Número de parâmetros.** Elimina qualquer sobrecarregamento que define um número diferente de parâmetros que são fornecidos na chamada.  
  
3.  **Tipos de dados do parâmetro.** O compilador dá preferência de métodos de instância sobre métodos de extensão. Se qualquer método de instância for encontrado que requer somente conversões para coincidir com a chamada de procedimento de expansão, todos os métodos de extensão são descartados e o compilador continua com apenas os candidatos a método de instância. Se esse método de instância não for encontrado, ele continua com métodos de extensão e de instância.  
  
     Nesta etapa, ele elimina qualquer sobrecarregamento para o qual os tipos de dados dos argumentos de chamada não podem ser convertidos para os tipos de parâmetro definidos no sobrecarregamento.  
  
4.  **Conversões de estreitamento.** Elimina qualquer sobrecarregamento que exige uma conversão de restrição dos tipos de argumento de chamada para os tipos de parâmetro definido. Isso é verdadeiro se a verificação de tipo muda ([instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) é `On` ou `Off`.  
  
5.  **Alargamento mínimo.** O compilador considera as sobrecargas restantes em pares. Para cada par, ele compara os tipos de dados dos parâmetros definidos. Se os tipos em uma das sobrecargas de todos os ampliam para os tipos correspondentes no outro, o compilador elimina o último. Ou seja, ele retém o sobrecarregamento que exige o mínimo de ampliação.  
  
6.  **Único candidato.** Continua considerando sobrecargas em pares até que apenas uma sobrecarga permanece e resolve a chamada para essa sobrecarga. Se o compilador não pode reduzir as sobrecargas para uma única candidata, ele gera um erro.  
  
 A ilustração a seguir mostra o processo que determina que um conjunto de versões sobrecarregadas para chamar.  
  
 ![Diagrama de fluxo do processo de resolução de sobrecarga](./media/overloadres.gif "OverloadRes")  
Resolução entre versões sobrecarregadas  
  
 O exemplo a seguir ilustra esse processo de resolução de sobrecarga.  
  
 [!code-vb[VbVbcnProcedures&#62;](./codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#63;](./codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 Na primeira chamada, o compilador elimina a primeira sobrecarga porque o tipo do primeiro argumento (`Short`) estreita ao tipo do parâmetro correspondente (`Byte`). Então elimina o terceiro sobrecarregamento porque cada tipo de argumento na segunda sobrecarga (`Short` e `Single`) amplia-se para o tipo correspondente no terceiro sobrecarregamento (`Integer` e `Single`). O segundo sobrecarregamento requer menos alargamento, então o compilador usa-o para a chamada.  
  
 Na segunda chamada, o compilador não pode eliminar qualquer uma das sobrecargas com base na restrição. Elimina o terceiro sobrecarregamento pela mesma razão que na primeira chamada, pois ele pode chamar o segundo sobrecarregamento com menos alargamento de tipos de argumento. No entanto, o compilador não pode resolver entre as primeira e o segunda sobrecargas. Cada um tem um tipo definido de parâmetro que amplia para o tipo correspondente no outro (`Byte` para `Short`, mas `Single` para `Double`). Portanto, o compilador gera um erro de resolução de sobrecarga.  
  
## <a name="overloaded-optional-and-paramarray-arguments"></a>Sobrecarregado opcional e argumentos ParamArray  
 Se duas sobrecargas de um procedimento possuem assinaturas idênticas exceto que o último parâmetro é declarado [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para o procedimento como se segue:  
  
|Se a chamada fornecer o último argumento como|O compilador resolve a chamada ao sobrecarregamento declarando o último argumento como|  
|---|---|  
|Nenhum valor (argumento omitido)|`Optional`|  
|Um único valor|`Optional`|  
|Dois ou mais valores em uma lista separada por vírgulas|`ParamArray`|  
|Uma matriz de qualquer comprimento (incluindo uma matriz vazia)|`ParamArray`|  
  
## <a name="see-also"></a>Consulte também  
 [Parâmetros opcionais](./optional-parameters.md)   
 [Matrizes de parâmetros](./parameter-arrays.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Procedimentos de solução de problemas](./troubleshooting-procedures.md)   
 [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)   
 [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md)   
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Métodos de Extensão](./extension-methods.md)
