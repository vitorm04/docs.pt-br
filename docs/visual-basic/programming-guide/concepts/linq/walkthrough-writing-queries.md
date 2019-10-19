---
title: Gravando consultas no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ [Visual Basic], walkthroughs
- LINQ [Visual Basic], writing queries
- writing LINQ queries [Visual Basic]
ms.assetid: f0045808-b9fe-4d31-88d1-473d9957211e
ms.openlocfilehash: ac654701a459b57e7121cb82f4cf53941bcf15e0
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578939"
---
# <a name="walkthrough-writing-queries-in-visual-basic"></a>Instruções passo a passo: escrevendo consultas em Visual Basic

Este tutorial demonstra como você pode usar Visual Basic recursos de idioma para escrever [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressões de consulta. O tutorial demonstra como criar consultas em uma lista de objetos de aluno, como executar as consultas e como modificá-las. As consultas incorporam vários recursos, incluindo inicializadores de objeto, inferência de tipo local e tipos anônimos.

Depois de concluir este passo a passos, você estará pronto para passar para os exemplos e a documentação do provedor de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] específico em que você está interessado. os provedores de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] incluem [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], LINQ to DataSet e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].

## <a name="create-a-project"></a>Criar um projeto

### <a name="to-create-a-console-application-project"></a>Para criar um projeto de aplicativo de console

1. Inicie o Visual Studio.

2. No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.

3. Na lista **modelos instalados** , clique em **Visual Basic**.

