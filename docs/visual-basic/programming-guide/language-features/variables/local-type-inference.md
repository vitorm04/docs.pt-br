---
title: "Infer&#234;ncia de tipo local (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "local type inference"
  - "vb.TypeInfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variáveis locais de tipo implícito [Visual Basic]"
  - "inferência [Visual Basic]"
  - "inferência de tipos local [Visual Basic]"
  - "instrução Option Infer"
  - "inferência de tipos [Visual Basic]"
  - "variáveis [Visual Basic], inferência de tipos"
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: 43
caps.handback.revision: 43
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Infer&#234;ncia de tipo local (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O compilador Visual Basic usa  *inferência de tipo* para determinar os tipos de dados de variáveis locais declarados sem um `As` cláusula.  O compilador infere o tipo da variável do tipo da expressão de inicialização.  Isso permite que você declarar variáveis sem explicitamente indicando um tipo, conforme mostrado no exemplo a seguir. Como resultado de declarações de, ambos `num1` e `num2` tem rigidez de tipos como inteiros.  
  
 [!CODE [VbVbalrTypeInference#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTypeInference#1)]  
  
> [!NOTE]
>  Se você não quiser `num2` no exemplo anterior para ser digitadas como um `Integer`, você pode especificar outro tipo, usando uma declaração como `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.  
  
 Inferência de tipo local aplica\-se no nível de procedimento.  Ele não pode ser usado para declarar variáveis no nível de módulo \(dentro de uma classe, estrutura, módulo ou interface mas não em um procedimento ou bloco\).  Se `num2` no exemplo anterior foram um campo de uma classe em vez de uma variável local em um procedimento, a declaração poderia causar um erro com `Option Strict` e seria classificar `num2` como um `Object` com `Option Strict` logoff.  Da mesma forma, a inferência de tipo local não se aplica a variáveis de nível de procedimento declaradas como `Static`.  
  
## Digite inferência vs.Ligação tardia  
 Código que usa inferência se parece com o código que depende de ligação tardia.  No entanto, inferência de tipos a variável em vez de deixá\-la como altamente `Object`.  O compilador usa o inicializador de uma variável para determinar o tipo da variável em tempo de compilação para produzir código early\-bound.  No exemplo anterior, `num2`, like `num1`, é digitada como uma `Integer`.  
  
 O comportamento de variáveis early\-bound difere das variáveis de ligação tardia, para o qual o tipo é conhecido somente em tempo de execução.  Saber o tipo mais cedo, permite que o compilador identificar problemas antes da execução, alocar memória com precisão e executar outras otimizações.  Vinculação antecipada também permite que o ambiente de desenvolvimento integrado \(IDE\) para fornecer ajuda de IntelliSense sobre os membros de um objeto Visual Basic.  Vinculação antecipada também é preferida para o desempenho.  Isso ocorre porque todos os dados armazenados em uma variável de ligação tardia devem ser dispostos como tipo de `Object`, e acessar os membros do tipo em tempo de execução faz com que o programa mais lento.  
  
## Exemplos  
 Inferência de tipo ocorre quando uma variável local é declarada sem uma `As` cláusula e inicializado.  O compilador usa o tipo do valor inicial atribuído como o tipo da variável.  Por exemplo, cada uma das linhas de código a seguir declara uma variável do tipo `String`.  
  
 [!CODE [VbVbalrTypeInference#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTypeInference#2)]  
  
 O código a seguir demonstra duas formas equivalentes para criar uma matriz de inteiros.  
  
 [!CODE [VbVbalrTypeInference#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTypeInference#3)]  
  
 É conveniente usar inferência de tipo para determinar o tipo de uma variável de controle de loop.  No código a seguir, o compilador infere que `number` é um `Integer` porque `someNumbers2` do exemplo anterior é uma matriz de inteiros.  
  
 [!CODE [VbVbalrTypeInference#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTypeInference#4)]  
  
 Inferência de tipo local pode ser usada em `Using` instruções para estabelecer o tipo de nome do recurso, como o exemplo a seguir demonstra.  
  
 [!CODE [VbVbalrTypeInference#7](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTypeInference#7)]  
  
 O tipo de uma variável pode ser deduzido dos valores retornados de funções, como o exemplo a seguir demonstra.  Ambos `pList1` e `pList2` são matrizes de processos, pois `Process.GetProcesses` retorna uma matriz de processos.  
  
 [!CODE [VbVbalrTypeInference#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrTypeInference#5)]  
  
## Option Infer  
 `Option Infer`que permite que especificar se a inferência de tipo local é permitida em um arquivo em particular.  Para permitir ou bloquear a opção, digite uma das instruções a seguir no início do arquivo.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Se você não especificar um valor para `Option Infer` no seu código, o padrão do compilador é `Option Infer On`.  Para projetos atualizados a partir de [!INCLUDE[vb_orcas_long](../../../../visual-basic/misc/includes/vb_orcas_long_md.md)] ou versões anteriores, o padrão do compilador é `Option Infer Off`.  
  
 Se o valor definido para `Option Infer`em um arquivo conflita com o valor definido no IDE ou na linha de comando, o valor no arquivo possui precedência.  
  
 Para obter mais informações, consulte [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) e [Página de Compilação, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic).  
  
## Restrições  
 Inferência de tipo pode ser usada somente para as variáveis locais não\-static; ele não pode ser usado para determinar o tipo de funções, propriedades ou campos de classe.  
  
## Consulte também  
 [Tipos anônimos](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Associação antecipada e tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)   
 [Instrução For...Next](../../../../visual-basic/language-reference/statements/for-next-statement.md)   
 [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [\/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)