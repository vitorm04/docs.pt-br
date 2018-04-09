---
title: Cadeias de caracteres (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, strings
- strings [C#]
ms.assetid: 21580405-cb25-4541-89d5-037846a38b07
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9478900be008588597c1dd9e75f704c751ebe344
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/28/2018
---
# <a name="strings-c-programming-guide"></a>Cadeias de caracteres (Guia de Programação em C#)
Uma cadeia de caracteres é um objeto do tipo <xref:System.String> cujo valor é texto. Internamente, o texto é armazenado como uma coleção sequencial somente leitura de objetos <xref:System.Char>. Não há um caractere de finalização null ao fim de uma cadeia em C#. Portanto, uma cadeia de caracteres em C# pode ter qualquer número de caracteres nulos inseridos ('\0'). A propriedade `Char` de uma cadeia de caracteres representa o número de objetos <xref:System.String.Length%2A> que ela contém e não o número de caracteres Unicode. Para acessar os pontos de código Unicode individuais em uma cadeia de caracteres, use o objeto <xref:System.Globalization.StringInfo>.  
  
## <a name="string-vs-systemstring"></a>cadeia de caracteres vs. System.String  
 Em C#, a palavra-chave `string` é um alias para <xref:System.String>. Portanto, `String` e `string` são equivalentes, e você pode usar a convenção de nomenclatura que preferir. A classe `String` fornece vários métodos para criar, manipular e comparar cadeias de caracteres com segurança. Além disso, a linguagem C# sobrecarrega alguns operadores para simplificar operações comuns de cadeia de caracteres. Para saber mais sobre a palavra-chave, confira [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md). Para obter mais informações sobre o tipo e seus métodos, consulte <xref:System.String>.  
  
## <a name="declaring-and-initializing-strings"></a>Declaração e inicialização de cadeias de caracteres  
 Você pode declarar e inicializar cadeias de caracteres de várias maneiras, conforme mostrado no seguinte exemplo:  
  
 [!code-csharp[csProgGuideStrings#1](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_1.cs)]  
  
 Observe que você não usa o operador [new](../../../csharp/language-reference/keywords/new-operator.md) para criar um objeto de cadeia de caracteres, exceto ao inicializar a cadeia de caracteres com uma matriz de caracteres.  
  
 Inicialize uma cadeia de caracteres com o valor constante <xref:System.String.Empty> para criar um novo objeto <xref:System.String> cuja cadeia de caracteres tem comprimento zero. A representação de cadeia de caracteres literal de uma cadeia de caracteres de comprimento zero é "". Ao inicializar cadeias de caracteres com o valor <xref:System.String.Empty> em vez de [nulo](../../../csharp/language-reference/keywords/null.md), você poderá reduzir as chances de uma <xref:System.NullReferenceException> ocorrer. Use o método estático <xref:System.String.IsNullOrEmpty%28System.String%29> para verificar o valor de uma cadeia de caracteres antes de tentar acessá-la.  
  
## <a name="immutability-of-string-objects"></a>Imutabilidade de objetos de cadeia de caracteres  
 Objetos de cadeia de caracteres são *imutáveis*: não pode ser alterados após serem criados. Todos os métodos <xref:System.String> e operadores C# que aparecem para modificar uma cadeia de caracteres retornam, na verdade, os resultados em um novo objeto de cadeia de caracteres. No exemplo a seguir, quando o conteúdo de `s1` e `s2` é concatenado para formar uma única cadeia de caracteres, as duas cadeias de caracteres originais são modificadas. O operador `+=` cria uma nova cadeia de caracteres que tem o conteúdo combinado. Esse novo objeto é atribuído à variável `s1`, e o objeto original que foi atribuído a `s1` é liberado para coleta de lixo, pois nenhuma outra variável contém uma referência a ele.  
  
 [!code-csharp[csProgGuideStrings#2](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_2.cs)]  
  
 Como uma cadeia de caracteres de "modificação" na verdade é uma nova criação de cadeia de caracteres, você deve ter cuidado ao criar referências em cadeias de caracteres. Se você criar uma referência a uma cadeia de caracteres e "modificar" a cadeia de caracteres original, a referência continuará apontar para o objeto original em vez do novo objeto que foi criado quando a cadeia de caracteres foi modificada. O código a seguir ilustra esse comportamento:  
  
 [!code-csharp[csProgGuideStrings#25](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_3.cs)]  
  
 Para saber mais sobre como criar novas cadeias de caracteres que se baseiam em modificações, como operações de pesquisa e substituição na cadeia de caracteres original, confira [Como modificar o conteúdo da cadeia de caracteres](../../how-to/modify-string-contents.md).  
  
## <a name="regular-and-verbatim-string-literals"></a>Literais de cadeia de caracteres regulares e textuais  
 Use literais de cadeia de caracteres regulares quando você precisar inserir caracteres de escape fornecidos por C#, conforme mostrado no seguinte exemplo:  
  
 [!code-csharp[csProgGuideStrings#3](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_4.cs)]  
  
 Use cadeias de caracteres textuais para conveniência e para facilitar a leitura quando o texto da cadeia de caracteres contiver caracteres de barra invertida, por exemplo, em caminhos de arquivo. Como as cadeias de caracteres textuais preservam os caracteres de nova linha como parte do texto da cadeia de caracteres, podem ser usadas para inicializar cadeias de caracteres de várias linhas. Use aspas duplas para inserir uma marca de aspas simples dentro de uma cadeia de caracteres textual. O exemplo a seguir mostra alguns usos comuns para cadeias de caracteres textuais:  
  
 [!code-csharp[csProgGuideStrings#4](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_5.cs)]  
  
## <a name="string-escape-sequences"></a>Sequências de escape de cadeia de caracteres  
  
|Sequência de escape|Nome do caractere|Codificação Unicode|  
|---------------------|--------------------|----------------------|  
|\\'|Aspas simples|0x0027|  
|\\"|Aspas duplas|0x0022|  
|\\\\ |Barra invertida|0x005C|  
|\0|Nulo|0x0000|  
|\a|Alerta|0x0007|  
|\b|Backspace|0x0008|  
|\f|Avanço de página|0x000C|  
|\n|Nova linha|0x000A|  
|\r|Retorno de carro|0x000D|  
|\t|Tabulação horizontal|0x0009|  
|\U|Sequência de escape Unicode para pares substitutos.|\Unnnnnnnn|  
|\u|Sequência de escape Unicode|\u0041 = "A"|  
|\v|Tabulação vertical|0x000B|  
|\x|Sequência de escape Unicode semelhante a "\u", exceto pelo comprimento variável.|\x0041 = "A"|  
  
> [!NOTE]
>  Em tempo de compilação, cadeias de caracteres textuais são convertidas em cadeias de caracteres comuns com as mesmas sequências de escape. Portanto, se exibir uma cadeia de caracteres textual na janela de observação do depurador, você verá os caracteres de escape que foram adicionados pelo compilador, não a versão textual do código-fonte. Por exemplo, a cadeia de caracteres textual @"C:\files.txt" será exibida na janela de inspeção como "C:\\\files.txt".  
  
## <a name="format-strings"></a>Cadeias de caracteres de formato  
 Uma cadeia de caracteres de formato é aquela cujo conteúdo pode ser determinado dinamicamente no tempo de execução. Você cria uma cadeia de caracteres de formato usando o método estático <xref:System.String.Format%2A> e inserindo espaços reservados entre chaves que serão substituídos por outros valores no tempo de execução. O exemplo a seguir usa uma cadeia de caracteres de formato para o resultado de cada iteração de um loop de saída:  
  
 [!code-csharp[csProgGuideStrings#26](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_6.cs)]  
  
 Uma sobrecarga do método <xref:System.Console.WriteLine%2A> usa uma cadeia de caracteres de formato como parâmetro. Portanto, você pode inserir apenas uma cadeia de caracteres de formato literal sem uma chamada explícita ao método. No entanto, se usar o método <xref:System.Diagnostics.Trace.WriteLine%2A> para exibir a saída de depuração na janela de **Saída** do Visual Studio, você precisará chamar explicitamente o método <xref:System.String.Format%2A>, uma vez que <xref:System.Diagnostics.Trace.WriteLine%2A> só aceita uma cadeia de caracteres e não uma cadeia de caracteres de formato. Para saber mais sobre cadeias de caracteres de formato, confira [Tipos de formatação](../../../standard/base-types/formatting-types.md).  
  
## <a name="substrings"></a>Subcadeias de caracteres  
 Uma subcadeia de caracteres é qualquer sequência de caracteres contida em uma cadeia de caracteres. Use o método <xref:System.String.Substring%2A> para criar uma nova cadeia de caracteres com base em uma parte da cadeia de caracteres original. Você pode pesquisar uma ou mais ocorrências de uma subcadeia de caracteres usando o método <xref:System.String.IndexOf%2A>. Use o método <xref:System.String.Replace%2A> para substituir todas as ocorrências de uma subcadeia de caracteres especificada por uma nova cadeia de caracteres. Como o método <xref:System.String.Substring%2A>, <xref:System.String.Replace%2A> retorna, na verdade, uma nova cadeia de caracteres e não a modifica a cadeia de caracteres original. Saiba mais em [Como pesquisar cadeias de caracteres](../../how-to/search-strings.md) e [Como modificar o conteúdo da cadeia de caracteres](../../how-to/modify-string-contents.md).  
  
 [!code-csharp[csProgGuideStrings#7](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_7.cs)]  
  
## <a name="accessing-individual-characters"></a>Acesso a caracteres individuais  
 Você pode usar a notação de matriz com um valor de índice para adquirir acesso somente leitura a caracteres individuais, como no seguinte exemplo:  
  
 [!code-csharp[csProgGuideStrings#9](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_8.cs)]  
  
 Se os métodos <xref:System.String> não fornecerem a funcionalidade necessária para modificar caracteres individuais em uma cadeia de caracteres, você poderá usar um objeto <xref:System.Text.StringBuilder> para modificar os caracteres individuais "in-loco" e criar uma nova cadeia de caracteres para armazenar os resultados usando os métodos <xref:System.Text.StringBuilder>. No exemplo a seguir, suponha que você deva modificar a cadeia de caracteres original de uma maneira específica e armazenar os resultados para uso futuro:  
  
 [!code-csharp[csProgGuideStrings#8](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_9.cs)]  
  
## <a name="null-strings-and-empty-strings"></a>Cadeias de caracteres nulas e cadeias de caracteres vazias  
 Uma cadeia de caracteres vazia é uma instância de um objeto <xref:System.String?displayProperty=nameWithType> que contém zero caractere. As cadeias de caracteres vazias geralmente são usadas em vários cenários de programação para representar um campo de texto em branco. Você pode chamar métodos em cadeias de caracteres vazias porque eles são objetos <xref:System.String?displayProperty=nameWithType> válidos. As cadeias de caracteres vazias são inicializadas da seguinte maneira:  
  
```  
string s = String.Empty;  
```  
  
 Por outro lado, uma cadeia de caracteres nula não se refere a uma instância de um objeto <xref:System.String?displayProperty=nameWithType> e qualquer tentativa de chamar um método em uma cadeia de caracteres nula provocará uma <xref:System.NullReferenceException>. No entanto, você pode usar cadeias de caracteres nulas em operações de comparação e concatenação com outras cadeias de caracteres. Os exemplos a seguir ilustram alguns casos em que uma referência a uma cadeia de caracteres nula faz e não faz com que uma exceção seja lançada:  
  
 [!code-csharp[csProgGuideStrings#27](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_10.cs)]  
  
## <a name="using-stringbuilder-for-fast-string-creation"></a>Uso do StringBuilder para a criação rápida de cadeias de caracteres  
 As operações de cadeia de caracteres no .NET são altamente otimizadas e, na maioria dos casos, não afetam o desempenho de forma significativa. No entanto, em alguns cenários, como loops rígidos que são executados centenas ou milhares de vezes, as operações de cadeia de caracteres podem afetar o desempenho. A classe <xref:System.Text.StringBuilder> cria um buffer de cadeia de caracteres que oferece desempenho melhor se o programa executa várias manipulações de cadeia de caracteres. A cadeia de caracteres <xref:System.Text.StringBuilder> também permite reatribuir caracteres individuais, o que o tipo de dados String interno não dá suporte. Esse código, por exemplo, altera o conteúdo de uma cadeia de caracteres sem criar uma nova cadeia de caracteres:  
  
 [!code-csharp[csProgGuideStrings#20](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_11.cs)]  
  
 Neste exemplo, um objeto <xref:System.Text.StringBuilder> é usado para criar uma cadeia de caracteres com base em um conjunto de tipos numéricos:  
  
 [!code-csharp[csProgGuideStrings#15](../../../csharp/programming-guide/strings/codesnippet/CSharp/index_12.cs)]  
  
## <a name="strings-extension-methods-and-linq"></a>Cadeias de caracteres, métodos de extensão e LINQ  
 Uma vez que o tipo <xref:System.String> implementa <xref:System.Collections.Generic.IEnumerable%601>, você pode usar os métodos de extensão definidos na classe <xref:System.Linq.Enumerable> em cadeias de caracteres. Para evitar a desordem visual, esses métodos são excluídos do IntelliSense para o tipo <xref:System.String>, mas estão disponíveis mesmo assim. Você também pode usar expressões [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] em cadeias de caracteres de consulta. Para saber mais, confira [LINQ e cadeias de caracteres](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md).  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Tópico|Descrição|  
|-----------|-----------------|  
|[Como modificar o conteúdo de uma cadeia de caracteres](../../how-to/modify-string-contents.md)|Ilustra as técnicas para transformar cadeias de caracteres e modificar o conteúdo delas.|  
|[Como comparar cadeias de caracteres](../../how-to/compare-strings.md)|Mostra como executar comparações ordinais e específicas da cultura de cadeias de caracteres.|  
|[Como analisar cadeias de caracteres usando String.Split ](../../how-to/parse-strings-using-split.md)|Contém um exemplo que ilustra como usar o método `String.Split` para analisar cadeias de caracteres.|  
|[Como pesquisar cadeias de caracteres](../../how-to/search-strings.md)|Explica como usar a pesquisa para texto específico ou padrões em cadeias de caracteres.|  
|[Como determinar se uma cadeia de caracteres representa um valor numérico](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)|Mostra como analisar com segurança uma cadeia de caracteres para ver se ela tem um valor numérico válido.|  
|[Como converter uma cadeia de caracteres em um DateTime](../../../csharp/programming-guide/strings/how-to-convert-a-string-to-a-datetime.md)|Mostra como converter uma cadeia de caracteres como "24/01/2008" em um objeto <xref:System.DateTime?displayProperty=nameWithType>.|  
|[Operações básicas de cadeias de caracteres](../../../../docs/standard/base-types/basic-string-operations.md)|Fornece links para tópicos que usam os métodos <xref:System.String?displayProperty=nameWithType> e <xref:System.Text.StringBuilder?displayProperty=nameWithType> para executar operações básicas de cadeia de caracteres.|  
|[Análise de cadeias de caracteres](../../../../docs/standard/base-types/parsing-strings.md)|Descreve como inserir caracteres ou espaços vazios em uma cadeia de caracteres.|  
|[Comparação de cadeias de caracteres](../../../../docs/standard/base-types/comparing.md)|Inclui informações sobre como comparar cadeias de caracteres e fornece exemplos em C# e Visual Basic.|  
|[Uso da classe StringBuilder](../../../standard/base-types/stringbuilder.md)|Descreve como criar e modificar objetos de cadeia de caracteres dinâmica usando a classe <xref:System.Text.StringBuilder>.|  
|[LINQ e Cadeias de Caracteres](../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)|Fornece informações sobre como executar várias operações de cadeia de caracteres usando consultas LINQ.|  
|[Guia de Programação em C#](../../../csharp/programming-guide/index.md)|Fornece links para tópicos que explicam as construções de programação em C#.|  