4. Na lista de tipos de projeto, clique em **aplicativo de console**. Na caixa **nome** , digite um nome para o projeto e clique em **OK**.

    Um projeto é criado. Por padrão, ele contém uma referência a System. Core. dll. Além disso, a lista de **namespaces importados** na [página referências, designer de projeto (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic) inclui o namespace <xref:System.Linq?displayProperty=nameWithType>.

5. Na [página compilar, designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), verifique se **Option Infer** está definida como **on**.

## <a name="add-an-in-memory-data-source"></a>Adicionar uma Fonte de Dados na Memória

A fonte de dados para as consultas neste passo a passos é uma lista de objetos `Student`. Cada objeto de `Student` contém um nome, um sobrenome, um ano de classe e uma classificação acadêmica no corpo do aluno.

### <a name="to-add-the-data-source"></a>Para adicionar a fonte de dados

- Defina uma classe de `Student` e crie uma lista de instâncias da classe.

  > [!IMPORTANT]
  > O código necessário para definir a classe de `Student` e criar a lista usada nos exemplos de explicação é fornecido em [como: criar uma lista de itens](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Você pode copiá-lo de lá e colá-lo em seu projeto. O novo código substitui o código que apareceu quando você criou o projeto.

### <a name="to-add-a-new-student-to-the-students-list"></a>Para adicionar um novo aluno à lista de alunos

- Siga o padrão no método `getStudents` para adicionar outra instância da classe `Student` à lista. Adicionar o aluno apresentará a você os inicializadores de objeto. Para obter mais informações, consulte [inicializadores de objeto: tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).

## <a name="create-a-query"></a>Criar uma consulta

Quando executado, a consulta adicionada nesta seção produz uma lista dos alunos cuja classificação acadêmica os coloca nos dez principais. Como a consulta seleciona o objeto de `Student` completo a cada vez, o tipo de resultado da consulta é `IEnumerable(Of Student)`. No entanto, o tipo da consulta normalmente não é especificado nas definições de consulta. Em vez disso, o compilador usa a inferência de tipo local para determinar o tipo. Para obter mais informações, consulte [inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md). A variável de intervalo da consulta, `currentStudent`, serve como uma referência a cada instância de `Student` na fonte, `students`, fornecendo acesso às propriedades de cada objeto no `students`.

### <a name="to-create-a-simple-query"></a>Para criar uma consulta simples

1. Localize o local no método `Main` do projeto que está marcado da seguinte maneira:

    [!code-vb[VbLINQWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#1)]

    Copie o código a seguir e cole-o em.

    [!code-vb[VbLINQWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#2)]

2. Posicione o ponteiro do mouse sobre `studentQuery` em seu código para verificar se o tipo atribuído ao compilador é `IEnumerable(Of Student)`.

## <a name="run-the-query"></a>Executar a Consulta

A variável `studentQuery` contém a definição da consulta, não os resultados da execução da consulta. Um mecanismo típico para executar uma consulta é um loop `For Each`. Cada elemento na sequência retornada é acessado por meio da variável de iteração de loop. Para obter mais informações sobre a execução da consulta, consulte [escrevendo sua primeira consulta LINQ](../../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).

### <a name="to-run-the-query"></a>Para executar a consulta

1. Adicione o seguinte loop de `For Each` abaixo da consulta em seu projeto.

    [!code-vb[VbLINQWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#3)]

2. Posicione o ponteiro do mouse sobre a variável de controle de loop `studentRecord` para ver seu tipo de dados. O tipo de `studentRecord` é inferido para ser `Student`, porque `studentQuery` retorna uma coleção de instâncias de `Student`.

3. Crie e execute o aplicativo pressionando CTRL + F5. Observe os resultados na janela do console.

## <a name="modify-the-query"></a>Modificar a Consulta

É mais fácil verificar os resultados da consulta se eles estiverem em uma ordem especificada. Você pode classificar a sequência retornada com base em qualquer campo disponível.

### <a name="to-order-the-results"></a>Para ordenar os resultados

1. Adicione a seguinte cláusula `Order By` entre a instrução `Where` e a instrução `Select` da consulta. A cláusula `Order By` ordenará os resultados em ordem alfabética de a a Z, de acordo com o sobrenome de cada aluno.

    ```vb
    Order By currentStudent.Last Ascending
    ```

2. Para ordenar por sobrenome e, em seguida, primeiro nome, adicione os dois campos à consulta:

    ```vb
    Order By currentStudent.Last Ascending, currentStudent.First Ascending
    ```

    Você também pode especificar `Descending` para ordenar de Z a A.

3. Crie e execute o aplicativo pressionando CTRL + F5. Observe os resultados na janela do console.

### <a name="to-introduce-a-local-identifier"></a>Para introduzir um identificador local

1. Adicione o código nesta seção para introduzir um identificador local na expressão de consulta. O identificador local manterá um resultado intermediário. No exemplo a seguir, `name` é um identificador que contém uma concatenação dos nomes e sobrenomes do aluno. Um identificador local pode ser usado para conveniência ou pode melhorar o desempenho armazenando os resultados de uma expressão que, de outra forma, seriam calculados várias vezes.

    [!code-vb[VbLINQWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#4)]

2. Crie e execute o aplicativo pressionando CTRL + F5. Observe os resultados na janela do console.

### <a name="to-project-one-field-in-the-select-clause"></a>Para projetar um campo na cláusula Select

1. Adicione a consulta e `For Each` loop desta seção para criar uma consulta que produza uma sequência cujos elementos diferem dos elementos na origem. No exemplo a seguir, a origem é uma coleção de objetos `Student`, mas apenas um membro de cada objeto é retornado: o nome de alunos cujo sobrenome é Garcia. Como `currentStudent.First` é uma cadeia de caracteres, o tipo de dados da sequência retornada pelo `studentQuery3` é `IEnumerable(Of String)`, uma sequência de cadeias de caracteres. Como nos exemplos anteriores, a atribuição de um tipo de dados para `studentQuery3` é deixada para o compilador determinar usando a inferência de tipo local.

    [!code-vb[VbLINQWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#5)]

2. Posicione o ponteiro do mouse sobre `studentQuery3` em seu código para verificar se o tipo atribuído é `IEnumerable(Of String)`.

3. Crie e execute o aplicativo pressionando CTRL + F5. Observe os resultados na janela do console.

### <a name="to-create-an-anonymous-type-in-the-select-clause"></a>Para criar um tipo anônimo na cláusula Select

1. Adicione o código desta seção para ver como os tipos anônimos são usados em consultas. Você os usa em consultas quando deseja retornar vários campos da fonte de dados em vez de registros completos (`currentStudent` registros nos exemplos anteriores) ou campos únicos (`First` na seção anterior). Em vez de definir um novo tipo nomeado que contém os campos que você deseja incluir no resultado, você especifica os campos na cláusula `Select` e o compilador cria um tipo anônimo com esses campos como suas propriedades. Para obter mais informações, consulte [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

    O exemplo a seguir cria uma consulta que retorna o nome e a classificação dos seniores cuja classificação acadêmica está entre 1 e 10, em ordem de classificação acadêmica. Neste exemplo, o tipo de `studentQuery4` deve ser inferido porque a cláusula `Select` retorna uma instância de um tipo anônimo, e um tipo anônimo não tem nenhum nome utilizável.

    [!code-vb[VbLINQWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#6)]

2. Crie e execute o aplicativo pressionando CTRL + F5. Observe os resultados na janela do console.

## <a name="additional-examples"></a>Exemplos adicionais

Agora que você entende os conceitos básicos, veja a seguir uma lista de exemplos adicionais para ilustrar a flexibilidade e a potência das consultas de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Cada exemplo é precedido por uma breve descrição do que ele faz. Posicione o ponteiro do mouse sobre a variável de resultado da consulta para cada consulta para ver o tipo inferido. Use um loop de `For Each` para produzir os resultados.

[!code-vb[VbLINQWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQWalkthrough/VB/Class1.vb#7)]

## <a name="additional-information"></a>Informações adicionais

Depois de estar familiarizado com os conceitos básicos do trabalho com consultas, você está pronto para ler a documentação e os exemplos para o tipo específico de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] provedor no qual você está interessado:

- [LINQ to Objects](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)

- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)

- [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)

- [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)

## <a name="see-also"></a>Consulte também

- [LINQ (consulta integrada à linguagem) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Inferência de Tipo de Variável Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Inicializadores de objeto: tipos nomeados e anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Tipos Anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
