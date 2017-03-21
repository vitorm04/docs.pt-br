---
title: "Convenções de codificação do Visual Basic | Documentos do Microsoft"
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
- coding conventions, Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 5712f14d53b86552a0b82af38ecf579577ef3fa1
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-coding-conventions"></a>Convenções de codificação do Visual Basic
A Microsoft desenvolve amostras e documentação que siga as diretrizes neste tópico. Se você seguir as mesmas convenções de codificação, você pode obter os seguintes benefícios:  
  
-   Seu código terá uma aparência consistente, para que os leitores melhor podem se concentrar no conteúdo, não o layout.  
  
-   Leitores de compreendam o código mais rapidamente porque elas podem fazer suposições com base nas experiências anteriores.  
  
-   Você pode copiar, alterar e manter o código mais facilmente.  
  
-   Você ajuda a garantir que seu código demonstra "práticas recomendadas" para o Visual Basic.  
  
## <a name="naming-conventions"></a>Convenções de nomenclatura  
  
-   Para obter informações sobre as diretrizes de nomenclatura, consulte [diretrizes de nomenclatura](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3) tópico.  
  
-   Não use "Meu" ou "Meu" como parte de um nome de variável. Essa prática cria confusão com o `My` objetos.  
  
-   Você não precisa alterar os nomes de objetos no código gerado automaticamente para ajustar as diretrizes.  
  
## <a name="layout-conventions"></a>Convenções de Layout  
  
-   Inserir tabulações como espaços e use o recuo inteligente com recuos de quatro espaço.  
  
