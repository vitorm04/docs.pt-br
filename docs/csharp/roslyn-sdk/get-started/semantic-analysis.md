---
title: "Introdução à análise semântica"
description: "Este tutorial fornece uma visão geral de como trabalhar com análise semântica usando o SDK do .NET Compiler."
author: billwagner
ms.author: wiwagn
ms.date: 02/06/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 94a28d21cfec1894c3ee3b631335043e1d0ec817
ms.sourcegitcommit: d95a91d685565f4d95c8773b558752864a6a3d7e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2018
---
# <a name="get-started-with-semantic-analysis"></a>Introdução à análise semântica

Este tutorial presume que você está familiarizado com a API de sintaxe. O artigo [Introdução à a análise de sintaxe](syntax-analysis.md) fornece uma introdução suficiente.

Neste tutorial, você explora as APIs de **Símbolo** e de **Associação**. Essas APIs fornecem informações sobre o _significado semântico_ de um programa. Elas permitem fazer e responder perguntas sobre os tipos representado por qualquer símbolo em seu programa.

## <a name="understanding-compilations-and-symbols"></a>Noções básicas sobre compilações e símbolos

Conforme você trabalha mais com o SDK do .NET Compiler, você se familiariza com as distinções entre a API de Sintaxe e a API de Semântica. A **API de Sintaxe** permite que você examine a _estrutura_ de um programa. Muitas vezes, no entanto, você deseja as informações sobre a semântica ou _significado_ de um programa. Enquanto um trecho ou arquivo de código livre VB ou C# pode ser analisado sintaticamente de modo isolado, não faz sentido fazer a esmo perguntas como "qual é o tipo dessa variável". O significado de um nome de tipo pode ser dependente de referências de assembly, importações de namespace ou outros arquivos de código. Essas perguntas são respondidas usando-se a **API de Semântica**, especificamente a classe <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType>.

Uma instância de <xref:Microsoft.CodeAnalysis.Compilation> é análoga a um único projeto conforme visto pelo compilador e representa tudo o que é necessário para compilar um programa Visual Basic ou C#. A **compilação** inclui o conjunto de arquivos de origem a serem compilados, referências de assembly e opções de compilador. Você pode avaliar o significado do código usando todas as outras informações neste contexto. Um <xref:Microsoft.CodeAnalysis.Compilation> permite que você encontre **símbolos** – entidades como tipos, namespaces, membros e variáveis aos quais os nomes e outras expressões se referem. O processo de associar nomes e expressões com **símbolos** é chamado de **associação**.

Assim como <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> é uma classe abstrata com derivativos específicos a um idioma. Ao criar uma instância de compilação, você deve invocar um método de fábrica na classe <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (ou <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>).

## <a name="querying-symbols"></a>Consultar símbolos

Neste tutorial, você analisa novamente o programa "Olá, Mundo". Dessa vez, você consulta os símbolos no programa para compreender quais tipos esses símbolos representam. Você consulta os tipos em um namespace e aprende a localizar os métodos disponíveis em um tipo.

> [!IMPORTANT]
> As amostras a seguir exigem que o **SDK do .NET Compiler** esteja instalado como parte do Visual Studio 2017. Você pode encontrar o SDK do .NET Compiler como o último componente opcional listado sob a carga de trabalho do **Desenvolvimento de extensão do Visual Studio**. Os modelos não são instalados sem esse componente.

