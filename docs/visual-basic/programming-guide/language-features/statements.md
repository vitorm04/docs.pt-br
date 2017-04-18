---
title: "Instruções no Visual Basic | Documentos do Microsoft"
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
- variables [Visual Basic], declaring
- colons (:)
- constants, defining
- underlines
- constants, statements
- blue underline
- procedures, statements
- variables [Visual Basic], assigning
- line breaks, in code
- executable statements
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
caps.latest.revision: 30
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
ms.openlocfilehash: 001ea1cb5e651b95f808eefd47fd468f556550a1
ms.lasthandoff: 03/13/2017

---
# <a name="statements-in-visual-basic"></a>Instruções no Visual Basic
Uma instrução em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] é uma instrução completa. Ele pode conter as palavras-chave, operadores, variáveis, constantes e expressões. Cada instrução pertence a uma das seguintes categorias:  
  
-   **Instruções de declaração**, que o nome de uma variável, uma constante ou um procedimento e também pode especificar um tipo de dados.  
  
-   **Instruções executáveis**, que iniciar ações. Essas instruções podem chamar um método ou função e podem executar um loop ou ramificação entre os blocos de código. Instruções executáveis incluem **instruções de atribuição**, que atribui um valor ou expressão a uma variável ou constante.  
  
 Este tópico descreve cada categoria. Além disso, este tópico descreve como combinar várias instruções em uma única linha e como continuar uma instrução em várias linhas.  
  
