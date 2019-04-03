---
title: Passando argumentos por valor e por referência (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: c23ca51322f57dc13a85c3ea94e0d335dc50ca13
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830351"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Passando argumentos por valor e por referência (Visual Basic)
No Visual Basic, você pode passar um argumento para um procedimento *pelo valor* ou *por referência*. Isso é conhecido como o *mecanismo de passagem*, e determina se o procedimento pode modificar o elemento de programação subjacente do argumento no código de chamada. A declaração de procedimento determina o mecanismo de passagem para cada parâmetro, especificando o [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave.  
  
## <a name="distinctions"></a>Distinções  
 Ao passar um argumento para um procedimento, esteja ciente das várias distinções diferentes que interagem entre si:  
  
-   Se o elemento de programação subjacente é modificável ou não modificáveis  
  
-   Se o argumento em si é modificável ou não modificáveis  
  
-   Se o argumento está sendo passado por valor ou por referência  
  
-   Se o tipo de dados de argumento é um tipo de valor ou um tipo de referência  
  
 Para obter mais informações, consulte [diferenças entre modificáveis e não modificáveis argumentos](./differences-between-modifiable-and-nonmodifiable-arguments.md) e [diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Escolha do mecanismo de passagem  
 Você deve escolher cuidadosamente para cada argumento, o mecanismo de passagem.  
  
-   **Proteção**. Na escolha entre os mecanismos de dois passando, o critério mais importante é a exposição de variáveis para alterar de chamada. A vantagem de passar um argumento `ByRef` é que o procedimento pode retornar um valor para o código de chamada por meio do argumento. A vantagem de passar um argumento `ByVal` é que ele protege uma variável que está sendo alterado pelo procedimento.  
  
-   **Desempenho**. Embora o mecanismo de passagem pode afetar o desempenho do seu código, a diferença é geralmente é insignificante. Uma exceção a isso é um tipo de valor passado `ByVal`. Nesse caso, o Visual Basic copia o conteúdo de dados inteiro do argumento. Portanto, para um tipo de valor grande, como uma estrutura, ele pode ser mais eficiente para passá-lo `ByRef`.  
  
     Para tipos de referência, somente o ponteiro para os dados é copiados (quatro bytes nas plataformas de 32 bits, oito bytes nas plataformas de 64 bits). Portanto, você pode passar argumentos de tipo `String` ou `Object` pelo valor sem prejudicar o desempenho.  
  
## <a name="determination-of-the-passing-mechanism"></a>Determinação do mecanismo de passagem  
 A declaração de procedimento especifica o mecanismo de passagem para cada parâmetro. O código de chamada não pode substituir um `ByVal` mecanismo.  
  
 Se um parâmetro for declarado com `ByRef`, o código de chamada pode forçar o mecanismo para `ByVal` colocando o nome do argumento entre parênteses na chamada. Para obter mais informações, confira [Como: Forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 É o padrão no Visual Basic passar argumentos por valor.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Quando você passar um argumento por valor  
  
-   Se o elemento de código chamada subjacente do argumento for um elemento não modificável, declarar o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Nenhum código pode alterar o valor de um elemento não modificável.  
  
-   Se o elemento base é modificável, mas você não deseja que o procedimento para ser capaz de alterar seu valor, declare o parâmetro `ByVal`. Somente o código de chamada pode alterar o valor de um elemento modificável passado por valor.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Quando você passar um argumento por referência  
  
-   Se o procedimento tenha uma necessidade original para alterar o elemento subjacente no código de chamada, declare o parâmetro correspondente [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Se a execução correta do código depende do procedimento alterar o elemento subjacente no código de chamada, declare o parâmetro `ByRef`. Se você a passar por valor, ou se o código de chamada substitui a `ByRef` mecanismo de passagem, colocando o argumento entre parênteses, a chamada de procedimento pode produzir resultados inesperados.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir ilustra quando passar argumentos por valor e passá-los por referência. Procedimento `Calculate` tem uma `ByVal` e um `ByRef` parâmetro. Considerando uma taxa de juros `rate`e uma soma de dinheiro, `debt`, a tarefa do procedimento é calcular um novo valor para `debt` que é o resultado da aplicação a taxa de juros para o valor original de `debt`. Porque `debt` é um `ByRef` parâmetro, o novo total é refletido no valor do argumento no código de chamada que corresponde ao `debt`. Parâmetro `rate` é um `ByVal` parâmetro porque `Calculate` não deve alterar seu valor.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbcnProcedures#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class2.vb#74)]  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos](./index.md)
- [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)
- [Como: Passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)
- [Como: Altere o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)
- [Como: Proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [Como: Forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md)
- [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
