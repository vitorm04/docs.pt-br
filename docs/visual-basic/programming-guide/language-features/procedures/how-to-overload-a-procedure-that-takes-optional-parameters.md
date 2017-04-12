---
title: "Como: sobrecarregar um procedimento que recebe parâmetros opcionais (Visual Basic) | Documentos do Microsoft"
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
- procedures, parameters
- procedure overloading, optional parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: 17
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
ms.openlocfilehash: 5265ef82cdb13107447fa516bb98735180ac4a8d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a>Como sobrecarregar um procedimento que usa parâmetros opcionais (Visual Basic)
Se um procedimento possui um ou mais [opcional](../../../../visual-basic/language-reference/modifiers/optional.md) parâmetros, você não pode definir uma versão sobrecarregada coincidindo com qualquer uma de suas sobrecargas implícitas. Para obter mais informações, consulte "Sobrecargas implícitas para parâmetros opcionais" em [considerações sobre procedimentos de sobrecarga](./considerations-in-overloading-procedures.md).  
  
## <a name="one-optional-parameter"></a>Um parâmetro opcional  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a>Para sobrecarregar um procedimento que recebe um parâmetro opcional  
  
1.  Escrever um `Sub` ou `Function` declaração que inclua o parâmetro opcional na lista de parâmetros. Não use o `Optional` palavra-chave nesta versão sobrecarregada.  
  
2.  Preceder o `Sub` ou `Function` palavra-chave com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.  
  
3.  Escreva o código de procedimento que deve executar quando o código de chamada fornece o argumento opcional.  
  
4.  Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
5.  Escreva uma segunda declaração é idêntica à primeira, exceto que ele não inclui o parâmetro opcional na lista de parâmetros.  
  
6.  Escreva o código de procedimento deve ser executado quando o código de chamada não fornecer o argumento opcional. Termine o procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
     O exemplo a seguir mostra um procedimento definido com um parâmetro opcional, um conjunto equivalente de dois procedimentos sobrecarregados e finalmente exemplos de versões sobrecarregadas válidos e inválidos.  
  
     [!code-vb[VbVbcnProcedures&#59;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a>Vários parâmetros opcionais  
 Para um procedimento com mais de um parâmetro opcional, você normalmente precisa de mais de duas versões sobrecarregadas. Por exemplo, se houver dois parâmetros opcionais, e o código de chamada pode fornecer ou omitir cada um deles independentemente uns dos outros, você precisa de quatro versões sobrecarregadas, uma para cada combinação possível de argumentos fornecidos.  
  
 Como o número de parâmetros opcionais aumenta, aumenta a complexidade do sobrecarregamento. A menos que algumas combinações de argumentos fornecidos não sejam aceitáveis, para parâmetros opcionais de N é necessário 2 ^ N versões sobrecarregadas. Dependendo da natureza do procedimento, você pode achar que a clareza da lógica justifica o esforço extra de definir todas as versões sobrecarregadas.  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a>Para sobrecarregar um procedimento que recebe mais de um parâmetro opcional  
  
1.  Determine quais combinações de argumentos opcionais fornecidos são aceitáveis à lógica do procedimento. Uma combinação inaceitável pode surgir se um parâmetro opcional depende de outro. Por exemplo, se um parâmetro aceita o nome do cônjuge e outro aceita a idade do cônjuge, uma combinação de argumentos fornecendo a idade mas omitindo o nome é inaceitável.  
  
2.  Para cada combinação aceitável de argumentos opcionais fornecidos, escreva uma `Sub` ou `Function` declaração que define a lista de parâmetros correspondente. Não use o `Optional` palavra-chave.  
  
3.  Em cada declaração, preceda o `Sub` ou `Function` palavra-chave com o [sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md) palavra-chave.  
  
4.  Seguindo cada declaração, escreva o código de procedimento que deve ser executado quando o código de chamada fornece uma lista de argumentos correspondente à lista de parâmetros da declaração.  
  
5.  Termine cada procedimento com o `End Sub` ou `End Function` instrução conforme apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Parâmetros opcionais](./optional-parameters.md)   
 [Matrizes de parâmetros](./parameter-arrays.md)   
 [Sobrecarga de procedimento](./procedure-overloading.md)   
 [Procedimentos de solução de problemas](./troubleshooting-procedures.md)   
 [Como: definir várias versões de um procedimento](./how-to-define-multiple-versions-of-a-procedure.md)   
 [Como: chamar um procedimento sobrecarregado](./how-to-call-an-overloaded-procedure.md)   
 [Como: sobrecarregar um procedimento que recebe um número indefinido de parâmetros](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Resolução de Sobrecarga](./overload-resolution.md)
