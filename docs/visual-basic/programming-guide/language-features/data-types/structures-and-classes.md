---
title: Estruturas e classes (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: e64b54b93463845dd9afd0c0efd0e39f20cab1ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="structures-and-classes-visual-basic"></a>Estruturas e classes (Visual Basic)
Visual Basic unifica a sintaxe para estruturas e classes, com o resultado que ambas as entidades suportam a maioria dos mesmos recursos. No entanto, também há diferenças importantes entre as estruturas e classes.  
  
 As classes têm a vantagem de ser tipos de referência — passar uma referência é mais eficiente do que passar uma variável de estrutura com todos os seus dados. Por outro lado, as estruturas não requerem alocação de memória na pilha global.  
  
 Como você não pode herdar de uma estrutura, estruturas devem ser usadas apenas para objetos que não precisam ser estendido. Use estruturas quando o objeto que você deseja criar tem um tamanho de instância pequena e levar em conta as características de desempenho de classes versus estruturas.  
  
## <a name="similarities"></a>Semelhanças  
 Estruturas e classes são semelhantes nos seguintes aspectos:  
  
-   Ambos são *contêiner* tipos, o que significa que elas contêm outros tipos como membros.  
  
-   Ambos têm membros, que podem incluir construtores, métodos, propriedades, campos, constantes, enumerações, eventos e manipuladores de eventos. No entanto, não confunda esses membros com o declarado *elementos* de uma estrutura.  
  
-   Membros de ambas podem ter níveis de acesso individualizados. Por exemplo, um membro pode ser declarado `Public` e outro `Private`.  
  
-   Ambas podem implementar interfaces.  
  
-   Ambos podem ter construtores compartilhados, com ou sem parâmetros.  
  
-   Ambos podem expor uma *propriedade padrão*, desde que a propriedade tem pelo menos um parâmetro.  
  
-   Ambas podem declarar e disparar eventos, e ambas podem declarar representantes.  
  
## <a name="differences"></a>Diferenças  
 Estruturas e classes diferem nas particularidades a seguir:  
  
-   Estruturas são *os tipos de valor*; classes são *tipos de referência*. Uma variável de um tipo de estrutura contém dados a estrutura dos, em vez de que contém uma referência para os dados como um tipo de classe faz.  
  
-   Estruturas usam alocação da pilha; classes usam alocação de heap.  
  
-   Todos os elementos de estrutura são `Public` por padrão; classe variáveis e constantes são `Private` por padrão, enquanto outros membros de classe são `Public` por padrão. Esse comportamento para membros de classe fornece compatibilidade com o sistema do Visual Basic 6.0 de padrões.  
  
-   Uma estrutura deve ter pelo menos uma não compartilhado variável ou não compartilhado e não personalizado elemento do evento. uma classe pode ser totalmente vazia.  
  
-   Elementos de estrutura não podem ser declarados como `Protected`; membros de classe podem.  
  
-   Um procedimento de estrutura pode manipular eventos somente se ele for um [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento e somente por meio do [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md); qualquer procedimento de classe pode manipular eventos, usando qualquer o [ Manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) palavra-chave ou o `AddHandler` instrução. Para obter mais informações, consulte [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Declarações de variável de estrutura não é possível especificar inicializadores ou tamanhos iniciais para matrizes; declarações de variável de classe podem.  
  
-   Estruturas implicitamente herdam o <xref:System.ValueType?displayProperty=nameWithType> de classe e não pode herdar de outro tipo; classes podem herdar de qualquer classe ou classes diferentes de <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Estruturas não são herdáveis; classes são.  
  
-   Estruturas são nunca finalizadas, portanto, o common language runtime (CLR) nunca chama o <xref:System.Object.Finalize%2A> método em qualquer estrutura; as classes são finalizadas pelo coletor de lixo (GC), que chama <xref:System.Object.Finalize%2A> em uma classe quando ele detecta que não há nenhuma referência ativa restantes.  
  
-   Uma estrutura não requer um construtor; faz uma classe.  
  
-   As estruturas podem ter construtores compartilhados somente se elas tiverem parâmetros; classes podem tê-los com ou sem parâmetros.  
  
 Cada estrutura tem um construtor público implícito sem parâmetros. Este construtor inicializa os elementos de dados do toda a estrutura para seus valores padrão. Você não pode redefinir esse comportamento.  
  
## <a name="instances-and-variables"></a>Instâncias e variáveis  
 Como estruturas são tipos de valor, cada variável de estrutura é permanentemente associada a uma instância de estrutura individual. Mas classes são tipos de referência e uma variável de objeto pode fazer referência a várias instâncias de classe em momentos diferentes. Essa distinção afeta o uso de classes e estruturas das seguintes maneiras:  
  
-   **inicialização.** Uma variável de estrutura implicitamente inclui uma inicialização dos elementos usando o construtor sem parâmetros da estrutura. Portanto, `Dim s As struct1` é equivalente a `Dim s As struct1 = New struct1()`.  
  
-   **Atribuir variáveis.** Quando você atribui uma variável de estrutura para outro ou passa uma instância de estrutura para um argumento de procedimento, os valores atuais de todos os elementos de variável são copiados para a nova estrutura. Quando você atribui uma variável de objeto para outro ou passa uma variável de objeto para um procedimento, o ponteiro de referência é copiado.  
  
-   **Atribuindo Nothing.** Você pode atribuir o valor [nada](../../../../visual-basic/language-reference/nothing.md) a uma estrutura de variável, mas a instância continuará a ser associado à variável. Você ainda pode chamar seus métodos e acessar seus elementos de dados, embora os elementos de variáveis são reinicializados pela atribuição.  
  
     Por outro lado, se você definir uma variável de objeto `Nothing`, você o dissocia de qualquer instância de classe e não pode acessar todos os membros através da variável até que você atribua uma outra instância a ela.  
  
-   **Várias instâncias.** Uma variável de objeto pode ter instâncias de classe diferente atribuídas a ela em momentos diferentes e diversas variáveis de objeto podem referir-se à mesma instância de classe ao mesmo tempo. As alterações feitas aos valores de membros de classe afetarão esses membros quando acessados por outra variável apontando para a mesma instância.  
  
     Elementos de estrutura, no entanto, são isolados em sua própria instância. Alterações em seus valores não serão refletidas em qualquer outra variável de estrutura, mesmo em outras instâncias do mesmo `Structure` declaração.  
  
-   **Igualdade.** Teste de igualdade de duas estruturas deve ser executada com um elemento pelo teste. Duas variáveis de objeto podem ser comparados usando o <xref:System.Object.Equals%2A> método. <xref:System.Object.Equals%2A> Indica se as duas variáveis apontam para a mesma instância.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Estruturas e Outros Elementos de Programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
