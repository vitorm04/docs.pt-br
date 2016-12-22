---
title: "Instru&#231;&#245;es passo a passo: escrevendo consultas em C# (LINQ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], explicações passo a passo"
  - "LINQ [C#], gravando consultas"
  - "consultas [LINQ in C#], gravando"
  - "gravando consultas LINQ"
ms.assetid: 2962a610-419a-4276-9ec8-4b7f2af0c081
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: escrevendo consultas em C# (LINQ)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este passo a passo demonstra os recursos de linguagem c\# que são usados para escrever expressões de consulta LINQ.  
  
## Criar um projeto c\#  
  
> [!NOTE]
>  As instruções a seguir são para o Visual Studio. Se você estiver usando um ambiente de desenvolvimento diferentes, crie um projeto de console com uma referência a System.Core.dll e uma `using` diretriz para a <xref:System.Linq?displayProperty=fullName> namespace.  
  
#### Para criar um projeto no Visual Studio  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
     O **novo projeto** caixa de diálogo é aberta.  
  
3.  Expanda **instalados**, expanda **modelos**, expanda **Visual C\#**, e, em seguida, escolha **aplicativo de Console**.  
  
4.  No **nome** caixa de texto, digite um nome diferente ou aceite o nome padrão e, em seguida, escolha o **OK** botão.  
  
     O novo projeto aparece na **Solution Explorer**.  
  
5.  Observe que o projeto tem uma referência a System.Core.dll e uma `using` diretriz para a <xref:System.Linq?displayProperty=fullName> namespace.  
  
## Criar uma fonte de dados na memória  
 A fonte de dados para as consultas é uma lista simples de `Student` objetos. Cada `Student` registro tem um nome, sobrenome e uma matriz de inteiros que representa seus resultados de testes na classe. Copie este código no seu projeto. Observe as seguintes características:  
  
-   O `Student` classe consiste em propriedades implementadas automaticamente.  
  
-   Cada aluno na lista é inicializado com um inicializador de objeto.  
  
