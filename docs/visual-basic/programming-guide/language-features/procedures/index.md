---
title: Procedimentos no Visual Basic
ms.custom: ''
ms.date: 04/28/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5487dc7dbe9be50e065610cfd61815242bb74ac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="procedures-in-visual-basic"></a>Procedimentos no Visual Basic
Um *procedimento* é um bloco de demonstrativos [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] incluídos por um demonstrativo de declaração (`Function`, `Sub`, `Operator`, `Get`, `Set`) e por uma declaração `End` de correspondência. Todos os demonstrativos executáveis em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] devem estar incluídos em algum procedimento.  
  
## <a name="calling-a-procedure"></a>Chamar um procedimento  
 Você invoca um procedimento de algum outro lugar no código. Isso é conhecido como uma *chamada de procedimento*. Quando a execução do procedimento termina, ele retorna o controle para o código que o invocou, que é conhecido como o *código de chamada*. O código de chamada é um demonstrativo, ou uma expressão incluída em um demonstrativo, que especifica o procedimento pelo nome e transfere o controle a ele.  
  
## <a name="returning-from-a-procedure"></a>Retorno de um procedimento  
 Um procedimento retorna o controle ao código de chamada quando termina a execução. Para fazer isso, ele pode usar um [Demonstrativo de Retorno](../../../../visual-basic/language-reference/statements/return-statement.md), o [Demonstrativo de Saída](../../../../visual-basic/language-reference/statements/exit-statement.md) apropriado para o procedimento ou o demonstrativo [Final \<Palavra-chave > Demonstrativo](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) do procedimento. O controle, então, é transmitido para o código de chamada, seguindo o ponto da chamada de procedimento.  
  
-   Com um demonstrativo `Return`, o controle retorna imediatamente para o código de chamada. Os demonstrativos que seguem o demonstrativo `Return` não são executados. Você pode ter mais de um demonstrativo `Return` no mesmo procedimento.  
  
-   Com um demonstrativo `Exit Sub` ou `Exit Function`, o controle retorna imediatamente para o código de chamada. Os demonstrativos que seguem o demonstrativo `Exit` não são executados. Você pode ter mais de um demonstrativo `Exit` no mesmo procedimento e mesclar os demonstrativos `Return` e `Exit` no mesmo procedimento.  
  
-   Se um procedimento não tiver nenhum demonstrativo `Return` ou `Exit`, ele será concluído com um demonstrativo `End Sub` ou `End Function`, `End Get` ou `End Set` após o último demonstrativo do corpo do procedimento. O demonstrativo `End` retorna o controle imediatamente para o código de chamada. Você pode ter apenas um demonstrativo `End` em um procedimento.  
  
## <a name="parameters-and-arguments"></a>Parâmetros e argumentos  
 Na maioria dos casos, um procedimento precisa operar em diferentes dados cada vez que é chamado. Você pode transmitir essas informações para o procedimento como parte da chamada de procedimento. O procedimento define zero ou mais *parâmetros* e cada um deles representa um valor que se espera que seja transmitido. A correspondência com cada parâmetro na definição do procedimento é um *argumento* na chamada de procedimento. Um argumento representa o valor que você transmite ao parâmetro correspondente em uma determinada chamada de procedimento.  
  
## <a name="types-of-procedures"></a>Tipos de procedimentos  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] usa vários tipos de procedimentos:  
  
-   Os [procedimentos Sub](./sub-procedures.md) executam ações, mas não retornam um valor para o código de chamada.  
  
-   Os procedimentos de manipulação de eventos são procedimentos `Sub` que são executados em resposta a um evento gerado por uma ação do usuário ou por uma ocorrência em um programa.  
  
-   Os [procedimentos Function](./function-procedures.md) retornam um valor para o código de chamada. Eles podem executar outras ações antes de retornar.

    Algumas funções escritas em C# devolvem um *valor retornado de referência*. Os chamadores da função podem modificar o valor retornado, e essa modificação é refletida no estado do objeto de chamada. Começando com o Visual Basic 2017, o código do Visual Basic pode consumir valores retornados de referência, embora não possa retornar um valor por referência. Para obter mais informações, consulte [Reference return values](ref-return-values.md) (Valores retornados de referência).
  
-   Os [procedimentos de propriedade](./property-procedures.md) retornam e atribuem valores de propriedades em objetos ou módulos.  
  
-   Os [procedimentos de operador](./operator-procedures.md) definem o comportamento de um operador padrão quando um ou ambos os operandos são uma classe ou estrutura definida recentemente.  
  
-   Os [procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) definem um ou mais *parâmetros de tipo*, além de seus parâmetros normais, para que o código de chamada possa transmitir tipos de dados específicos cada vez que faz uma chamada.  
  
## <a name="procedures-and-structured-code"></a>Procedimentos e código estruturado  
 Cada linha de código executável em seu aplicativo deve estar em algum procedimento, como `Main`, `calculate` ou `Button1_Click`. Se você subdividir procedimentos grandes em menores, seu aplicativo ficará mais legível.  
  
 Os procedimentos são úteis para executar tarefas repetidas ou compartilhadas, como cálculos frequentemente usados, manipulação e controle de texto e operações de banco de dados. Você pode chamar um procedimento de vários locais diferentes em seu código. Desse modo, você pode usar procedimentos como blocos de construção para seu aplicativo.  
  
 Estruturar seu código com procedimentos lhe oferece os seguintes benefícios:  
  
-   Os procedimentos permitem que você divida seus programas em unidades lógicas distintas. Você pode depurar unidades separadas mais facilmente do que depurar um programa inteiro sem procedimentos.  
  
-   Depois de desenvolver procedimentos para uso em um programa, você pode usá-los em outros programas, geralmente com pouca ou nenhuma modificação. Isso ajuda a evitar a duplicação de código.  
  
## <a name="see-also"></a>Consulte também  
 [Como criar um procedimento](./how-to-create-a-procedure.md)  
 [Subprocedimentos](./sub-procedures.md)  
 [Procedimentos de Função](./function-procedures.md)  
 [Procedimentos de Propriedade](./property-procedures.md)  
 [Procedimentos de Operador](./operator-procedures.md)  
 [Parâmetros e Argumentos de Procedimento](./procedure-parameters-and-arguments.md)  
 [Procedimentos Recursivos](./recursive-procedures.md)  
 [Sobrecarga de Procedimento](./procedure-overloading.md)  
 [Procedimentos genéricos no Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