-   Use **bastante listando (reformatação) do código** reformatar o código no editor de códigos. Para obter mais informações, consulte [opções, Editor de texto, básico (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Use apenas uma instrução por linha. Não use o caractere de separador de linha (:) do Visual Basic.  
  
-   Evite usar o caractere de continuação de linha explícita "_" em favor de continuação implícita de linha sempre que o idioma permite a ele.  
  
-   Use apenas uma declaração por linha.  
  
-   Se **bastante listando (reformatação) do código** não formatar linhas de continuação automaticamente, manualmente Recuar continuação linhas uma parada de tabulação. No entanto, sempre alinhado à esquerda itens em uma lista.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Adicione pelo menos uma linha em branco entre as definições de método e propriedade.  
  
## <a name="commenting-conventions"></a>Comentando Convenções  
  
-   Inserir comentários em uma linha separada em vez de no final de uma linha de código.  
  
-   Inicie o texto do comentário com uma letra maiuscula e texto de comentário final com um ponto.  
  
-   Insira um espaço entre o delimitador de comentário (') e o texto do comentário.  
  
     [!code-vb[VbVbalrGuidelines n º&2;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Não coloque comentários com blocos de asteriscos formatados.  
  
## <a name="program-structure"></a>Estrutura do programa  
  
-   Quando você usa o `Main` método, use o construtor padrão para novos aplicativos de console e usar `My` para argumentos de linha de comando.  
  
     [!code-vb[VbVbalrGuidelines n º&3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Diretrizes de Linguagem  
  
### <a name="string-data-type"></a>Tipo de dados da cadeia de caracteres  
  
-   Para concatenar cadeias de caracteres, use um e comercial (&).  
  
     [!code-vb[VbVbalrGuidelines n º&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Para acrescentar cadeias de caracteres em loops, use o <xref:System.Text.StringBuilder>objeto.</xref:System.Text.StringBuilder>  
  
     [!code-vb[VbVbalrGuidelines n º&5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Delegados relaxados nos manipuladores de eventos  
 Não qualifique explicitamente os argumentos (Object e EventArgs) para manipuladores de eventos. Se você não estiver usando os argumentos do evento são passados para um evento (por exemplo, o remetente como objeto, e como EventArgs), usar delegados relaxados e omitir os argumentos do evento no seu código:  
  
 [!code-vb[VbVbalrGuidelines&#7;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>Tipo de Dados Sem Sinal  
  
-   Use `Integer` em vez de tipos não assinados, exceto onde eles são necessários.  
  
### <a name="arrays"></a>Matrizes  
  
-   Use a sintaxe abreviada ao inicializar matrizes na linha da declaração. Por exemplo, use a sintaxe a seguir.  
  
     [!code-vb[VbVbalrGuidelines n º&8;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Não use a sintaxe a seguir.  
  
     [!code-vb[VbVbalrGuidelines n º&9;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Coloque o designador de matriz do tipo, e não na variável. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines n º&11;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Não use a sintaxe a seguir:  
  
     [!code-vb[VbVbalrGuidelines n º&10;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Use a sintaxe {} quando você declara e inicializar matrizes de tipos de dados básicos. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines&#12;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Não use a sintaxe a seguir:  
  
     [!code-vb[VbVbalrGuidelines&13;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Use a palavra-chave With  
 Quando você faz uma série de chamadas a um objeto, considere o uso de `With` palavra-chave:  
  
 [!code-vb[VbVbalrGuidelines&#15;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Use a instrução Try... Catch e instruções Using ao usar tratamento de exceções  
 Não use `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Use a palavra-chave IsNot  
 Use o `IsNot` palavra-chave em vez de `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>Palavra-chave New  
  
-   Use instanciação curta. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines&#21;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     A linha anterior é equivalente a esta:  
  
     [!code-vb[VbVbalrGuidelines&#22;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Use inicializadores de objeto para novos objetos em vez do construtor sem parâmetros:  
  
     [!code-vb[VbVbalrGuidelines&#23;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Tratamento de Evento  
  
-   Use `Handles` em vez de `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines&#24;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Use `AddressOf`e não instanciar o delegado explicitamente:  
  
     [!code-vb[25 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Quando você define um evento, use a sintaxe abreviada e permitem que o compilador defina o delegado:  
  
     [!code-vb[VbVbalrGuidelines&#26;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Não verificar se um evento é `Nothing` (null) antes de chamar o `RaiseEvent` método. `RaiseEvent`verifica se há `Nothing` antes de gerar o evento.  
  
### <a name="using-shared-members"></a>Usando membros compartilhados  
 Chamar `Shared` membros usando o nome de classe, não a partir de uma variável de instância.  
  
### <a name="use-xml-literals"></a>Usar literais XML  
 Literais XML simplificam as tarefas mais comuns encontrados ao trabalhar com XML (por exemplo, carga, consulta e transformação). Ao desenvolver com XML, siga estas diretrizes:  
  
-   Use literais XML para criar documentos XML e fragmentos em vez de chamar APIs XML diretamente.  
  
-   Importe namespaces XML no nível do arquivo ou projeto para aproveitar as otimizações de desempenho para literais XML.  
  
-   Use as propriedades do eixo XML para acessar elementos e atributos em um documento XML.  
  
-   Usar expressões inseridas para incluir valores e criar o XML de valores existentes em vez de usar chamadas de API, como o `Add` método:  
  
     [!code-vb[VbVbalrGuidelines&#27;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>Consultas LINQ  
  
-   Use nomes significativos para variáveis de consulta:  
  
     [!code-vb[VbVbalrGuidelines&#28;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Fornecer nomes de elementos em uma consulta para certificar-se de que os nomes de propriedades de tipos anônimos são corretamente em maiusculas usando Pascal casing:  
  
     [!code-vb[29 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos. Por exemplo, se a consulta retorna um cliente, nome e uma ID de ordem, renomeá-los o em vez de deixá-los como `Name` e `ID` no resultado:  
  
     [!code-vb[30 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Use a inferência de tipo na declaração de variáveis de consulta e intervalo:  
  
     [!code-vb[VbVbalrGuidelines&#31;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Alinhe cláusulas de consulta sob o `From` instrução:  
  
     [!code-vb[32 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Use `Where` cláusulas antes de outras cláusulas de consulta para que as cláusulas de consulta posteriores operam em conjunto filtrado de dados:  
  
     [!code-vb[33 VbVbalrGuidelines](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Use o `Join` cláusula definir explicitamente uma operação de junção em vez de usar o `Where` cláusula implicitamente definir uma operação de junção:  
  
     [!code-vb[VbVbalrGuidelines&#34;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
