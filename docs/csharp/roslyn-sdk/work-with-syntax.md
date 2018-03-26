---
title: Usar o modelo de sintaxe do SDK do .NET Compiler Platform
description: Esta visão geral fornece uma compreensão dos tipos usados para entender e manipular nós de sintaxe.
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 09d07e6257ad7d32d75328a8c1850888b4d0b937
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="work-with-syntax"></a>Trabalhar com sintaxe

A **árvore de sintaxe** é uma estrutura de dados fundamental exposta pelas APIs do compilador. Essas árvores representam a estrutura lexical e sintática do código-fonte. Elas servem duas finalidades importantes:

1. Permitir que ferramentas – como um IDE, suplementos, ferramentas de análise de código e refatorações – vejam e processem a estrutura sintática do código-fonte no projeto do usuário.
2. Permitir que ferramentas – como refatorações e um IDE – criem, modifiquem e reorganizem o código-fonte de uma maneira natural sem a necessidade de uso de edições de texto diretas. Criando e manipulando árvores, as ferramentas podem criar e reorganizar o código-fonte com facilidade.

## <a name="syntax-trees"></a>Árvores de sintaxe

Árvores de sintaxe são a estrutura principal usada para compilação, análise de código, associação, refatoração, recursos de IDE e geração de código. Nenhuma parte do código-fonte é entendida sem primeiro ser identificada e categorizada em um dos muitos elementos de linguagem estrutural conhecidos. 

As árvores de sintaxe têm três atributos-chave. O primeiro atributo é que as árvores de sintaxe mantêm todas as informações de origem em fidelidade total. Isso significa que a árvore de sintaxe contém cada informação encontrada no texto de origem, cada constructo gramatical, cada token lexical e todo o resto, incluindo espaço em branco, comentários e diretivas do pré-processador. Por exemplo, cada literal mencionado na fonte é representado exatamente como foi digitado. As árvores de sintaxe também representam erros no código-fonte quando o programa está incompleto ou mal-formado, com a representação de tokens ignorados ou ausentes na árvore de sintaxe.  

Isso possibilita o segundo atributo das árvores de sintaxe. Uma árvore de sintaxe obtida do analisador pode produzir o texto exato com base no qual ela foi analisada. Em qualquer nó de sintaxe, é possível obter a representação de texto da subárvore com raiz nesse nó. Isso significa que as árvores de sintaxe podem ser usadas como uma maneira de construir e editar o texto de origem. Ao criar uma árvore, por implicação, você criou o texto equivalente e, ao editar uma árvore de sintaxe criando uma nova árvore com base nas alterações de uma árvore existente, você editou o texto efetivamente. 

O terceiro atributo das árvores de sintaxe é que elas são imutáveis e thread-safe.  Isso significa que, depois que uma árvore é obtida, ela é um instantâneo do estado atual do código e nunca é alterada. Isso permite que vários usuários interajam com a mesma árvore de sintaxe ao mesmo tempo em threads diferentes sem bloqueio nem duplicação. Como as árvores são imutáveis e nenhuma modificação pode ser feita diretamente em uma árvore, os métodos de fábrica ajudam a criar e modificar árvores de sintaxe criando instantâneos adicionais da árvore. As árvores são eficientes no modo como reutilizam os nós subjacentes, de forma que uma nova versão possa ser recompilada rapidamente e com pouca memória extra.

Uma árvore de sintaxe é literalmente uma estrutura de dados de árvore, em que os elementos estruturais não terminais são pais de outros elementos. Cada árvore de sintaxe é composta por nós, tokens e desafios.  

## <a name="syntax-nodes"></a>Nós de sintaxe

Nós de sintaxe são um dos elementos principais das árvores de sintaxe. Esses nós representam os constructos sintáticos como declarações, instruções, cláusulas e expressões. Cada categoria de nós de sintaxe é representada por uma classe separada derivada de <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. O conjunto de classes de nó não é extensível. 

Todos os nós de sintaxe são nós não terminais na árvore de sintaxe, o que significa que eles sempre têm outros nós e tokens como filhos. Como filho de outro nó, cada nó tem um nó pai que pode ser acessado por meio da propriedade <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType>. Como os nós e as árvores são imutáveis, o pai de um nó nunca é alterado. A raiz da árvore tem um pai nulo.  

Cada nó tem um método <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType>, que retorna uma lista de nós filho em ordem sequencial com base em sua posição no texto de origem. Essa lista não contém tokens. Cada nó também tem métodos para examinar os Descendentes, como <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A> ou <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> – que representam uma lista de todos os nós, tokens ou desafios, que existem na subárvore com raiz nesse nó.  

Além disso, cada subclasse de nó de sintaxe expõe os mesmos filhos por meio de propriedades fortemente tipadas. Por exemplo, uma classe de nó <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> tem três propriedades adicionais específicas aos operadores binários: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> e <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. O tipo de <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> e <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> é <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax> e o tipo de <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> é <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Alguns nós de sintaxe têm filhos opcionais. Por exemplo, um <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> tem um <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax> opcional. Se o filho não estiver presente, a propriedade retornará nulo. 

## <a name="syntax-tokens"></a>Tokens de sintaxe

Os tokens de sintaxe são os terminais da gramática da linguagem, que representam os menores fragmentos sintáticos do código. Eles nunca são os pais de outros nós ou tokens. Os tokens de sintaxe consistem em palavras-chave, identificadores, literais e pontuação. 

Para fins de eficiência, o tipo <xref:Microsoft.CodeAnalysis.SyntaxToken> é um tipo de valor CLR. Portanto, ao contrário dos nós de sintaxe, há apenas uma estrutura para todos os tipos de tokens com uma combinação de propriedades que têm significado, dependendo do tipo de token que está sendo representado.