## <a name="declaration-statements"></a>Instruções de declaração  
 Você pode usar instruções de declaração para nomear e definir procedimentos, variáveis, propriedades, matrizes e constantes. Quando você declara um elemento de programação, você também pode definir o tipo de dados, nível de acesso e escopo. Para obter mais informações, consulte [características do elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).  
  
 O exemplo a seguir contém três declarações.  
  
 [!code-vb[VbVbalrStatements&#80;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_1.vb)]  
  
 A primeira declaração é a `Sub` instrução. Junto com seus correspondentes `End Sub` instrução, ele declara um procedimento denominado `applyFormat`. Ela também especifica que `applyFormat` é `Public`, que significa que qualquer código que pode fazer referência a ele pode chamá-lo.  
  
 A segunda declaração é a `Const` instrução, que declara a constante `limit`, especificando o `Integer` tipo de dados e um valor de 33.  
  
 A terceira declaração é a `Dim` instrução, que declara a variável `thisWidget`. O tipo de dados é um objeto específico, ou seja, um objeto criado a partir de `Widget` classe. Você pode declarar uma variável de qualquer tipo de dados elementar ou de qualquer tipo de objeto que é exposto no aplicativo que você está usando.  
  
### <a name="initial-values"></a>Valores iniciais  
 Quando o código que contém uma instrução de declaração é executado, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] reserva de memória exigida para o elemento declarado. Se o elemento contém um valor [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] inicializa com o valor padrão para seu tipo de dados. Para obter mais informações, consulte "Comportamento" em [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
 Você pode atribuir um valor inicial para uma variável como parte de sua declaração, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements&#81;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_2.vb)]  
  
 Se uma variável é uma variável de objeto, você pode criar explicitamente uma instância de sua classe quando você declará-la usando o [novo operador](../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave, como o exemplo a seguir ilustra.  
  
 [!code-vb[VbVbalrStatements&#82;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_3.vb)]  
  
 Observe que o valor inicial especificado em uma instrução de declaração não é atribuído a uma variável até que a execução atinge sua instrução de declaração. Até lá, a variável contém o valor padrão para seu tipo de dados.  
  
## <a name="executable-statements"></a>Instruções executáveis  
 Uma instrução executável executa uma ação. Ele pode chamar um procedimento, a ramificação para outro lugar no código, o loop por meio de várias instruções, ou avaliar uma expressão. Uma instrução de atribuição é um caso especial de uma instrução executável.  
  
 O exemplo a seguir usa um `If...Then...Else` estrutura para executar diferentes blocos de código com base no valor de uma variável de controle. Em cada bloco de código, um `For...Next` loop é executado um número especificado de vezes.  
  
 [!code-vb[VbVbalrStatements&#83;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_4.vb)]  
  
 O `If` instrução no exemplo anterior verifica o valor do parâmetro `clockwise`. Se o valor for `True`, ele chama o `spinClockwise` método `aWidget`. Se o valor for `False`, ele chama o `spinCounterClockwise` método `aWidget`. O `If...Then...Else` estrutura de controle termina com `End If`.  
  
 O `For...Next` loop em cada bloco chama o método apropriado um número de vezes igual ao valor da `revolutions` parâmetro.  
  
## <a name="assignment-statements"></a>Instruções de atribuição  
 Instruções de atribuição realizarem operações de atribuição, que consistem em fazer o valor à direita do operador de atribuição (`=`) e armazená-lo no elemento à esquerda, como no exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements&#73;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_5.vb)]  
  
 No exemplo anterior, a instrução de atribuição armazena o valor literal 42 na variável `v`.  
  
### <a name="eligible-programming-elements"></a>Elementos de programação qualificados  
 O elemento de programação no lado esquerdo do operador de atribuição deve ser capaz de aceitar e armazenar um valor. Isso significa que ele deve ser uma variável ou propriedade que não seja [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md), ou deve ser um elemento de matriz. No contexto de uma instrução de atribuição, esse elemento é chamado, às vezes, uma *lvalue*, "valor esquerdo".  
  
 O valor à direita do operador de atribuição é gerado por uma expressão, que pode consistir em qualquer combinação de literais, constantes, variáveis, propriedades, elementos de matriz, outras expressões ou chamadas de função. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrStatements&#74;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_6.vb)]  
  
 O exemplo acima adiciona o valor mantido na variável `y` para o valor mantido na variável `z`e, em seguida, adiciona o valor retornado pela chamada à função `findResult`. O valor total dessa expressão é armazenado na variável `x`.  
  
### <a name="data-types-in-assignment-statements"></a>Tipos de dados em instruções de atribuição  
 Além dos valores numéricos, o operador de atribuição também pode atribuir `String` valores, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements&#75;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_7.vb)]  
  
 Você também pode atribuir `Boolean` valores, usando um `Boolean` literal ou um `Boolean` expressão, como o exemplo a seguir ilustra.  
  
 [!code-vb[VbVbalrStatements&#76;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_8.vb)]  
  
 Da mesma forma, você pode atribuir os valores apropriados para elementos de programação do `Char`, `Date`, ou `Object` tipo de dados. Você também pode atribuir uma instância do objeto para um elemento declarado como a classe da qual essa instância é criada.  
  
### <a name="compound-assignment-statements"></a>Instruções de atribuição compostas  
 *Instruções de atribuição compostas* primeiro executar uma operação em uma expressão antes de atribuí-la a um elemento de programação. O exemplo a seguir ilustra um destes operadores `+=`, que incrementa o valor da variável no lado esquerdo do operador pelo valor da expressão no lado direito.  
  
 [!code-vb[VbVbalrStatements&#77;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_9.vb)]  
  
 O exemplo anterior adiciona 1 ao valor de `n`e, em seguida, armazena esse novo valor em `n`. É uma abreviação equivalente da instrução a seguir:  
  
 [!code-vb[VbVbalrStatements&#78;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_10.vb)]  
  
 Uma variedade de operações de atribuição composta pode ser realizada usando operadores desse tipo. Para obter uma lista de mais informações sobre eles e esses operadores, consulte [operadores de atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md).  
  
 O operador de atribuição de concatenação (`&=`) é útil para adicionar uma cadeia de caracteres ao final da já existentes cadeias de caracteres, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements&#79;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_11.vb)]  
  
### <a name="type-conversions-in-assignment-statements"></a>Conversões de tipo em instruções de atribuição  
 O valor que você atribui a uma variável, propriedade ou elemento de matriz deve ser um tipo de dados apropriado para o elemento de destino. Em geral, você deve tentar gerar um valor do mesmo tipo de dados que o elemento de destino. No entanto, alguns tipos podem ser convertidos em outros tipos durante a atribuição.  
  
 Para obter informações sobre como converter entre tipos de dados, consulte [conversões de tipo no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md). Em resumo, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente converte um valor de um determinado tipo em qualquer outro tipo ao qual ele se expande. A *conversões ampliadoras* é um em que sempre terá êxito em tempo de execução e não perderá os dados. Por exemplo, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] converte uma `Integer` valor `Double` quando apropriado, pois `Integer` amplia a `Double`. Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 *Conversões de estreitamento* (aquelas que não são de ampliação) carregam um risco de falha em tempo de execução ou de perda de dados. Você pode executar uma conversão de restrição explicitamente usando uma função de conversão de tipo, ou você pode instruir o compilador para executar todas as conversões implicitamente pela configuração `Option Strict Off`. Para obter mais informações, consulte [conversões explícitas e implícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="putting-multiple-statements-on-one-line"></a>Colocar várias instruções em uma linha  
 Você pode ter várias instruções em uma única linha, separada por dois-pontos (`:`) caracteres. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrStatements&#70;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_12.vb)]  
  
 Embora ocasionalmente conveniente, essa forma de sintaxe torna seu código difícil de ler e manter. Portanto, é recomendável que você mantenha uma instrução em uma linha.  
  
## <a name="continuing-a-statement-over-multiple-lines"></a>Continuar uma instrução em várias linhas  
 Uma instrução normalmente se encaixa em uma linha, mas quando ele for muito grande, você pode continuá-lo para a próxima linha usando uma sequência de continuação de linha, que consiste em um espaço seguido por um caractere de sublinhado (`_`) seguido por um retorno de carro. No exemplo a seguir, o `MsgBox` instrução executável é continuada em duas linhas.  
  
 [!code-vb[VbVbalrStatements&#71;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_13.vb)]  
  
### <a name="implicit-line-continuation"></a>Continuação implícita de linha  
 Em muitos casos, você pode continuar uma instrução na próxima linha consecutiva sem usar o caractere de sublinhado (_). A tabela a seguir lista os elementos de sintaxe que a instrução continuam implicitamente na próxima linha de código.  
  
|Elemento de sintaxe|Exemplo|  
|---|---|  
|Depois de uma vírgula (`,`).|[!code-vb[VbVbalrLineContinuation n º&1;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_14.vb)]|  
|Depois de um parêntese de abertura (`(`) ou antes de um parêntese de fechamento (`)`).|[!code-vb[VbVbalrLineContinuation n º&2;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_15.vb)]|  
|Depois de uma chave aberta (`{`) ou antes de uma chave de fechamento (`}`).|[!code-vb[VbVbalrLineContinuation n º&3;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_16.vb)]<br /><br /> Para obter mais informações, consulte [inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) ou [inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
|Após um aberto expressão incorporada (`<%=`) ou antes do fechamento de uma expressão incorporada (`%>`) dentro de um literal XML.|[!code-vb[VbVbalrLineContinuation n º&4;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_17.vb)]<br /><br /> Para obter mais informações, consulte [expressões inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
|Após o operador de concatenação (`&`).|[!code-vb[VbVbcnConventions n º&9;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_18.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|After assignment operators (`=`, `&=`, `:=`, `+=`, `-=`, `*=`, `/=`, `\=`, `^=`, `<<=`, `>>=`).|[!code-vb[VbVbalrLineContinuation n º&5;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|After binary operators (`+`, `-`, `/`, `*`, `Mod`, `<>`, `<`, `>`, `<=`, `>=`, `^`, `>>`, `<<`, `And`, `AndAlso`, `Or`, `OrElse`, `Like`, `Xor`) within an expression.|[!code-vb[VbVbalrLineContinuation&#7;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_20.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Após o `Is` e `IsNot` operadores.|[!code-vb[VbVbalrLineContinuation n º&8;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_21.vb)]<br /><br /> Para obter mais informações, consulte [operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md).|  
|Depois de um caractere de qualificador de membro (`.`) e antes do nome do membro. No entanto, você deve incluir um caractere de continuação de linha (_), um caractere de qualificador de membro a seguir quando você estiver usando o `With` instrução ou fornecer valores na lista de inicialização para um tipo. Divida a linha após o operador de atribuição (por exemplo, `=`) quando você estiver usando `With` instruções ou listas de inicialização de objeto.|[!code-vb[VbVbalrLineContinuation n º&5;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_19.vb)]<br />[!code-vb[VbVbalrLineContinuation&#14;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_22.vb)]<br /><br /> Para obter mais informações, consulte [com... Terminar com instrução](../../../visual-basic/language-reference/statements/with-end-with-statement.md) ou [inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md).|  
|Depois de um qualificador de propriedade de eixo XML (`.` ou `.@` ou `...`). No entanto, você deve incluir um caractere de continuação de linha (_) ao especificar um qualificador de membro quando você estiver usando o `With` palavra-chave.|[!code-vb[VbVbalrLineContinuation n º&9;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_23.vb)]<br /><br /> Para obter mais informações, consulte [propriedades do eixo XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).|  
|Após um menor-que (<) or="" before="" a="" greater-than="" sign=""></)>`>`) quando você especificar um atributo. Além disso, após um maior-que (`>`) quando você especificar um atributo. No entanto, você deve incluir um caractere de continuação de linha (_) ao especificar atributos de nível de assembly ou módulo.|[!code-vb[VbVbalrLineContinuation n º&10;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_24.vb)]<br /><br /> Para obter mais informações, consulte [visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md).|  
|Before and after query operators (`Aggregate`, `Distinct`, `From`, `Group By`, `Group Join`, `Join`, `Let`, `Order By`, `Select`, `Skip`, `Skip While`, `Take`, `Take While`, `Where`, `In`, `Into`, `On`, `Ascending`, and `Descending`). Não é possível dividir uma linha entre as palavras-chave dos operadores de consulta que são compostos de várias palavras-chave (`Order By`, `Group Join`, `Take While`, e `Skip While`).|[!code-vb[VbVbalrLineContinuation n º&11;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_25.vb)]<br /><br /> Para obter mais informações, consulte [consultas](../../../visual-basic/language-reference/queries/queries.md).|  
|Após o `In` palavra-chave em um `For Each` instrução.|[!code-vb[VbVbalrLineContinuation&#12;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_26.vb)]<br /><br /> Para obter mais informações, consulte [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).|  
|Após o `From` palavra-chave em um inicializador de coleção.|[!code-vb[VbVbalrLineContinuation&13;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/statements_27.vb)]<br /><br /> Para obter mais informações, consulte [inicializadores de coleção](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).|  
  
## <a name="adding-comments"></a>Adicionando comentários  
 Código-fonte nem sempre é auto-explicativo, até mesmo para o programador que escreveu. Para ajudar a documentar seu código, portanto, a maioria dos programadores fazer uso liberal dos comentários inseridos. Comentários no código podem explicar um procedimento ou uma instrução específica para qualquer pessoa ler ou trabalhar com ela mais tarde. [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ignora os comentários durante a compilação, e elas não afetam o código compilado.  
  
 Linhas de comentários começam com um apóstrofo (`'`) ou `REM` seguido por um espaço. Eles podem ser adicionados em qualquer lugar no código, exceto em uma cadeia de caracteres. Para acrescentar um comentário em uma instrução, insira um apóstrofo ou `REM` depois da instrução, seguida do comentário. Comentários também podem entrar em sua própria linha separada. O exemplo a seguir demonstra essas possibilidades.  
  
 [!code-vb[VbVbalrStatements&#72;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/statements_28.vb)]  
  
## <a name="checking-compilation-errors"></a>Verificação de erros de compilação  
 Se, depois que você digitar uma linha de código, a linha é exibida com um sublinhado ondulado azul (uma mensagem de erro pode aparecer também), há um erro de sintaxe na instrução. Você deve descobrir o que há de errado com a instrução (por procurando na lista de tarefas, ou passar o mouse sobre o erro com o ponteiro do mouse e ler a mensagem de erro) e corrigi-lo. Até que você resolveu todos os erros de sintaxe no seu código, seu programa não será compilado corretamente.  
  
## <a name="related-sections"></a>Seções relacionadas  
  
|Termo|Definição|  
|---|---|  
|[Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)|Fornece links para páginas de referência de linguagem que abrangem os operadores de atribuição como `=`, `*=`, e `&=`.|  
|[Operadores e Expressões](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)|Mostra como combinar elementos com operadores para gerar novos valores.|  
|[Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|Mostra como dividir uma única instrução em várias linhas e como colocar várias instruções na mesma linha.|  
|[Como rotular instruções](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|Mostra como rotular uma linha de código.|
