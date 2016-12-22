---
title: "What&#39;s New for Visual C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9f18dc26-27fa-4603-a639-b573f07a117b
caps.latest.revision: 39
caps.handback.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# What&#39;s New for Visual C# #
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Esta página lista os nomes dos recursos principais para cada versão do c\# com descrições dos recursos novos e aprimorados na versão mais recente da linguagem.  
  
## Versões anteriores  
 C\# 1, o Visual Studio .NET 2002  
 Primeira versão  
  
 C\# 1.1, Visual Studio .NET 2003  
 `#line` pragma e xml comentários doc  
  
 C\# 2, o Visual Studio .NET 2005  
 Métodos anônimos, genéricos, tipos anuláveis, iteradores\/yield, `static` classes, variação de co\/compensado para delegados  
  
 C\# 3, o Visual Studio 2008 .NET  
 Inicializadores de objeto e coleção, expressões lambda, métodos de extensão, tipos anônimos, propriedades automáticas, LINQ Language Integrated Query \(\), tipos anônimos, locais `var` inferência de tipos, LINQ  
  
 C\# 4, o Visual Studio 2010 do .NET  
 `Dynamic`, chamado de argumentos, parâmetros opcionais, covariância genérica\/compensado variação  
  
 C\# 5, o Visual Studio 2012 do .NET  
 `Async` \/ `await`, atributos de informações do chamador  
  
 O Visual Studio .NET 2013  
 Correções de bugs, aprimoramentos de desempenho e visualizações de tecnologia do .NET Compiler Platform \("Roslyn"\)  
  
 C\# 6, o Visual Studio .NET 2015  
 Versão atual, consulte abaixo  
  
## Versão atual  
 [nome](../../csharp/language-reference/keywords/nameof.md)  
 Você pode obter o nome de cadeia de caracteres não qualificado de um tipo ou membro para uso em uma mensagem de erro sem embuti uma cadeia de caracteres.  Isso permite que seu código permaneça correto quando a refatoração.  Esse recurso também é útil para conectar links MVC model\-view\-controller e acionar eventos de propriedade alterada.  
  
 [Interpolação de cadeia de caracteres](../../csharp/language-reference/keywords/interpolated-strings.md)  
 Você pode usar expressões de interpolação de cadeia de caracteres para construir cadeias de caracteres.  Uma expressão de cadeia de caracteres interpolados se parece com uma cadeia de caracteres de modelo que contém expressões.  C\# cria uma cadeia de caracteres, substituindo as expressões com o represenations ToString dos resultados de expressões.  Uma cadeia de caracteres interpolada é mais fácil compreender em relação a argumentos que [Formatação composta](../Topic/Composite%20Formatting.md).  
  
 [Acesso de membro NULL condicional e indexação](../../csharp/language-reference/operators/null-conditional-operators.md)  
 Você pode testar null de maneira muito clara sintática antes de executar um acesso de membro \(`?.`\) ou índice \(`?[]`\) operação.  Esses operadores ajudarão\-lo a escrever menos código para lidar com null verifica, especialmente em ordem decrescente em estruturas de dados.  Se a referência de objeto ou operando esquerda for nula, as operações retorna null.  
  
 [Inicializadores de índice](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 Agora você pode inicializar os elementos específicos de uma coleção que oferece suporte à indexação, como inicializar um dicionário.  
  
 [Inicializador de coleção e adicionar métodos de extensão](../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 Você pode usar os inicializadores para coleções agora quando a coleção tem um método de extensão adicionar.  Anteriormente, o método Add tinha de ser um método de instância.  
  
 **Resolução de sobrecarga**  
 O compilador melhorou a resolução de sobrecarga que resulta em mais código acabou funcionando como esperado ela se comporta.  Um lugar onde você pode interromper a observar um problema é ao escolher entre sobrecargas colocar tipos de valor anulável ou ao transmitir grupos de método \(em vez de lambdas\) para sobrecargas que adotam delegados.  
  
 [Filtros de exceção](../../csharp/language-reference/keywords/try-catch.md)  
 Você pode usar filtros de exceção em `catch` cláusulas para determinar se uma cláusula catch deve tratar a exceção.  Sem esse recurso, você precisa relançar a exceção, que Recorta a pilha de chamadas relatada na exceção gerada novamente.  
  
 [Await em Catch e blocos Finally](../../csharp/language-reference/keywords/try-catch.md)  
 Você pode usar `await` no `catch` e `finally` cláusulas.  
  
 [Inicializadores de propriedade automaticamente](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 Você pode inicializar propriedades automáticas agora da mesma forma que como inicializar campos.  
  
 [Auto\-propriedades somente getter](../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)  
 Você pode definir propriedades automáticas somente leitura agora sem precisar definir uma propriedade com a sintaxe de propriedade completa.  Você pode inicializar a propriedade onde você declará\-la ou no construtor do tipo.  
  
 **Membros da função com corpos de expressão**  
 Você pode declarar membros com corpos de expressão de código no mesmo leve sintaxe usada com expressões lambda.  Consulte [Métodos](../../fsharp/language-reference/members/methods.md), [Propriedades](../../csharp/programming-guide/classes-and-structs/properties.md), [Indexadores](../../csharp/programming-guide/indexers/index.md), e [Operadores sobrecarregáveis](../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md).  
  
 [Usando estático](../../csharp/language-reference/keywords/using-directive.md)  
 Você pode importar acessíveis membros estáticos de tipos estáticos para que você pode consultar os membros sem qualificar o acesso com o nome do tipo.  
  
## Consulte também  
 [O que há de novo no Visual Studio 2015](/visual-studio/ide/what-s-new-in-visual-studio-2015)