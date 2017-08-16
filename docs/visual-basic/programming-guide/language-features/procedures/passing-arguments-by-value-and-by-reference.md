---
title: "Passando argumentos por valor e por referência (Visual Basic) | Documentos do Microsoft"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- passing arguments, by value or by reference
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing, by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
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
ms.openlocfilehash: 56d1ceba14020ca7f3dc750c2318efd3e9586af0
ms.lasthandoff: 03/13/2017

---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>Passando argumentos por valor e por referência (Visual Basic)
Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], você pode passar um argumento para um procedimento *pelo valor* ou *por referência*. Isso é conhecido como o *mecanismo de passagem*, e determina se o procedimento pode modificar o elemento de programação subjacente o argumento o código de chamada. A declaração do procedimento determina o mecanismo de passagem de cada parâmetro especificando o [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) palavra-chave.  
  
## <a name="distinctions"></a>Distinções  
 Ao passar um argumento para um procedimento, esteja ciente das várias distinções diferentes que interagem entre si:  
  
-   Se o elemento de programação subjacente é modificáveis ou não modificáveis  
  
-   Se o próprio argumento é modificáveis ou não modificáveis  
  
-   Se o argumento está sendo passado por valor ou por referência  
  
-   Se o tipo de dados de argumento é um tipo de valor ou um tipo de referência  
  
 Para obter mais informações, consulte [as diferenças entre modificáveis e não modificáveis argumentos](./differences-between-modifiable-and-nonmodifiable-arguments.md) e [as diferenças entre passar um argumento por valor e por referência](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
## <a name="choice-of-passing-mechanism"></a>Escolha do mecanismo de passagem  
 Você deve escolher cuidadosamente para cada argumento, o mecanismo de passagem.  
  
-   **Proteção**. Escolher entre os mecanismos de passagem de dois, o critério mais importante é a exposição de chamar a variável para alterar. A vantagem de passar um argumento `ByRef` é que o procedimento pode retornar um valor para o código de chamada através desse argumento. A vantagem de passar um argumento `ByVal` é que ele protege uma variável que está sendo alterada pelo procedimento.  
  
-   **Desempenho**. Embora o mecanismo de passagem pode afetar o desempenho do seu código, a diferença é geralmente é insignificante. Uma exceção a isso é um tipo de valor passado `ByVal`. Nesse caso, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copia o conteúdo de todo o data do argumento. Portanto, para um tipo de valor grande, como uma estrutura, ele pode ser mais eficiente para passá-lo `ByRef`.  
  
     Para tipos de referência, somente o ponteiro para os dados é copiados (quatro bytes em plataformas de 32 bits, oito bytes em plataformas de 64 bits). Portanto, você pode passar argumentos de tipo `String` ou `Object` por valor sem prejudicar o desempenho.  
  
## <a name="determination-of-the-passing-mechanism"></a>Determinação do mecanismo de passagem  
 A declaração de procedimento especifica o mecanismo de passagem de cada parâmetro. O código de chamada não pode substituir um `ByVal` mecanismo.  
  
 Se um parâmetro é declarado com `ByRef`, o código de chamada pode forçar o mecanismo para `ByVal` colocando o nome do argumento entre parênteses na chamada. Para obter mais informações, consulte [como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
 O padrão no [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é passar argumentos por valor.  
  
## <a name="when-to-pass-an-argument-by-value"></a>Quando passar um argumento por valor  
  
-   Se o elemento de código chamada subjacente o argumento é um elemento não modificável, declare o parâmetro correspondente [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). Nenhum código pode alterar o valor de um elemento não modificável.  
  
-   Se o elemento base é modificável, mas você não quiser que o procedimento seja capaz de alterar seu valor, declare o parâmetro `ByVal`. Somente o código de chamada pode alterar o valor de um elemento modificável passado por valor.  
  
## <a name="when-to-pass-an-argument-by-reference"></a>Quando você passar um argumento por referência  
  
-   Se o procedimento tenha uma necessidade original para alterar o elemento subjacente no código de chamada, declare o parâmetro correspondente [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).  
  
-   Se a execução correta do código depende do procedimento alterar o elemento subjacente no código de chamada, declare o parâmetro `ByRef`. Se você a passar por valor, ou se o código de chamada substitui o `ByRef` mecanismo de passagem, colocando o argumento entre parênteses, a chamada de procedimento pode produzir resultados inesperados.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 O exemplo a seguir ilustra quando passar argumentos por valor e passá-los por referência. Procedimento `Calculate` tem um `ByVal` e um `ByRef` parâmetro. Dada uma taxa de juros, `rate`e uma soma de dinheiro, `debt`, é calcular um novo valor para a tarefa do procedimento `debt` que é o resultado da aplicação a taxa de juros para o valor original de `debt`. Porque `debt` é um `ByRef` parâmetro, o novo total será refletido no valor do argumento no código de chamada que corresponde a `debt`. Parâmetro `rate` é um `ByVal` parâmetro porque `Calculate` não deve alterar seu valor.  
  
### <a name="code"></a>Código  
 [!code-vb[VbVbcnProcedures&#74;](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Procedimentos](./index.md)   
 [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md)   
 [Como: passar argumentos para um procedimento](./how-to-pass-arguments-to-a-procedure.md)   
 [Como: alterar o valor de um argumento de procedimento](./how-to-change-the-value-of-a-procedure-argument.md)   
 [Como: proteger um argumento de procedimento contra alterações de valor](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Como: forçar um argumento a ser passado por valor](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passando argumentos por posição e nome](./passing-arguments-by-position-and-by-name.md)   
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
