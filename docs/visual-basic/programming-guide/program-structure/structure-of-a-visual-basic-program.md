---
title: "Estrutura de um programa Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "compilação condicional, Visual Basic"
  - "procedimentos, Estrutura "
  - "estrutura do programa, Visual Basic"
  - "código do Visual Basic, estrutura do programa"
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estrutura de um programa Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programa é composto de blocos de construção padrão.  A  *solução* compreendem um ou mais projetos.  A  *projeto* por sua vez, pode conter um ou mais assemblies.  Cada  *assembly* é compilada a partir de um ou mais arquivos de origem.  A  *arquivo de origem* fornece a definição e implementação de classes, estruturas, módulos e interfaces, que, por fim, contenham todo o seu código.  
  
 Para obter mais informações sobre esses blocos de construção de um [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] de programa, consulte [Soluções e Projetos](/visual-studio/ide/solutions-and-projects-in-visual-studio) e [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Elementos de programação de nível de arquivo  
 Quando você inicia um projeto ou arquivo e abre o editor de código, você pode ver alguns códigos já no lugar e na ordem correta.  Qualquer código que você escreve deve seguir a seguinte seqüência:  
  
1.  `Option`instruções  
  
2.  `Imports`instruções  
  
3.  `Namespace`instruções e elementos de nível de namespace  
  
 Se você inserir instruções em uma ordem diferente, erros de compilação podem resultar.  
  
 Um programa também pode conter instruções de compilação condicional.  Você pode intercalar esses no arquivo de origem entre as instruções da seqüência precedente.  
  
### Instrução Option  
 `Option`instruções estabelecem regras básicas para código subseqüente, ajudando a evitar erros de sintaxe e lógica.  O [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md) garante que todas as variáveis são declaradas e escritas corretamente, o que reduz o tempo de depuração.  O [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) ajuda a minimizar a perda de dados e erros de lógica que pode ocorrer quando você trabalha entre variáveis de diferentes tipos de dados.  O [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) Especifica as seqüências de caracteres de forma são comparadas entre si, com base em uma seus `Binary` ou `Text` valores.  
  
### Instruções Imports  
 Você pode incluir um [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para importar nomes definidos fora do seu projeto.  Um `Imports` instrução permite que seu código fazer referência a classes e outros tipos definidos dentro do namespace importado, sem ter que qualificá\-los.  Você pode usar quantas `Imports` instruções conforme apropriado.  Para obter mais informações, consulte [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).  
  
### Declarações de namespace  
 Namespaces ajuda você a organizar e classificar os elementos de programação para facilitar o agrupamento e acessando.  Você pode usar o [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) para classificar as instruções a seguir em um namespace específico.  Para obter mais informações, consulte [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).  
  
### Instruções condicionais de compilação  
 Instruções de compilação condicional podem aparecer de praticamente qualquer lugar no seu arquivo de origem.  Eles fazem com que partes do seu código para serem incluídos ou excluídos em tempo de compilação, dependendo de certas condições.  Você também pode usá\-los para depurar seu aplicativo, porque o código condicional é executado no modo somente de depuração.  Para obter mais informações, consulte [Compilação condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).  
  
## Elementos de programação de nível de namespace  
 Classes, estruturas e módulos contêm todo o código no seu arquivo de origem.  Eles são  *nível de namespace* elementos, que podem aparecer dentro de um namespace ou no nível do arquivo de origem.  Eles mantêm as declarações de todos os outros elementos de programação.  Interfaces, que definem as assinaturas do elemento, mas não fornecem nenhuma implementação, também aparecem no nível de módulo.  Para obter mais informações sobre os elementos de nível de módulo, consulte o seguinte:  
  
-   [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [Instrução Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 Elementos de dados no nível do espaço para nome são delegados e enumerações.  
  
## Elementos de programação de nível de módulo  
 Procedimentos, operadores, propriedades e eventos são os únicos elementos de programação que podem conter código executável \(instruções que executam ações em tempo de execução\).  Eles são o  *nível de módulo* elementos do seu programa.  Para obter mais informações sobre os elementos de nível de procedimento, consulte o seguinte:  
  
-   [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [Instrução Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 Elementos de dados no nível de módulo são variáveis, constantes, delegados e enumerações.  
  
## Elementos de programação de nível de procedimento  
 A maioria do conteúdo do  *nível de procedimento* elementos são instruções executáveis, que constituem o código de tempo de execução do seu programa.  All executable code must be in some procedure \(`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`\).  Para obter mais informações, consulte [Instruções](../../../visual-basic/programming-guide/language-features/statements.md).  
  
 Elementos de dados no nível de procedimento são limitados a constantes e variáveis locais.  
  
## O procedimento Main  
 O `Main` procedimento é o primeiro código ao seu aplicativo foi carregado.  `Main`serve como o ponto de partida e controle geral do seu aplicativo.  Existem quatro variedades de `Main`.  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 A variedade mais comum desse procedimento é `Sub Main()`.  Para obter mais informações, consulte [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).  
  
## Consulte também  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/pt-br/9d030b60-e148-4366-a462-69532f02294c)   
 [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)   
 [Convenções de nomenclatura do Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Limitações do Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)