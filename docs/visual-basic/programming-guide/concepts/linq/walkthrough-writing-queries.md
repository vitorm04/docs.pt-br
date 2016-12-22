---
title: "Instru&#231;&#245;es passo a passo: escrevendo consultas em Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "consulta escrita [LINQ no Visual Basic]"
  - "LINQ [Visual Basic], instruções passo a passo"
  - "Escrever consultas da LINQ [Visual Basic]"
  - "gravando consultas LINQ [Visual Basic]"
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
caps.latest.revision: 70
caps.handback.revision: 70
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: escrevendo consultas em Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este passo a passo demonstra como você pode usar recursos de linguagem do Visual Basic para escrever [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] expressões de consulta. Passo a passo demonstra como criar consultas em uma lista de objetos do aluno, como executar as consultas e como modificá\-los. As consultas incorporam vários recursos como tipos anônimos, inicializadores de objeto e Inferência de tipo local.  
  
 Depois de concluir este passo a passo, você estará pronto para passar para exemplos e documentação específicas [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor que você está interessado.[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedores incluem [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], e [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
## Criar um projeto  
  
#### Para criar um projeto de aplicativo de console  
  
1.  Inicie o Visual Studio.  
  
2.  Sobre o **arquivo** aponte para **novo**, e, em seguida, clique em **projeto**.  
  
3.  No **modelos instalados** lista, clique em **Visual Basic**.  
  
4.  Na lista de tipos de projeto, clique em **aplicativo de Console**. No **nome** caixa, digite um nome para o projeto e, em seguida, clique em **OK**.  
  
     Um projeto é criado. Por padrão, ele contém uma referência a System.Core.dll. Além disso, o **importado namespaces** lista o [Página Referências, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic) inclui o <xref:System.Linq?displayProperty=fullName> namespace.  
  
5.  Sobre o [Página de Compilação, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic), certifique\-se de que **Option infer** é definido como **em**.  
  
## Adicionar uma fonte de dados na memória  
 A fonte de dados para as consultas neste passo a passo é uma lista de `Student` objetos. Cada `Student` objeto contém um nome, sobrenome, um ano de classe e uma classificação acadêmica no corpo do aluno.  
  
#### Para adicionar a fonte de dados  
  
-   Definir um `Student` classe e criar uma lista de instâncias da classe.  
  
    > [!IMPORTANT]
    >  O código necessário para definir o `Student` classe e criar a lista usada no passo a passo exemplos é fornecido no [Como criar uma lista de itens](../Topic/How%20to:%20Create%20a%20List%20of%20Items.md). Você pode copiá\-lo de lá e colá\-lo em seu projeto. O novo código substitui o código que apareceu quando você criou o projeto.  
  
#### Para adicionar um novo aluno à lista de alunos  
  
-   Seguem o padrão no `getStudents` para adicionar outra instância do `Student` classe à lista. Adicionar o aluno apresentará os inicializadores de objeto. Para obter mais informações, consulte [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md).  
  
## Criar uma consulta  
 Quando executada, a consulta adicionada nesta seção produz uma lista dos alunos cuja posição acadêmica coloca em dez. Porque a consulta seleciona completo `Student` objeto sempre, o tipo do resultado da consulta é `IEnumerable(Of Student)`. No entanto, o tipo da consulta geralmente não é especificado nas definições de consulta. Em vez disso, o compilador usa inferência de tipo local para determinar o tipo. Para obter mais informações, consulte [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Variável de intervalo da consulta, `currentStudent`, serve como uma referência a cada `Student` instância na origem, `students`, fornecendo acesso às propriedades de cada objeto na `students`.  
  
#### Para criar uma consulta simples  
  
1.  Localizar o local de `Main` método do projeto que está marcado como segue:  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Copie o seguinte código e cole\-o.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Posicione o ponteiro do mouse `studentQuery` em seu código para verificar se o tipo atribuído pelo compilador é `IEnumerable(Of Student)`.  
  
## Executar a consulta  
 A variável `studentQuery` contém a definição da consulta, não os resultados da execução da consulta. Um mecanismo típico para executar uma consulta é um `For Each` loop. Cada elemento na sequência retornada é acessado através da variável de iteração do loop. Para obter mais informações sobre a execução da consulta, consulte [Escrevendo a primeira consulta LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### Para executar a consulta  
  
1.  Adicione o seguinte `For Each` loop abaixo da consulta em seu projeto.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  O ponteiro do mouse sobre a variável de controle de loop `studentRecord` para ver seu tipo de dados. O tipo de `studentRecord` é inferido para ser `Student`, pois `studentQuery` retorna uma coleção de `Student` instâncias.  
  
3.  Compile e execute o aplicativo pressionando CTRL \+ F5. Observe que os resultados na janela do console.  
  
## Modifique a consulta  
 É mais fácil verificar os resultados da consulta se eles estiverem em uma ordem especificada. Você pode classificar a sequência retornada com base em qualquer campo disponível.  
  
#### Para ordenar os resultados  
  
1.  Adicione o seguinte `Order By` cláusula entre o `Where` instrução e `Select` instrução da consulta. O `Order By` cláusula será ordenar os resultados em ordem alfabética da a Z, de acordo com para o último nome de cada aluno.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Para ordenar por sobrenome e nome, adicione os campos à consulta:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Você também pode especificar `Descending` a ordem de Z a.  
  
3.  Compile e execute o aplicativo pressionando CTRL \+ F5. Observe que os resultados na janela do console.  
  
#### Para introduzir um identificador local  
  
1.  Adicione o código desta seção para introduzir um identificador local na expressão de consulta. O identificador local manterá um resultado intermediário. No exemplo a seguir, `name` é um identificador que mantém uma concatenação do aluno do primeiro e último nome. Um identificador local pode ser usado para fins de conveniência, ou ele pode melhorar o desempenho armazenando os resultados de uma expressão que deve ser calculado várias vezes.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Compile e execute o aplicativo pressionando CTRL \+ F5. Observe que os resultados na janela do console.  
  
#### Para projetar um campo na cláusula Select  
  
1.  Adicionar a consulta e `For Each` loop desta seção para criar uma consulta que produz uma sequência cujos elementos são diferentes dos elementos na origem. No exemplo a seguir, a fonte é uma coleção de `Student` objetos, mas somente um membro de cada objeto é retornado: o nome de alunos cujo nome é Garcia. Porque `currentStudent.First` é uma cadeia de caracteres, o tipo de dados da sequência retornado por `studentQuery3` é `IEnumerable(Of String)`, uma seqüência de cadeias de caracteres. Como nos exemplos anteriores, a atribuição de um dado tipo para `studentQuery3` é deixada para o compilador determinar usando inferência de tipo local.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Posicione o ponteiro do mouse `studentQuery3` em seu código para verificar se o tipo atribuído é `IEnumerable(Of String)`.  
  
3.  Compile e execute o aplicativo pressionando CTRL \+ F5. Observe que os resultados na janela do console.  
  
#### Para criar um tipo anônimo na cláusula Select  
  
1.  Adicione o código desta seção para ver como os tipos anônimos são usados em consultas. Usá\-los em consultas quando você quiser retornar vários campos de fonte de dados em vez de registros completos \(`currentStudent` registros nos exemplos anteriores\) ou um único campos \(`First` na seção anterior\). Em vez de definir um novo tipo nomeado que contém os campos que deseja incluir no resultado, você especificar os campos de `Select` cláusula e o compilador cria um tipo anônimo com esses campos como suas propriedades. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     O exemplo a seguir cria uma consulta que retorna o nome e a classificação de seniores cuja posição acadêmica está entre 1 e 10, em ordem de classificação acadêmica. Neste exemplo, o tipo de `studentQuery4` deve ser inferido porque o `Select` cláusula retorna uma instância de um tipo anônimo, e um tipo anônimo não tem nenhum nome utilizável.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Compile e execute o aplicativo pressionando CTRL \+ F5. Observe que os resultados na janela do console.  
  
## Exemplos adicionais  
 Agora que você aprendeu os conceitos básicos, a seguir está uma lista de exemplos adicionais para ilustrar a flexibilidade e a potência do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] consultas. Cada exemplo é precedido por uma breve descrição do que ele faz. Posicione o ponteiro do mouse sobre a variável de resultados de consulta para cada consulta ver o tipo inferido. Use um `For Each` loop para produzir os resultados.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## Informações adicionais  
 Depois de se familiarizar com os conceitos básicos de como trabalhar com consultas, você está pronto para ler a documentação e exemplos para o tipo específico de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] provedor que você está interessado em:  
  
 [Objetos LINQ to](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
## Consulte também  
 [Consulta integrada à linguagem \(LINQ\) \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/index.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Inicializadores de objeto: tipos nomeados e anônimos](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Consultas](../../../../visual-basic/language-reference/queries/queries.md)