Você pode ver o código concluído para essa amostra no [nosso repositório do GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Os tipos de árvore de sintaxe usam a herança para descrever os elementos de sintaxe diferentes que são válidos em locais diferentes no programa. Usar essas APIs geralmente significa converter propriedades ou membros da coleção em tipos derivados específicos. Nos exemplos a seguir, a atribuição e as conversões são instruções separadas, usando variáveis explicitamente tipadas. Você pode ler o código para ver os tipos de retorno da API e o tipo de tempo de execução dos objetos retornados. Na prática, é mais comum usar variáveis implicitamente tipadas e depender de nomes de API para descrever o tipo de objeto que está sendo examinado.

Criar um novo projeto de **Ferramenta de Análise de Código Autônoma** do C#:

* No Visual Studio, escolha **Arquivo** > **Novo** > **Projeto** para exibir a caixa de diálogo Novo Projeto.
* Em **Visual C#** > **Extensibilidade**, escolha **Ferramenta de Análise de Código Autônoma**.
* Nomeie o projeto "**SemanticQuickStart**" e clique em OK.

Você analisará o programa "Olá, Mundo!" básico mostrado anteriormente.
Adicione o texto ao programa Olá, Mundo como uma constante em sua classe `Program`:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Em seguida, adicione o código a seguir para criar a árvore de sintaxe para o texto do código na constante `programText`.  Adicione a seguinte linha ao seu método `Main`:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Em seguida, compile uma <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> da árvore que você já criou. A amostra "Olá, Mundo" depende dos tipos <xref:System.String> e <xref:System.Console>. Você precisa fazer referência ao assembly que declara esses dois tipos em sua compilação. Adicione a seguinte linha ao seu método `Main` para criar uma compilação de sua árvore de sintaxe, incluindo a referência ao assembly apropriado:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

O método <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> adiciona referências à compilação. O método <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> carrega um assembly como uma referência. 

## <a name="querying-the-semantic-model"></a>Consultar o modelo semântico

Assim que você tiver uma <xref:Microsoft.CodeAnalysis.Compilation>, você poderá solicitar a ela um <xref:Microsoft.CodeAnalysis.SemanticModel> para qualquer <xref:Microsoft.CodeAnalysis.SyntaxTree> contida nessa <xref:Microsoft.CodeAnalysis.Compilation>. Você pode pensar no modelo semântico como a origem de todas as informações normalmente obtidas do IntelliSense. Um <xref:Microsoft.CodeAnalysis.SemanticModel> pode responder a perguntas como "O que são nomes no escopo nesse local?", "Quais membros são acessíveis deste método?", "Quais variáveis são usadas neste bloco de texto?" e "A que este nome/expressão se refere?" Adicione esta instrução para criar o modelo semântico:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Associar um nome

A <xref:Microsoft.CodeAnalysis.Compilation> cria o <xref:Microsoft.CodeAnalysis.SemanticModel> da <xref:Microsoft.CodeAnalysis.SyntaxTree>. Depois de criar o modelo, você pode consultar para localizar a primeira diretiva `using` e recuperar as informações de símbolo para o namespace `System`. Adicione estas duas linhas a seu método `Main` para criar o modelo semântico e recuperar o símbolo para a primeira instrução using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

O código anterior mostra como associar o nome na primeira diretiva `using` para recuperar um <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> para o namespace `System`. O código anterior também ilustra o uso da **sintaxe de modelo** para localizar a estrutura do código; você usa o **modelo semântico** para entender seu significado. A **sintaxe de modelo** localiza a cadeia de caracteres `System` na instrução using. O **modelo semântico** tem todas as informações sobre os tipos definidos no namespace `System`.

Do objeto <xref:Microsoft.CodeAnalysis.SymbolInfo>, você pode obter o <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> usando a propriedade <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType>. Essa propriedade retorna o símbolo a que essa expressão se refere. Para expressões que não se referem a nada (como literais numéricos), essa propriedade é `null`. Quando o <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> não for null, o <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> denotará o tipo do símbolo. Nesse exemplo, a propriedade <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> é um <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Adicione o código a seguir ao método `Main`. Ele recupera o símbolo para o namespace `System` e, em seguida, exibe todos os namespaces filho declarados no namespace `System`:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Execute o programa e você deverá ver a seguinte saída:

```
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> A saída não inclui todos os namespaces que são namespaces filhos do namespace `System`. El exibe cada namespace presente nessa compilação, que só referencia o assembly em que `System.String` é declarada. Quaisquer outros namespaces declarados em outros assemblies não são conhecidos desta compilação

### <a name="binding-an-expression"></a>Associar uma expressão

O código anterior mostra como encontrar um símbolo associando-o a um nome. Há outras expressões em um programa C# que podem ser associadas que não são nomes. Para demonstrar essa capacidade, acessaremos a associação a um único literal de cadeia de caracteres.

O programa "Olá, Mundo" contém um <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, a cadeia de caracteres "Olá, Mundo!" exibida pelo console.

Você localiza a cadeia de caracteres "Olá, Mundo!" localizando o único literal de cadeia de caracteres no programa. Em seguida, depois de localizar o nó de sintaxe, você obtém as informações de tipo para esse nó do modelo semântico. Adicione o código a seguir ao método `Main`:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

O struct <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> inclui uma propriedade <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> que permite o acesso às informações semânticas sobre o tipo do literal. Neste exemplo, ele é do tipo `string`. Adicione uma declaração que atribui essa propriedade a uma variável local:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Para concluir este tutorial, criaremos uma consulta LINQ que criará uma sequência de todos os métodos públicos declarados no tipo `string` que retorna um `string`. Essa consulta torna-se complexa, então a compilaremos linha a linha e então a reconstruiremos como uma única consulta. A ordem desta consulta é a sequência de todos os membros declarados no tipo `string`:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Essa sequência de origem contém todos os membros, incluindo propriedades e campos, portanto, filtre-a usando o método <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> para localizar elementos que são objetos <xref:Microsoft.CodeAnalysis.IMethodSymbol?diplayProperty=nameWithType>:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Em seguida, adicione outro filtro para retornar somente os métodos que são públicos e retornam um `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Selecione apenas a propriedade de nome e somente os nomes distintos, removendo quaisquer sobrecargas:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Você pode também compilar a consulta completa usando a sintaxe de consulta LINQ e, em seguida, exibir todos os nomes de método no console:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Build and display the results of the query.")]

Compile e execute o programa. Você deverá ver a seguinte saída:

```
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```
Você usou a API de semântica para localizar e exibir informações sobre os símbolos que fazem parte deste programa.
