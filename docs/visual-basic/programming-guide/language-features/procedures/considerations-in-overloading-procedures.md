---
title: "Considerações sobre procedimentos de sobrecarga (Visual Basic) | Documentos do Microsoft"
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
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
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
ms.openlocfilehash: aa20cf367fba157f88afd861a4799540dcdecde1
ms.lasthandoff: 03/13/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>Considerações sobre procedimentos de sobrecarga (Visual Basic)
Quando você sobrecarrega um procedimento, você deve usar um outro *assinatura* para cada versão sobrecarregada. Isso geralmente significa que cada versão deve especificar uma lista de parâmetros diferentes. Para obter mais informações, consulte "Assinatura diferente" em [sobrecarga de procedimento](./procedure-overloading.md).  
  
 Você pode sobrecarregar uma `Function` procedimento com uma `Sub` procedimento e vice-versa, que tenham assinaturas diferentes. Duas sobrecargas não podem diferir somente em que um tem um valor de retorno e o outro não.  
  
 Você pode sobrecarregar uma propriedade da mesma maneira que sobrecarrega um procedimento e com as mesmas restrições. No entanto, você não pode sobrecarregar um procedimento com uma propriedade, ou vice-versa.  
  
## <a name="alternatives-to-overloaded-versions"></a>Alternativas para versões sobrecarregadas  
 Às vezes, você tem alternativas para versões sobrecarregadas, particularmente quando a presença dos argumentos é opcional ou seu número é variável.  
  
 Tenha em mente que argumentos opcionais não são necessariamente suportados por todos os idiomas, e matrizes de parâmetros são limitadas a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Se você estiver escrevendo um procedimento que é provável de ser chamado a partir do código escrito em qualquer um dos vários idiomas diferentes, versões sobrecarregadas oferecem a maior flexibilidade.  
  
### <a name="overloads-and-optional-arguments"></a>Sobrecargas e argumentos opcionais  
 Quando o código de chamada pode opcionalmente fornecer ou omitir um ou mais argumentos, você pode definir várias versões sobrecarregados ou usar parâmetros opcionais.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quando usar versões sobrecarregadas  
 Você pode considerar definir uma série de versões sobrecarregadas nos seguintes casos:  
  
-   A lógica no código do procedimento é significativamente diferente dependendo se o código de chamada fornece um argumento opcional ou não.  
  
-   O código do procedimento não pode testar com confiança se o código de chamada forneceu um argumento opcional. Esse é o caso, por exemplo, se não houver nenhum candidato possível para um valor padrão que o código de chamada pode não ser esperado para fornecer.  
  
#### <a name="when-to-use-optional-parameters"></a>Quando usar parâmetros opcionais  
 Talvez você prefira um ou mais parâmetros opcionais nos seguintes casos:  
  
-   A única ação necessária quando o código de chamada não fornece um argumento opcional é definir o parâmetro como um valor padrão. Nesse caso, o código do procedimento pode ser menos complicado se você definir uma única versão com um ou mais `Optional` parâmetros.  
  
 Para obter mais informações, consulte [parâmetros opcionais](./optional-parameters.md).  
  
### <a name="overloads-and-paramarrays"></a>Sobrecargas e ParamArrays  
 Quando o código de chamada pode passar um número variável de argumentos, você pode definir várias versões sobrecarregados ou usar uma matriz de parâmetros.  
  
#### <a name="when-to-use-overloaded-versions"></a>Quando usar versões sobrecarregadas  
 Você pode considerar definir uma série de versões sobrecarregadas nos seguintes casos:  
  
-   Você sabe que o código de chamada nunca passa mais do que um pequeno número de valores para a matriz de parâmetros.  
  
-   A lógica no código do procedimento é significativamente diferente dependendo de quantos valores o código de chamada passa.  
  
-   O código de chamada pode passar valores de diferentes tipos de dados.  
  
#### <a name="when-to-use-a-parameter-array"></a>Quando usar uma matriz de parâmetros  
 Você é mais bem atendidas por um `ParamArray` parâmetro nos seguintes casos:  
  
-   Não é possível prever quantos valores o código de chamada pode passar para a matriz de parâmetros, e pode ser um número grande.  
  
-   A lógica do procedimento presta-se à iteração em todos os valores que o código de chamada passa, executando essencialmente as mesmas operações em cada valor.  
  
 Para obter mais informações, consulte [matrizes de parâmetros](./parameter-arrays.md).  
  
## <a name="implicit-overloads-for-optional-parameters"></a>Sobrecargas implícitas para parâmetros opcionais  
 Um procedimento com um [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetro é equivalente a dois procedimentos sobrecarregados, um com o parâmetro opcional e outro sem ele. Você não pode sobrecarregar tal procedimento com uma lista de parâmetros correspondente a um deles. As declarações a seguir ilustram isso.  
  
 [!code-vb[VbVbcnProcedures&#58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 Para um procedimento com mais de um parâmetro opcional, há um conjunto de sobrecargas implícitas, acessou por lógica semelhante ao exemplo anterior.  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>Sobrecargas implícitas para um parâmetro ParamArray  
 O compilador considera um procedimento com um [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parâmetro deverá ter um número infinito de sobrecargas, com diferenças no que o código de chamada passa para a matriz de parâmetros, da seguinte maneira:  
  
-   Uma sobrecarga para quando o código de chamada não fornece um argumento para o`ParamArray`  
  
-   Uma sobrecarga para quando o código de chamada fornece uma matriz unidimensional do `ParamArray` tipo de elemento  
  
-   Para cada inteiro positivo, uma sobrecarga para quando o código de chamada fornece esse número de argumentos, cada um a `ParamArray` tipo de elemento  
  
 As seguintes declarações ilustram essas sobrecargas implícitas.  
  
 [!code-vb[VbVbcnProcedures&#68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 Você não pode sobrecarregar tal procedimento com uma lista de parâmetros que usa uma matriz unidimensional para a matriz de parâmetros. No entanto, você pode usar as assinaturas das outras sobrecargas implícitas. As declarações a seguir ilustram isso.  
  
 [!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>Programação sem tipo como uma alternativa para sobrecarga  
 Se você quiser permitir que o código de chamada passe diferentes tipos de dados para um parâmetro, uma abordagem alternativa é programação sem tipo. Você pode definir o tipo de verificação alternar para `Off` utilizando o [instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou o [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) opção de compilador. Em seguida, você não precisa declarar o tipo de dados do parâmetro. No entanto, essa abordagem tem as seguintes desvantagens comparadas à sobrecarga:  
  
-   Programação sem tipo produz código de execução menos eficiente.  
  
-   O procedimento deve testar cada tipo de dados que ele prevê que está sendo passada.  
  
-   O compilador não pode sinalizar um erro se o código de chamada passa um tipo de dados que o procedimento não oferece suporte.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Procedimentos de solução de problemas](./troubleshooting-procedures.md)   
 [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)   
 [Como: sobrecarregar um procedimento que recebe parâmetros opcionais](./how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Resolução de sobrecarga](./overload-resolution.md)   
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)
