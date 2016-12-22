---
title: "Estruturas e classes (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic]"
  - "classes [Visual Basic], x estruturas"
  - "variáveis de estrutura"
  - "estruturas"
  - "estruturas, em comparação com classes"
  - "estruturas, variáveis de estrutura"
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estruturas e classes (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] unifica a sintaxe para estruturas e classes, com o resultado que ambas as entidades suportam a maioria dos mesmos recursos.  No entanto, também existem diferenças importantes entre as estruturas e classes.  
  
 Classes têm a vantagem de ser tipos de referência — passar uma referência é mais eficiente do que passar uma variável de estrutura com todos os seus dados.  Por outro lado, as estruturas não requerem alocação de memória na pilha global.  
  
 Como você não pode herdar de uma estrutura, estruturas devem ser usadas somente para objetos que não precisam ser estendidos.  Use estruturas quando o objeto que você deseja criar tem uma instância de tamanho pequeno e leve em conta as características de desempenho de classes versus estruturas.  
  
## Semelhanças  
 Estruturas e classes são semelhantes nos seguintes aspectos:  
  
-   Ambas são tipos *continente*, o que significa que elas contêm outros tipos como membros.  
  
-   Ambas tem membros, que podem incluir construtores, métodos, propriedades, campos, constantes, enumerações, eventos e manipuladores de eventos.  No entanto, não confunda esses membros com o *elementos* declarado de uma estrutura.  
  
-   Membros de ambas podem ter níveis de acesso individualizados.  Por exemplo, um membro pode ser `Public` declarado e outro `Private`.  
  
-   Ambas podem implementar interfaces.  
  
-   Ambas podem te construtores compartilhados, com ou sem parâmetros.  
  
-   Ambos podem expor uma  *propriedade padrão* , desde que a propriedade aceite pelo menos um parâmetro.  
  
-   Ambas podem declarar e disparar eventos, e ambas podem declarar representantes.  
  
## Diferenças  
 Estruturas e classes diferem nas particularidades a seguir:  
  
-   Estruturas são   *tipos de valor* ; classes são  *tipos de referência*.  Uma variável de um tipo de estrutura contém a estrutura dos dados, em vez de conter uma referência para os dados como um tipo de classe teria.  
  
-   Estruturas usam alocação da pilha \(stack\); classes usam alocação da heap.  
  
-   Todos os elementos de estrutura são `Public` por padrão; variáveis de classe e constantes são `Private` por padrão, enquanto outros membros da classe são `Public` por padrão.  Esse comportamento para membros de classe fornece compatibilidade com o sistema de padrões do Visual Basic 6.0.  
  
-   Uma estrutura deve ter pelo menos uma variável não compartilhada ou evento não compartilhado e não personalizado; uma classe pode ser completamente vazia.  
  
-   Elementos de estrutura não podem ser declarados como `Protected`; membros de classe podem.  
  
-   Um procedimento de estrutura pode manipular eventos somente se ele é um procedimento [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` e somente por meio de [Instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md); qualquer procedimento de classe pode manipular eventos, usando a palavra\-chave [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) ou a instrução `AddHandler`.  Para obter mais informações, consulte [Eventos](../../../../visual-basic/programming-guide/language-features/events/events.md).  
  
-   Declarações de variável de estrutura não podem especificar inicializadores ou tamanhos iniciais para matrizes; declarações de variável de classe podem.  
  
-   Estruturas implicitamente herdam da classe <xref:System.ValueType?displayProperty=fullName> e não podem herdar de nenhum outro tipo; classes podem herdar de qualquer classe ou classes diferentes de <xref:System.ValueType?displayProperty=fullName>.  
  
-   Estruturas não são herdáveis;  classes são.  
  
-   Estruturas são nunca finalizadas, portanto, a Common Language Runtime \(CLR\) nunca chama o método <xref:System.Object.Finalize%2A> em qualquer estrutura; as classes são finalizadas pelo coletor de lixo \(GC\), que chama <xref:System.Object.Finalize%2A> em uma classe quando ele detecta que não á referências ativas restantes.  
  
-   Uma estrutura não requer um construtor; uma classe requer.  
  
-   Estruturas podem ter construtores compartilhados somente se elas tiverem parâmetros; classes podem tê\-los com ou sem parâmetros.  
  
 Cada estrutura tem um construtor público implícito sem parâmetros.  Esse construtor inicializa todos os elementos de dados da estrutura para seus valores padrão.  Você não pode redefinir esse comportamento.  
  
## Instâncias e Variáveis  
 Como estruturas são tipos de valor, cada variável de estrutura é permanentemente é acoplada a uma instância estrutura individual.  Mas classes são tipos de referência, e um variável de objeto pode referir\-se a várias instâncias de classe em momentos diferentes.  Essa distinção afeta o uso de classes e as estruturas das seguintes maneiras:  
  
-   **Inicialização.** Uma variável de estrutura implicitamente inclui uma inicialização dos elementos usando a estrutura do construtor sem parâmetros.  Portanto, `Dim s As struct1` é equivalente a `Dim s As struct1 = New struct1()`.  
  
-   **Atribuindo variáveis.** Quando você atribui uma variável de estrutura a outra, ou passa uma instância de estrutura para um argumento de procedimento, os valores atuais de todos os elementos de variáveis são copiados para a nova estrutura.  Quando você atribui uma variável de objeto a outra, ou passa um variável de objeto para um procedimento, somente o ponteiro de referência é copiado.  
  
-   **Atribuindo Nothing.** Você pode atribuir o valor [nada](../../../../visual-basic/language-reference/nothing.md) para uma estrutura variável, mas a instância continua a ser associado à variável.  Você ainda pode chamar seus métodos e acessar seus elementos de dados, embora os elementos de variável sejam reinicializados pela atribuição.  
  
     Por outro lado, se você definir um variável de objeto como `Nothing`, você o dissocia de qualquer instância de classe, e não pode acessar todos os membros através da variável até que você atribua uma outra instância a ela.  
  
-   **Várias Instâncias.** Uma variável de objeto pode ter instâncias de classe diferente atribuídas a ela em diferentes momentos, e várias variáveis de objeto podem referir\-se à mesma instância de classe ao mesmo tempo.  As alterações que você fizer nos valores de membros de classe afetarão esses membros quando acessados por outra variável apontando para a mesma instância.  
  
     Elementos de estrutura, no entanto, estão isolados dentro sua própria instância.  Alterações em seus valores não serão refletidas em qualquer outra variável de estrutura, mesmo em outras instâncias da mesma declaração `Structure`.  
  
-   **Igualdade.** Teste de igualdade de duas estruturas deve ser executado com um teste elemento\-por\-elemento.  Duas variáveis de objeto podem ser comparadas com o <xref:System.Object.Equals%2A> método.  <xref:System.Object.Equals%2A>Indica se as duas variáveis aponte para a mesma instância.  
  
## Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos de valor e referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Objetos e classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)