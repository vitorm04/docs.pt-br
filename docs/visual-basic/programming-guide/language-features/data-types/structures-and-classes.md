---
title: Estruturas e Classes (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e7402ec0fcfc279470d39a4919d3b5ec8b5d9dff
ms.lasthandoff: 03/13/2017

---
# <a name="structures-and-classes-visual-basic"></a>Estruturas e classes (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]unifica a sintaxe para estruturas e classes, com o resultado que ambas as entidades suportam a maioria dos mesmos recursos. No entanto, também existem diferenças importantes entre as estruturas e classes.  
  
 Classes têm a vantagem de ser tipos de referência — passar uma referência é mais eficiente do que passar uma variável de estrutura com todos os seus dados. Por outro lado, as estruturas não requerem alocação de memória na pilha global.  
  
 Como você não pode herdar de uma estrutura, estruturas devem ser usadas apenas para objetos que não precisam ser estendido. Use estruturas quando o objeto que você deseja criar tem uma instância de tamanho pequeno e levar em conta as características de desempenho de classes versus estruturas.  
  
## <a name="similarities"></a>Semelhanças  
 Estruturas e classes são semelhantes nos seguintes aspectos:  
  
-   Ambos são *contêiner* tipos, o que significa que elas contêm outros tipos como membros.  
  
-   Ambas ter membros, que podem incluir construtores, métodos, propriedades, campos, constantes, enumerações, eventos e manipuladores de eventos. No entanto, não confunda esses membros com o declarados *elementos* de uma estrutura.  
  
-   Membros de ambas podem ter níveis de acesso individualizados. Por exemplo, um membro pode ser declarado `Public` e outro `Private`.  
  
-   Ambas podem implementar interfaces.  
  
-   Ambos podem ter construtores compartilhados, com ou sem parâmetros.  
  
-   Ambos podem expor uma *propriedade padrão*, desde que a propriedade aceite pelo menos um parâmetro.  
  
-   Ambas podem declarar e disparar eventos, e ambas podem declarar representantes.  
  
## <a name="differences"></a>Diferenças  
 Estruturas e classes diferem nas particularidades a seguir:  
  
-   Estruturas são *tipos de valor*; são classes *tipos de referência*. Uma variável de um tipo de estrutura contém dados a estrutura dos, em vez que contendo uma referência para os dados como um tipo de classe.  
  
-   Estruturas usam alocação da pilha; classes usam alocação de heap.  
  
-   Todos os elementos de estrutura são `Public` por padrão; classe variáveis e constantes são `Private` por padrão, enquanto outros membros da classe são `Public` por padrão. Esse comportamento para membros de classe fornece compatibilidade com o sistema de padrões de Visual Basic 6.0.  
  
-   Uma estrutura deve ter pelo menos um não compartilhado variável ou não compartilhado e não personalizado elemento eventos; uma classe pode ser completamente vazia.  
  
-   Elementos de estrutura não podem ser declarados como `Protected`; membros de classe podem.  
  
-   Um procedimento de estrutura pode manipular eventos somente se ele for um [compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procedimento e somente por meio do [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md); qualquer procedimento de classe pode manipular eventos, usando o [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) palavra-chave ou o `AddHandler` instrução. Para obter mais informações, consulte [eventos](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
-   Declarações de variável de estrutura não é possível especificar inicializadores ou tamanhos iniciais para matrizes; declarações de variável de classe podem.  
  
-   Estruturas implicitamente herdam o <xref:System.ValueType?displayProperty=fullName>de classe e não podem herdar de nenhum outro tipo; classes podem herdar de qualquer classe ou classes diferentes <xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName> </xref:System.ValueType?displayProperty=fullName>  
  
-   Estruturas não são herdáveis; classes são.  
  
-   Estruturas são nunca finalizadas, portanto, o common language runtime (CLR) nunca chama o <xref:System.Object.Finalize%2A>método em qualquer estrutura; as classes são finalizadas pelo coletor de lixo (GC), que chama <xref:System.Object.Finalize%2A>em uma classe quando ele detecta que há referências ativas restantes.</xref:System.Object.Finalize%2A> </xref:System.Object.Finalize%2A>  
  
-   Uma estrutura não requer um construtor; faz uma classe.  
  
-   Estruturas podem ter construtores compartilhados somente se elas tiverem parâmetros; classes podem tê-los com ou sem parâmetros.  
  
 Cada estrutura tem um construtor público implícito sem parâmetros. Este construtor inicializa os elementos de dados do toda a estrutura para seus valores padrão. Você não pode redefinir esse comportamento.  
  
## <a name="instances-and-variables"></a>Instâncias e variáveis  
 Como estruturas são tipos de valor, cada variável de estrutura é permanentemente associada a uma instância de estrutura individual. Mas classes são tipos de referência e uma variável de objeto pode fazer referência a várias instâncias de classe em momentos diferentes. Essa distinção afeta o uso de classes e estruturas das seguintes maneiras:  
  
-   **Inicialização.** Uma variável de estrutura implicitamente inclui uma inicialização dos elementos usando o construtor sem parâmetros da estrutura. Portanto, `Dim s As struct1` é equivalente a `Dim s As struct1 = New struct1()`.  
  
-   **Atribuindo variáveis.** Quando você atribuir uma variável de estrutura para outro ou passa uma instância de estrutura para um argumento de procedimento, os valores atuais de todos os elementos de variáveis são copiados para a nova estrutura. Quando você atribuir uma variável de objeto para outro ou passa uma variável de objeto para um procedimento, o ponteiro de referência é copiado.  
  
-   **Atribuindo Nothing.** Você pode atribuir o valor [nada](../../../../visual-basic/language-reference/nothing.md) a estrutura de uma variável, mas a instância continua a ser associado à variável. Você ainda pode chamar seus métodos e acessar seus elementos de dados, embora os elementos de variável sejam reinicializados pela atribuição.  
  
     Por outro lado, se você definir uma variável de objeto para `Nothing`, você o dissocia de qualquer instância de classe e não pode acessar todos os membros através da variável até que você atribua uma outra instância a ela.  
  
-   **Várias instâncias.** Uma variável de objeto pode ter instâncias de classe diferente atribuídas a ela em momentos diferentes, e várias variáveis de objeto podem referir-se à mesma instância de classe ao mesmo tempo. As alterações feitas aos valores de membros de classe afetarão esses membros quando acessados por outra variável apontando para a mesma instância.  
  
     Elementos de estrutura, no entanto, são isolados em sua própria instância. Alterações em seus valores não são refletidas em qualquer outra variável de estrutura, mesmo em outras instâncias do mesmo `Structure` declaração.  
  
-   **Igualdade.** Teste de igualdade de duas estruturas deve ser executada com um teste de elemento por elemento. Duas variáveis de objeto podem ser comparadas usando o <xref:System.Object.Equals%2A>método.</xref:System.Object.Equals%2A> <xref:System.Object.Equals%2A>Indica se as duas variáveis apontam para a mesma instância.</xref:System.Object.Equals%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Tipos de dados compostos](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Tipos de valor e tipos de referência](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Estruturas](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Estruturas e outros elementos de programação](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Objetos e Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