-   A lista em si é inicializada com um inicializador de coleção.  
  
 Essa estrutura de dados inteira será inicializada e instanciada sem chamadas explícitas a nenhum construtor ou acesso de membro explícito. Para obter mais informações sobre esses novos recursos, consulte [Propriedades autoimplementadas](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) e [Inicializadores de objeto e coleção](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
#### Para adicionar a fonte de dados  
  
-   Adicionar o `Student` classe e a lista inicializada de alunos a `Program` classe em seu projeto.  
  
     [!code-cs[CsLinqGettingStarted#11](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_1.cs)]  
  
#### Para adicionar um novo aluno à lista de alunos  
  
1.  Adicione um novo `Student` para o `Students` lista e use um nome e testar as pontuações de sua escolha. Tente digitar as novas informações de aluno para melhor aprender a sintaxe de inicializador de objeto.  
  
## Criar a consulta  
  
#### Para criar uma consulta simples  
  
-   O aplicativo `Main` método, criar uma consulta simples que, quando ele é executado, produzirá uma lista de todos os alunos cuja pontuação no primeiro teste era maior que 90. Observe que, como todo `Student` objeto é selecionado, o tipo de consulta é `IEnumerable<Student>`. Embora o código também pode usar a digitação implícita, usando o [var](../../../../csharp/language-reference/keywords/var.md) palavra\-chave, uma digitação explícita é usada para ilustrar claramente os resultados. \(Para obter mais informações sobre `var`, consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).\)  
  
     Observe também que, a consulta a variável de intervalo, `student`, serve como uma referência a cada `Student` na origem, fornecendo acesso de membro para cada objeto.  
  
 [!code-cs[CsLINQGettingStarted#12](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_2.cs)]  
  
## Executar a consulta  
  
#### Para executar a consulta  
  
1.  Agora, escrever o `foreach` loop que fará com que a consulta seja executada. Observe o seguinte sobre o código:  
  
    -   Cada elemento na sequência retornada é acessado pela variável de iteração no `foreach` loop.  
  
    -   O tipo dessa variável é `Student`, e o tipo da variável de consulta é compatível, `IEnumerable<Student>`.  
  
2.  Após você ter adicionado esse código, compilar e executar o aplicativo para ver os resultados no **Console** janela.  
  
 [!code-cs[CsLINQGettingStarted#13](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_3.cs)]  
  
#### Para adicionar outra condição de filtro  
  
1.  Você pode combinar várias condições Boolianas no `where` cláusula para refinar uma consulta. O código a seguir adiciona uma condição de forma que a consulta retorna os alunos cuja primeiro pontuação foi acima de 90 e cuja último pontuação foi inferior a 80. O `where` cláusula deve se parecer com o código a seguir.  
  
    ```  
    where student.Scores[0] > 90 && student.Scores[3] < 80  
    ```  
  
     Para obter mais informações, consulte [Cláusula where](../../../../visual-basic/language-reference/queries/where-clause.md).  
  
## Modifique a consulta  
  
#### Para ordenar os resultados  
  
1.  Será mais fácil verificar os resultados, se eles estiverem em algum tipo de ordem. Você pode ordenar a sequência retornada por qualquer campo acessível nos elementos de origem. Por exemplo, a seguinte `orderby` cláusula ordena os resultados em ordem alfabética de À Z de acordo com para o último nome de cada aluno. Adicione o seguinte `orderby` cláusula à sua consulta, logo após o `where` instrução e antes do `select` instrução:  
  
    ```  
    orderby student.Last ascending  
    ```  
  
2.  Agora, altere o `orderby` cláusula para que ele ordena os resultados em ordem inversa de acordo com a pontuação no primeiro teste da pontuação mais alta para a menor pontuação.  
  
    ```  
    orderby student.Scores[0] descending  
    ```  
  
3.  Alterar o `WriteLine` cadeia de caracteres de formato para que você possa ver as pontuações:  
  
    ```  
    Console.WriteLine("{0}, {1} {2}", student.Last, student.First, student.Scores[0]);  
    ```  
  
     Para obter mais informações, consulte [Cláusula orderby](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
#### Para agrupar os resultados  
  
1.  O agrupamento é uma poderosa funcionalidade em expressões de consulta. Uma consulta com uma cláusula group produz uma sequência de grupos, e cada grupo em si contém um `Key` e uma seqüência que consiste em todos os membros desse grupo. Nova consulta a seguir agrupa os alunos usando a primeira letra do sobrenome como a chave.  
  
     [!code-cs[CsLINQGettingStarted#14](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_4.cs)]  
  
2.  Observe que o tipo da consulta foi alterado. Ele produz uma sequência de grupos que têm um `char` tipo como uma chave e uma sequência de `Student` objetos. Como o tipo de consulta foi alterada, o código a seguir alterações a `foreach` também de loop de execução:  
  
     [!code-cs[CsLINQGettingStarted#15](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_5.cs)]  
  
3.  Execute o aplicativo e ver os resultados no **Console** janela.  
  
     Para obter mais informações, consulte [Cláusula group](../../../../csharp/language-reference/keywords/group-clause.md).  
  
#### Para tornar as variáveis de tipo implícito  
  
1.  Codificação explicitamente `IEnumerables` de `IGroupings` pode rapidamente se tornar entediante. Você pode escrever a mesma consulta e `foreach` muito mais conveniente, usando um loop `var`. O `var` palavra\-chave não altera os tipos de objetos; ele simplesmente instrui o compilador a inferir os tipos. Alterar o tipo de `studentQuery` e a variável de iteração `group` para `var` e execute a consulta novamente. Observe que no interno `foreach` loop, a variável de iteração ainda é digitada como `Student`, e a consulta funciona exatamente como antes. Alteração de `s` variável de iteração para `var` e execute a consulta novamente. Você verá que você obtenha exatamente os mesmos resultados.  
  
     [!code-cs[CsLINQGettingStarted#16](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_6.cs)]  
  
     Para obter mais informações sobre [var](../../../../csharp/language-reference/keywords/var.md), consulte [Variáveis locais de tipo implícito](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
#### Para ordenar os grupos pelo valor da chave  
  
1.  Ao executar a consulta anterior, observe que os grupos não estão em ordem alfabética. Para alterar isso, você deve fornecer um `orderby` cláusula após o `group` cláusula. Mas, para usar um `orderby` cláusula, primeiro é necessário um identificador que serve como uma referência para os grupos criados pelo `group` cláusula. Forneça o identificador usando o `into` palavra\-chave, da seguinte maneira:  
  
     [!code-cs[csLINQGettingStarted#17](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_7.cs)]  
  
     Quando você executa essa consulta, você verá que os grupos agora estão classificados em ordem alfabética.  
  
#### Para introduzir um identificador usando let  
  
1.  Você pode usar o `let` palavra\-chave para introduzir um identificador para qualquer resultado da expressão na expressão de consulta. Esse identificador pode ser uma conveniência, como no exemplo a seguir, ou ele pode melhorar o desempenho armazenando os resultados de uma expressão para que ele não precisa ser calculado várias vezes.  
  
     [!code-cs[csLINQGettingStarted#18](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_8.cs)]  
  
     Para obter mais informações, consulte [Cláusula let](../../../../csharp/language-reference/keywords/let-clause.md).  
  
#### Para usar a sintaxe de método em uma expressão de consulta  
  
1.  Conforme descrito em [Sintaxe de consulta e sintaxe de método em LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md), algumas operações de consulta só podem ser expresso usando sintaxe de método. O código a seguir calcula a pontuação total para cada `Student` na sequência de origem e então chama o `Average()` método nos resultados da consulta para calcular a pontuação média da classe. Observe a colocação de parênteses em torno de expressão de consulta.  
  
     [!code-cs[csLINQGettingStarted#19](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_9.cs)]  
  
#### Para transformar ou projetar na cláusula select  
  
1.  É muito comum para uma consulta produzir uma sequência cujos elementos são diferentes dos elementos nas sequências de origem. Exclua ou comente o loop de consulta e execução anterior e substituí\-lo com o código a seguir. Observe que a consulta retorna uma seqüência de cadeias de caracteres \(não `Students`\), e esse fato é refletido no `foreach` loop.  
  
     [!code-cs[csLINQGettingStarted#20](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_10.cs)]  
  
2.  Código anterior neste passo a passo indicou que a pontuação média de classe está aproximadamente 334. Para produzir uma sequência de `Students` cuja pontuação total é maior que a média de classe, juntamente com seus `Student ID`, você pode usar um tipo anônimo no `select` instrução:  
  
     [!code-cs[csLINQGettingStarted#21](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/walkthrough-writing-queries-linq_11.cs)]  
  
## Próximas etapas  
 Depois que você estiver familiarizado com os aspectos básicos de como trabalhar com consultas em c\#, você estará pronto para ler a documentação e exemplos para o tipo específico de provedor LINQ que lhe interessam:  
  
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)  
  
 [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md)  
  
 [LINQ to XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
  
 [LINQ to Objects \(c\#\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
## Consulte também  
 [Consulta integrada à linguagem \(LINQ\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/index.md)   
 [Introdução a LINQ em C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Expressões de consulta LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)