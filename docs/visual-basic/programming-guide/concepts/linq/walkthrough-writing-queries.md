---
title: Escrevendo consultas em Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: 2f641d04b53d2e80985defcd6bd9a4882004fd97
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868005"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Instruções passo a passo: escrevendo consultas em Visual Basic
Este passo a passo demonstra como você pode usar recursos de linguagem do Visual Basic para escrever [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressões de consulta. O passo a passo demonstra como criar consultas em uma lista de objetos do aluno, como executar as consultas e como modificá-los. As consultas incorporam vários recursos, incluindo tipos anônimos, inferência de tipo local e inicializadores de objeto.  
  
 Depois de concluir este passo a passo, você estará pronto para passar para os exemplos e documentação para o determinado [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provedor que você está interessado. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provedores incluem [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="create-a-project"></a>Criar um projeto  
  
#### <a name="to-create-a-console-application-project"></a>Para criar um projeto de aplicativo de console  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  No **modelos instalados** , clique em **Visual Basic**.  
  
4.  Na lista de tipos de projeto, clique em **aplicativo de Console**. No **nome** caixa, digite um nome para o projeto e, em seguida, clique em **Okey**.  
  
     Um projeto é criado. Por padrão, ele contém uma referência à dll. Além disso, o **namespaces importados** lista os [página referências, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) inclui o <xref:System.Linq?displayProperty=nameWithType> namespace.  
  
5.  Sobre o [compilar página, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), certifique-se de que **Option infer** é definido como **em**.  
  
## <a name="add-an-in-memory-data-source"></a>Adicionar uma Fonte de Dados na Memória  
 A fonte de dados para as consultas neste passo a passo é uma lista de `Student` objetos. Cada `Student` objeto contém um nome, sobrenome, um ano de classe e uma classificação acadêmica no corpo do aluno.  
  
#### <a name="to-add-the-data-source"></a>Para adicionar a fonte de dados  
  
-   Definir um `Student` de classe e criar uma lista de instâncias da classe.  
  
    > [!IMPORTANT]
    >  O código necessário para definir a `Student` de classe e criar a lista usada no passo a passo exemplos é fornecido no [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Você pode copiá-lo a partir daí e cole-a no seu projeto. O novo código substitui o código que apareceu quando você criou o projeto.  
  
#### <a name="to-add-a-new-student-to-the-students-list"></a>Para adicionar um novo aluno à lista de alunos  
  
-   Seguem o padrão no `getStudents` método para adicionar outra instância da `Student` classe à lista. Adicionar o aluno apresentará os inicializadores de objeto. Para obter mais informações, consulte [inicializadores de objeto: tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).  
  
## <a name="create-a-query"></a>Criar uma consulta  
 Quando executada, a consulta adicionada nesta seção produz uma lista dos alunos cuja classificação acadêmica coloca-os nos dez principais. Porque a consulta seleciona completo `Student` cada vez, o tipo do resultado da consulta de objeto é `IEnumerable(Of Student)`. No entanto, o tipo de consulta normalmente não é especificado nas definições de consulta. Em vez disso, o compilador usa a inferência de tipo local para determinar o tipo. Para obter mais informações, consulte [inferência de tipo Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). Variável de intervalo da consulta, `currentStudent`, serve como uma referência a cada `Student` instância na origem, `students`, fornecendo acesso às propriedades de cada objeto no `students`.  
  
#### <a name="to-create-a-simple-query"></a>Para criar uma consulta simples  
  
1.  Encontre o local no `Main` método do projeto que é marcado da seguinte maneira:  
  
     [!code-vb[VbLINQWalkthrough#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_1.vb)]  
  
     Copie o código a seguir e cole-o no.  
  
     [!code-vb[VbLINQWalkthrough#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_2.vb)]  
  
2.  Posiciona o ponteiro do mouse sobre `studentQuery` em seu código para verificar se o tipo atribuído pelo compilador é `IEnumerable(Of Student)`.  
  
## <a name="run-the-query"></a>Executar a Consulta  
 A variável `studentQuery` contém a definição da consulta, não os resultados da execução da consulta. Um mecanismo típico para executar uma consulta é um `For Each` loop. Cada elemento na sequência retornada é acessado por meio da variável de iteração do loop. Para obter mais informações sobre a execução da consulta, consulte [escrever sua primeira consulta de LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
#### <a name="to-run-the-query"></a>Para executar a consulta  
  
1.  Adicione o seguinte `For Each` loop abaixo da consulta em seu projeto.  
  
     [!code-vb[VbLINQWalkthrough#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_3.vb)]  
  
2.  O ponteiro do mouse sobre a variável de controle de loop `studentRecord` para ver seu tipo de dados. O tipo de `studentRecord` será inferida para ser `Student`, porque `studentQuery` retorna uma coleção de `Student` instâncias.  
  
3.  Compile e execute o aplicativo pressionando CTRL + F5. Observe que os resultados na janela do console.  
  
## <a name="modify-the-query"></a>Modificar a Consulta  
 É mais fácil verificar os resultados da consulta, se eles estiverem em uma ordem especificada. Você pode classificar a sequência retornada com base em qualquer campo disponível.  
  
#### <a name="to-order-the-results"></a>Para ordenar os resultados  
  
1.  Adicione o seguinte `Order By` cláusula entre o `Where` instrução e o `Select` instrução da consulta. O `Order By` cláusula será ordenar os resultados em ordem alfabética de A a Z, de acordo com o para o último nome de cada aluno.  
  
    ```  
    Order By currentStudent.Last Ascending   
    ```  
  
2.  Para ordenar por sobrenome e nome, adicione os dois campos à consulta:  
  
    ```  
    Order By currentStudent.Last Ascending, currentStudent.First Ascending   
    ```  
  
     Você também pode especificar `Descending` a ordem de Z a.  
  
3.  Compile e execute o aplicativo pressionando CTRL + F5. Observe que os resultados na janela do console.  
  
#### <a name="to-introduce-a-local-identifier"></a>Para introduzir um identificador local  
  
1.  Adicione o código nesta seção para introduzir um identificador de local na expressão de consulta. O identificador local conterá um resultado intermediário. No exemplo a seguir, `name` é um identificador que mantém uma concatenação do aluno do primeiro e último nome. Um identificador local pode ser usado para sua conveniência, ou ele pode melhorar o desempenho armazenando os resultados de uma expressão que deve ser calculado várias vezes.  
  
     [!code-vb[VbLINQWalkthrough#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_4.vb)]  
  
2.  Compile e execute o aplicativo pressionando CTRL + F5. Observe que os resultados na janela do console.  
  
#### <a name="to-project-one-field-in-the-select-clause"></a>Para projetar um campo na cláusula Select  
  
1.  Adicione a consulta e `For Each` loop dessa seção para criar uma consulta que produz uma sequência cujos elementos são diferentes dos elementos na origem. No exemplo a seguir, a fonte é uma coleção de `Student` objetos, mas somente um membro de cada objeto é retornado: o nome de alunos cujo nome é Garcia. Porque `currentStudent.First` é uma cadeia de caracteres, o tipo de dados da sequência retornada por `studentQuery3` é `IEnumerable(Of String)`, uma sequência de cadeias de caracteres. Como nos exemplos anteriores, a atribuição de um dado tipo para `studentQuery3` é deixada para o compilador determine com o uso de inferência de tipo local.  
  
     [!code-vb[VbLINQWalkthrough#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_5.vb)]  
  
2.  Posiciona o ponteiro do mouse sobre `studentQuery3` em seu código para verificar se o tipo atribuído é `IEnumerable(Of String)`.  
  
3.  Compile e execute o aplicativo pressionando CTRL + F5. Observe que os resultados na janela do console.  
  
#### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Para criar um tipo anônimo na cláusula Select  
  
1.  Adicione o código desta seção para ver como os tipos anônimos são usados em consultas. Usá-los em consultas quando você deseja retornar vários campos de fonte de dados em vez de registros completos (`currentStudent` registros nos exemplos anteriores) ou únicas campos (`First` na seção anterior). Em vez de definir um novo tipo nomeado que contém os campos que você deseja incluir no resultado, especifique os campos no `Select` cláusula e o compilador cria um tipo anônimo com esses campos como suas propriedades. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
     O exemplo a seguir cria uma consulta que retorna o nome e a classificação de seniores cuja classificação acadêmica está entre 1 e 10, em ordem de classificação acadêmica. Neste exemplo, o tipo de `studentQuery4` deve ser inferido porque o `Select` cláusula retorna uma instância de um tipo anônimo, e um tipo anônimo tem nenhum nome utilizável.  
  
     [!code-vb[VbLINQWalkthrough#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_6.vb)]  
  
2.  Compile e execute o aplicativo pressionando CTRL + F5. Observe que os resultados na janela do console.  
  
## <a name="additional-examples"></a>Exemplos adicionais  
 Agora que você entende as Noções básicas, a seguir está uma lista de exemplos adicionais para ilustrar a flexibilidade e poder do [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] consultas. Cada exemplo é precedido por uma breve descrição do que ele faz. O ponteiro do mouse sobre a variável de resultado de consulta para cada consulta ver o tipo inferido. Use um `For Each` loop para produzir os resultados.  
  
 [!code-vb[VbLINQWalkthrough#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/walkthrough-writing-queries_7.vb)]  
  
## <a name="additional-information"></a>Informações adicionais  
 Depois de se familiarizar com os conceitos básicos de como trabalhar com consultas, você está pronto para ler a documentação e exemplos para o tipo específico de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provedor que você está interessado:  
  
 [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9)  
  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
  
 [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13)  
  
 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)  
  
## <a name="see-also"></a>Consulte também  
 [LINQ (consulta integrada à linguagem) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Inicializadores de objeto: tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Consultas](../../../../visual-basic/language-reference/queries/index.md)