Por exemplo, um token literal inteiro representa um valor numérico. Além do texto de origem não processado abrangido pelo token, o token literal tem uma propriedade <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> que informa o valor inteiro decodificado exato. Essa propriedade é tipada como <xref:System.Object> porque pode ser um dos muitos tipos primitivos.

A propriedade <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> indica as mesmas informações que a propriedade <xref:Microsoft.CodeAnalysis.SyntaxToken.Value>; no entanto, essa propriedade sempre é tipada como <xref:System.String>. Um identificador no texto de origem C# pode incluir caracteres de escape Unicode, embora a sintaxe da sequência de escape em si não seja considerada parte do nome do identificador. Portanto, embora o texto não processado abrangido pelo token inclua a sequência de escape, isso não ocorre com a propriedade <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText>. Em vez disso, ela inclui os caracteres Unicode identificados pelo escape. Por exemplo, se o texto de origem contiver um identificador gravado como `\u03C0`, a propriedade <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> desse token retornará `π`.

## <a name="syntax-trivia"></a>Desafios de sintaxe

Os desafios de sintaxe representam as partes do texto de origem que são amplamente insignificantes para compreensão normal do código, como espaço em branco, comentários e diretivas do pré-processador. Assim como os tokens de sintaxe, os desafios são tipos de valor. O único tipo <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> é usado para descrever todos os tipos de desafios.

Como os desafios não fazem parte da sintaxe de linguagem normal e podem aparecer em qualquer lugar entre dois tokens quaisquer, eles não são incluídos na árvore de sintaxe como um filho de um nó. Apesar disso, como eles são importantes ao implementar um recurso como refatoração e para manter fidelidade total com o texto de origem, eles existem como parte da árvore de sintaxe.

Acesse os desafios inspecionando as coleções <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> ou <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> de um token. Quando o texto de origem é analisado, sequências de desafios são associadas aos tokens. Em geral, um token possui qualquer desafio após ele na mesma linha até o próximo token. Qualquer desafio após essa linha é associado ao próximo token. O primeiro token no arquivo de origem obtém todos as desafios iniciais e a última sequência de desafios no arquivo é anexada ao token de fim do arquivo, que, de outro modo, tem largura zero.

Ao contrário dos nós e tokens de sintaxe, os desafios de sintaxe não têm pais. Apesar disso, como eles fazem parte da árvore e cada um deles é associado um único token, você poderá acessar o token ao qual ele está associado usando a propriedade <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType>.

## <a name="spans"></a>Intervalos

Cada nó, token ou desafio conhece sua posição dentro do texto de origem e o número de caracteres no qual ele consiste. Uma posição de texto é representada como um inteiro de 32 bits, que é um índice `char` baseado em zero. Um objeto <xref:Microsoft.CodeAnalysis.Text.TextSpan> é a posição inicial e uma contagem de caracteres, ambas representadas como inteiros. Se <xref:Microsoft.CodeAnalysis.Text.TextSpan> tem comprimento zero, ele se refere a um local entre dois caracteres.

Cada nó tem duas <xref:Microsoft.CodeAnalysis.Text.TextSpan> propriedades: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> e <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>. 

A propriedade <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> é o intervalo de texto do início do primeiro token na subárvore do nó ao final do último token. Esse intervalo não inclui nenhum desafio à esquerda ou à direita.

A propriedade <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> é o intervalo de texto que inclui o intervalo normal do nó mais o intervalo de qualquer desafio à esquerda ou à direita.

Por exemplo: 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

O nó de instrução dentro do bloco tem um intervalo indicado pelas barras verticais simples (|). Ele inclui os caracteres `throw new Exception("Not right.");`. O intervalo total é indicado pelas barras verticais duplas (||). Ele inclui os mesmos caracteres do intervalo e os caracteres associados ao desafio à esquerda e à direita.

## <a name="kinds"></a>Variantes

Cada nó, token ou desafio tem uma propriedade <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType>, do tipo <xref:System.Int32?displayProperty=nameWithType>, que identifica o elemento de sintaxe exato representado. Esse valor pode ser convertido em uma enumeração específica a uma linguagem; cada linguagem, C# ou VB, tem uma única enumeração `SyntaxKind` (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> e <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>, respectivamente) que lista todos os possíveis elementos de nós, tokens e desafios na gramática. Esta conversão pode ser feita automaticamente acessando o <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> ou <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> métodos de extensão.

A propriedade <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> permite a desambiguidade fácil de tipos de nó de sintaxe que compartilham a mesma classe de nó. Para tokens e desafios, essa propriedade é a única maneira de diferenciar um tipo de elemento de outro. 

Por exemplo, uma única classe <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> tem <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> e <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> como filhos. A propriedade <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> distingue se ela é um tipo <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression> ou <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> de nó de sintaxe.

## <a name="errors"></a>Erros

Mesmo quando o texto de origem contém erros de sintaxe, uma árvore de sintaxe completa com ida e volta para a origem é exposta. Quando o analisador encontra um código que não está em conformidade com a sintaxe definida da linguagem, ele usa uma das duas técnicas para criar uma árvore de sintaxe.

Primeiro, se o analisador espera determinado tipo de token, mas não o encontra, ele pode inserir um token ausente na árvore de sintaxe no local em que o token era esperado. Um token ausente representa o token real que era esperado, mas tem um intervalo vazio e sua propriedade <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> retorna `true`.

Em segundo lugar, o analisador pode ignorar tokens até encontrar um no qual pode continuar a análise. Nesse caso, os tokens ignorados são anexados como um nó de desafio com o tipo <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
