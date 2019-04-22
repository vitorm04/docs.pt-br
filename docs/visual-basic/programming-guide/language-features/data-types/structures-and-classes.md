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
ms.openlocfilehash: 3635729705520518d4c950f8a79da7d1249285bf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841609"
---
# <a name="structures-and-classes-visual-basic"></a>Estruturas e classes (Visual Basic)
Visual Basic unifica a sintaxe para estruturas e classes, com o resultado que ambas as entidades dão suporte à maioria dos mesmos recursos. No entanto, também há diferenças importantes entre as estruturas e classes.  
  
 As classes têm a vantagem de ser tipos de referência — passar uma referência é mais eficiente do que passar uma variável de estrutura com todos os seus dados. Por outro lado, estruturas não precisam de alocação de memória no heap global.  
  
 Como você não pode herdar de uma estrutura, estruturas devem ser usadas apenas para objetos que não precisam ser estendido. Use estruturas quando o objeto que você deseja criar tem um tamanho de instância pequena e levar em conta as características de desempenho de classes versus estruturas.  
  
## <a name="similarities"></a>Semelhanças  
 Estruturas e classes são semelhantes nos seguintes aspectos:  
  
-   Ambos são *contêiner* tipos, o que significa que eles contêm outros tipos como membros.  
  
-   Ambos têm membros, que podem incluir construtores, métodos, propriedades, campos, constantes, enumerações, eventos e manipuladores de eventos. No entanto, não confunda esses membros com o declarado *elementos* de uma estrutura.  
  
-   Os membros das funções podem ter níveis de acesso individualizados. Por exemplo, um membro pode ser declarado `Public` e outro `Private`.  
  
-   Ambos podem implementar interfaces.  
  
-   Ambos podem ter construtores, compartilhados, com ou sem parâmetros.  
  
-   Ambos podem expor uma *propriedade padrão*, desde que a propriedade tem pelo menos um parâmetro.  
  
-   Ambas podem declarar e acionar eventos, e ambas podem declarar delegados.  
  
## <a name="differences"></a>Diferenças  
 Estruturas e classes diferem nas particularidades a seguir:  
  
-   Estruturas são *tipos de valor*; as classes são *tipos de referência*. Uma variável de um tipo de estrutura contém dados a estrutura dos, em vez de contendo uma referência para os dados como um tipo de classe faz.  
  
-   Estruturas usam alocação da pilha; classes usam alocação de heap.  
  
-   Todos os elementos de estrutura são `Public` por padrão; variáveis de classe e as constantes são `Private` por padrão, enquanto outros membros de classe são `Public` por padrão. Esse comportamento para membros de classe fornece compatibilidade com o sistema do Visual Basic 6.0 de padrões.  
  
-   Uma estrutura deve ter pelo menos uma não compartilhado não compartilhado, ou variável não personalizado elemento event; uma classe pode ser completamente vazia.  
  
-   Elementos de estrutura não podem ser declarados como `Protected`; os membros de classe podem.  
  
-   Um procedimento de estrutura pode manipular eventos somente se ele for um [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento e somente por meio das [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md); qualquer procedimento de classe pode manipular eventos, usando qualquer um dos [ Manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) palavra-chave ou o `AddHandler` instrução. Para obter mais informações, consulte [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Declarações de variável de estrutura não é possível especificar inicializadores ou tamanhos iniciais para matrizes; declarações de variável de classe podem.  
  
-   Estruturas herdam implicitamente do <xref:System.ValueType?displayProperty=nameWithType> de classe e não pode herdar de qualquer outro tipo; as classes podem herdar de qualquer classe ou classes diferentes de <xref:System.ValueType?displayProperty=nameWithType>.  
  
-   Estruturas não são herdáveis; as classes são.  
  
-   Estruturas nunca são finalizadas, portanto, o common language runtime (CLR) nunca chama o <xref:System.Object.Finalize%2A> método em qualquer estrutura; as classes são finalizadas pelo coletor de lixo (GC), que chama <xref:System.Object.Finalize%2A> em uma classe quando ele detecta que nenhuma referência de ativo restantes.  
  
-   Uma estrutura não exige um construtor; uma classe faz.  
  
-   Estruturas podem ter construtores compartilhados somente se elas tiverem parâmetros; as classes podem tê-los com ou sem parâmetros.  
  
 Cada estrutura tem um construtor público implícito sem parâmetros. Este construtor inicializa os elementos de dados de todos os da estrutura para seus valores padrão. Você não pode redefinir esse comportamento.  
  
## <a name="instances-and-variables"></a>Instâncias e variáveis  
 Como estruturas são tipos de valor, cada variável de estrutura é permanentemente associada a uma instância de estrutura individual. Mas classes são tipos de referência e uma variável de objeto pode fazer referência a várias instâncias de classe em momentos diferentes. Essa distinção afeta o uso de estruturas e classes das seguintes maneiras:  
  
-   **Inicialização.** Uma variável de estrutura implicitamente inclui uma inicialização dos elementos usando o construtor sem parâmetros da estrutura. Portanto, `Dim s As struct1` é equivalente a `Dim s As struct1 = New struct1()`.  
  
-   **Atribuindo variáveis.** Quando você atribuir uma variável de estrutura para outra ou passa uma instância de estrutura para um argumento de procedimento, os valores atuais de todos os elementos de variável são copiados para a nova estrutura. Quando você atribuir uma variável de objeto para outro ou passa uma variável de objeto para um procedimento, somente o ponteiro de referência é copiado.  
  
-   **Atribuindo nada.** Você pode atribuir o valor [nada](../../../../visual-basic/language-reference/nothing.md) a estrutura de uma variável, mas a instância continua a ser associada à variável. Você ainda pode chamar seus métodos e acessar seus elementos de dados, embora os elementos de variáveis são reinicializados pela atribuição.  
  
     Por outro lado, se você definir uma variável de objeto como `Nothing`, dissociá-lo de qualquer instância de classe e não pode acessar todos os membros por meio da variável até que você atribua uma outra instância para ele.  
  
-   **Várias instâncias.** Uma variável de objeto pode ter instâncias de classe diferente atribuídas a ele em momentos diferentes, e diversas variáveis de objeto podem se referir à mesma instância de classe ao mesmo tempo. As alterações feitas aos valores de membros de classe afetam desses membros quando acessados por meio de outra variável que aponta para a mesma instância.  
  
     Elementos de estrutura, no entanto, são isolados em sua própria instância. Alterações em seus valores não são refletidas em qualquer outra variável de estrutura, mesmo em outras instâncias do mesmo `Structure` declaração.  
  
-   **Igualdade.** Teste de igualdade de duas estruturas deve ser executada com um teste de elemento por elemento. Duas variáveis de objeto podem ser comparadas usando o <xref:System.Object.Equals%2A> método. <xref:System.Object.Equals%2A> Indica se as duas variáveis que apontam para a mesma instância.  
  
## <a name="see-also"></a>Consulte também

- [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Tipos de Dados Compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Tipos de Valor e Tipos de Referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Estruturas e Outros Elementos de Programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
