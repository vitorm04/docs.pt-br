---
title: Estrutura de um programa Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 42e366a844f9c5e80a8f617bf73dfd869608540d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295764"
---
# <a name="structure-of-a-visual-basic-program"></a>Estrutura de um programa Visual Basic
Um programa Visual Basic é compilado para cima de blocos de construção padrão. Um *solução* consiste em um ou mais projetos. Um *projeto* por sua vez, pode conter um ou mais assemblies. Cada *assembly* são compiladas a partir de um ou mais arquivos de origem. Um *arquivo de origem* fornece a definição e implementação de classes, estruturas, módulos e interfaces, que contêm, por fim, todo o seu código.  
  
 Para obter mais informações sobre esses blocos de construção de um programa em Visual Basic, consulte [soluções e projetos](/visualstudio/ide/solutions-and-projects-in-visual-studio) e [Assemblies no .NET](../../../standard/assembly/index.md).  
  
## <a name="file-level-programming-elements"></a>Elementos de programação de nível de arquivo  
 Quando você iniciar um projeto ou arquivo e abra o editor de código, você verá algum código já está em vigor e na ordem correta. Qualquer código que você escreve deve seguir a sequência a seguir:  
  
1. `Option` Instruções  
  
2. `Imports` Instruções  
  
3. `Namespace` instruções e os elementos de nível de namespace  
  
 Se você inserir instruções em uma ordem diferente, podem resultar erros de compilação.  
  
 Um programa também pode conter instruções de compilação condicional. Você pode intercalar eles no arquivo de origem entre as instruções da sequência anterior.  
  
### <a name="option-statements"></a>Instruções de opção  
 `Option` instruções estabelecerem regras básicas para o código subsequente, ajudando a evitar erros de sintaxe e lógica. O [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md) garante que todas as variáveis são declaradas e escritas corretamente, o que reduz o tempo de depuração. O [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) ajuda a minimizar a perda de dados e erros de lógica que pode ocorrer quando você trabalha entre variáveis de diferentes tipos de dados. O [instrução opção comparar](../../../visual-basic/language-reference/statements/option-compare-statement.md) Especifica as cadeias de caracteres de forma são comparadas entre si, com base em uma seus `Binary` ou `Text` valores.  
  
### <a name="imports-statements"></a>Instruções Imports  
 Você pode incluir um [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) importar nomes definidos fora de seu projeto. Um `Imports` instrução permite que seu código fazer referência a classes e outros tipos definidos no namespace importado, sem ter que qualificá-los. Você pode criar quantas `Imports` instruções conforme apropriado. Para obter mais informações, consulte [referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Declarações de Namespace  
 Namespaces ajudam a organizar e classificar os elementos de programação para facilitar o agrupamento e acessar. Você usa o [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) para classificar as instruções a seguir em um namespace específico. Para obter mais informações, consulte [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Instruções de compilação condicional  
 Instruções de compilação condicional podem aparecer em quase qualquer lugar em seu arquivo de origem. Eles fazem com que partes do seu código para serem incluídos ou excluídos no tempo de compilação, dependendo de determinadas condições. Você também pode usá-los para depurar seu aplicativo, como o código condicional é executado no modo somente de depuração. Para obter mais informações, consulte [compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Elementos de programação de nível de Namespace  
 Classes, estruturas e módulos contêm todo o código no seu arquivo de origem. Eles são *nível de namespace* elementos, que podem aparecer dentro de um namespace ou no nível do arquivo de origem. Eles contêm as declarações de todos os outros elementos de programação. Interfaces, que definem assinaturas de elemento, mas não fornecem nenhuma implementação, também aparecem no nível de módulo. Para obter mais informações sobre os elementos de nível de módulo, consulte o seguinte:  
  
-   [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Elementos de dados no nível de namespace são delegados e enumerações.  
  
## <a name="module-level-programming-elements"></a>Elementos de programação de nível de módulo  
 Procedimentos, operadores, propriedades e eventos são os únicos elementos de programação que podem conter código executável (instruções que executam ações em tempo de execução). Eles são os *nível de módulo* elementos do programa. Para obter mais informações sobre os elementos de nível de procedimento, consulte o seguinte:  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Elementos de dados no nível de módulo são variáveis, constantes, enumerações e delegados.  
  
## <a name="procedure-level-programming-elements"></a>Elementos de programação de nível de procedimento  
 A maioria do conteúdo do *nível de procedimento* elementos são instruções executáveis, que constituem o código de tempo de execução do programa. Todo o código executável deve estar em algum procedimento (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`). Para obter mais informações, consulte [Instruções](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Elementos de dados no nível de procedimento são limitados a constantes e variáveis locais.  
  
## <a name="the-main-procedure"></a>Procedimento principal  
 O `Main` procedimento é o primeiro código ser executado quando seu aplicativo tiver sido carregado. `Main` serve como o ponto de partida e controle geral para seu aplicativo. Existem quatro variedades de `Main`:  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 A variedade mais comum desse procedimento é `Sub Main()`. Para obter mais informações, consulte [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## <a name="see-also"></a>Consulte também

- [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
- [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [Limitações do Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)
