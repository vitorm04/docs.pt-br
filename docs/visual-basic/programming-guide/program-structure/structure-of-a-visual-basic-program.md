---
title: Estrutura de um programa Visual Basic | Documentos do Microsoft
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
- conditional compilation, Visual Basic
- program structure, Visual Basic
- procedures, structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
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
ms.openlocfilehash: 64aab045538461d86946c870fa428bf8ad4ec15e
ms.lasthandoff: 03/13/2017

---
# <a name="structure-of-a-visual-basic-program"></a>Estrutura de um programa Visual Basic
Um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa for criado partir de blocos de construção padrão. A *solução* consiste em um ou mais projetos. A *projeto* por sua vez, pode conter um ou mais assemblies. Cada *assembly* são compiladas a partir de um ou mais arquivos de origem. A *arquivo de origem* fornece a definição e implementação de classes, estruturas, módulos e interfaces, que, por fim, contenham todo o seu código.  
  
 Para obter mais informações sobre esses blocos de construção de uma [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de programa, consulte [soluções e projetos](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio) e [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).  
  
## <a name="file-level-programming-elements"></a>Elementos de programação de nível de arquivo  
 Quando você iniciar um projeto ou arquivo e abra o editor de código, você verá algum código já no local e na ordem correta. Qualquer código que você escreve deve seguir a sequência a seguir:  
  
1.  `Option`instruções  
  
2.  `Imports`instruções  
  
3.  `Namespace`instruções e os elementos de nível de namespace  
  
 Se você inserir instruções em uma ordem diferente, erros de compilação podem ocorrer.  
  
 Um programa também pode conter instruções de compilação condicional. Você pode intercalar no arquivo de origem entre as instruções da sequência anterior.  
  
### <a name="option-statements"></a>Instruções de opção  
 `Option`instruções estabelecerem regras básicas para código subsequente, ajudando a evitar erros de sintaxe e lógica. O [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md) garante que todas as variáveis são declaradas e escritas corretamente, o que reduz o tempo de depuração. O [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) ajuda a minimizar a perda de dados e erros de lógica que pode ocorrer ao trabalhar entre variáveis de diferentes tipos de dados. O [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) Especifica as cadeias de caracteres de maneira são comparadas entre si, com base nas suas `Binary` ou `Text` valores.  
  
### <a name="imports-statements"></a>Instruções Imports  
 Você pode incluir um [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para importar os nomes definidos fora do projeto. Um `Imports` instrução permite que seu código fazer referência a classes e outros tipos definidos no namespace importado, sem ter que qualificá-los. Você pode usar tantos `Imports` instruções conforme apropriado. Para obter mais informações, consulte [referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Declarações de Namespace  
 Namespaces ajuda você a organizar e classificar os elementos de programação para facilidade de agrupamento e acessar. Você usa o [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) para classificar as instruções a seguir em um namespace específico. Para obter mais informações, consulte [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Instruções de compilação condicional  
 Instruções de compilação condicional podem aparecer em quase qualquer lugar em seu arquivo de origem. Elas causam partes do seu código para serem incluídos ou excluídos no tempo de compilação, dependendo de determinadas condições. Você também pode usá-los para depurar seu aplicativo, como o código condicional é executado no modo somente de depuração. Para obter mais informações, consulte [compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Elementos de programação de nível de Namespace  
 Classes, estruturas e módulos contêm todo o código no arquivo de origem. Eles são *nível de namespace* elementos, que podem aparecer dentro de um namespace ou no nível do arquivo de origem. Elas contêm as declarações de todos os outros elementos de programação. Interfaces, que definem assinaturas de elemento, mas não fornecem nenhuma implementação, também aparecem no nível de módulo. Para obter mais informações sobre os elementos de nível de módulo, consulte o seguinte:  
  
-   [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Elementos de dados no nível de namespace são enumerações e delegados.  
  
## <a name="module-level-programming-elements"></a>Elementos de programação de nível de módulo  
 Procedimentos, operadores, propriedades e eventos são os únicos elementos de programação que podem conter código executável (instruções que executam ações em tempo de execução). Eles são o *nível de módulo* elementos do programa. Para obter mais informações sobre os elementos de nível de procedimento, consulte o seguinte:  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Elementos de dados no nível de módulo são variáveis, constantes, enumerações e delegados.  
  
## <a name="procedure-level-programming-elements"></a>Elementos de programação de nível de procedimento  
 A maior parte do conteúdo do *nível de procedimento* elementos são instruções executáveis, que constituem o código de tempo de execução do programa. Todos os códigos executáveis devem estar em algum procedimento (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Para obter mais informações, consulte [instruções](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Elementos de dados no nível de procedimento são limitados a constantes e variáveis locais.  
  
## <a name="the-main-procedure"></a>Procedimento principal  
 O `Main` procedimento é o primeiro código ao seu aplicativo foi carregado. `Main`serve como ponto de partida e controle geral para seu aplicativo. Existem quatro variedades de `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 A variedade mais comum desse procedimento é `Sub Main()`. Para obter mais informações, consulte [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Consulte também  
 [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Limitações do Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)
