---
title: "Passando argumentos por valor e por referência (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752c0c8e90cafe457cbd5d684bc984a1ea4632ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Passando argumentos por valor e por referência (Visual Basic)
Em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], você pode passar um argumento para um procedimento *pelo valor* ou *por referência*. Isso é conhecido como o *mecanismo de passagem*, e determina se o procedimento pode modificar o elemento de programação subjacente do argumento no código de chamada. A declaração do procedimento determina o mecanismo de passagem para cada parâmetro, especificando o [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave.  
  
## <a name="distinctions"></a>Distinções  
 Ao passar um argumento para um procedimento, esteja ciente de várias distinções diferentes que interagem entre si:  
  
-   Se o elemento de programação subjacente é modificáveis ou não modificáveis  
  
-   Se o argumento em si é modificáveis ou não modificáveis  
  
-   Se o argumento está sendo passado por valor ou por referência  
  
-   Se o tipo de dados do argumento é um tipo de valor ou um tipo de referência  
  
 Para obter mais informações, consulte [diferenças entre modificáveis e não modificáveis argumentos](./differences-between-modifiable-and-nonmodifiable-arguments.md) e [diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Escolha do mecanismo de passagem  
 Você deve escolher o mecanismo de passagem com cuidado para cada argumento.  
  
-   **Proteção**. Em escolher entre os mecanismos de passagem de dois, o critério mais importante é a exposição de chamada de variáveis para alterar. A vantagem de passar um argumento `ByRef` é que o procedimento pode retornar um valor para o código de chamada por meio desse argumento. A vantagem de passar um argumento `ByVal` é que ele protege uma variável que está sendo alterada pelo procedimento.  
  
-   **Desempenho**. Embora o mecanismo de passagem pode afetar o desempenho do seu código, a diferença é geralmente é insignificante. Uma exceção a isso é um tipo de valor passado `ByVal`. Nesse caso, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] copia o conteúdo de todo o data do argumento. Portanto, para um tipo de valor grande, como uma estrutura, ele pode ser mais eficiente para passá-lo `ByRef`.  
  
     Para tipos de referência, somente o ponteiro para os dados é copiados (quatro bytes nas plataformas de 32 bits, oito bytes nas plataformas de 64 bits). Portanto, você pode passar argumentos de tipo `String` ou `Object` por valor sem prejudicar o desempenho.  
  
## <a name="determination-of-the-passing-mechanism"></a>Determinação do mecanismo de passagem  
 A declaração de procedimento especifica o mecanismo de passagem para cada parâmetro. O código de chamada não pode substituir um `ByVal` mecanismo.  
  
 Se um parâmetro for declarado com `ByRef`, o código de chamada pode forçar o mecanismo de `ByVal` incluindo o nome do argumento entre parênteses na chamada. Para obter mais informações, consulte [como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 O padrão no [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] é passar argumentos por valor.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Quando você passar um argumento por valor  
  
-   Se o elemento de código de chamada subjacente do argumento é um elemento não modificável, declare o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Nenhum código pode alterar o valor de um elemento não modificável.  
  
-   Se o elemento base é modificável, mas você não quiser que o procedimento seja capaz de alterar seu valor, declare o parâmetro `ByVal`. Somente o código de chamada pode alterar o valor de um elemento modificável passado por valor.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Quando você passar um argumento por referência  
  
-   Se o procedimento tiver uma necessidade original para alterar o elemento subjacente no código de chamada, declare o parâmetro correspondente [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Se a execução correta do código depende do procedimento alterando o elemento subjacente no código de chamada, declare o parâmetro `ByRef`. Se você passá-lo por valor, ou se o código de chamada substitui o `ByRef` mecanismo de passagem, colocando o argumento entre parênteses, a chamada de procedimento pode produzir resultados inesperados.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir ilustra quando passar argumentos por valor e passá-los por referência. Procedimento `Calculate` tem um `ByVal` e um `ByRef` parâmetro. Considerando uma taxa de juros, `rate`e uma soma de dinheiro, `debt`, a tarefa do procedimento é calcular um novo valor para `debt` que é o resultado da aplicação a taxa de juros para o valor original da `debt`. Porque `debt` é um `ByRef` parâmetro, o novo total é refletido no valor do argumento no código de chamada que corresponde ao `debt`. Parâmetro `rate` é um `ByVal` parâmetro porque `Calculate` não deve alterar seu valor.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Como passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)  
 [Como alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Como proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Como forçar um argumento a ser passado por Valor](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Passando Argumentos por Posição e Nome](./passing-arguments-by-position-and-by-name.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
