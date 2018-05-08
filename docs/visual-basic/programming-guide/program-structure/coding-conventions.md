---
title: Convenções de codificação do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: b686747b46529b53b0802a7deb38b5b4949f4d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="visual-basic-coding-conventions"></a>Convenções de codificação do Visual Basic
A Microsoft desenvolve amostras e documentação que siga as diretrizes neste tópico. Se você seguir as mesmas convenções de codificação, você pode obter os seguintes benefícios:  
  
-   Seu código terá uma aparência consistente, para que os leitores concentrar-se no conteúdo, não o layout.  
  
-   Leitores de compreendam o código mais rapidamente porque ele possa fazer suposições com base em experiências anteriores.  
  
-   Você pode copiar, alterar e manter o código mais facilmente.  
  
-   Ajudar a garantir que seu código demonstra "práticas recomendadas" para o Visual Basic.  
  
## <a name="naming-conventions"></a>Convenções de nomenclatura  
  
-   Para obter informações sobre as diretrizes de nomenclatura, consulte [diretrizes de nomenclatura](../../../standard/design-guidelines/naming-guidelines.md) tópico.  
  
-   Não use "Meu" ou "Meu" como parte de um nome de variável. Essa prática cria confusão com o `My` objetos.  
  
-   Você não precisa alterar os nomes de objetos no código gerado automaticamente para ajustar as diretrizes.  
  
## <a name="layout-conventions"></a>Convenções de Layout  
  
-   Inserir tabulações como espaços e use o recuo inteligente com espaço em quatro recuos.  
  
-   Use **(reformatação) do código de reformatação** reformatar seu código no editor de códigos. Para obter mais informações, consulte [opções, Editor de texto, básico (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Use somente uma instrução por linha. Não use o caractere de separador de linha do Visual Basic (:).  
  
-   Evite usar o caractere de continuação de linha explícita "_" em favor de continuação de linha implícitas sempre que o idioma permite que ele.  
  
-   Use somente uma declaração por linha.  
  
-   Se **(reformatação) do código de reformatação** não formatar linhas de continuação automaticamente, manualmente Recuar continuação linhas uma parada de tabulação. No entanto, sempre esquerda itens em uma lista.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Adicione pelo menos uma linha em branco entre as definições de método e propriedade.  
  
## <a name="commenting-conventions"></a>Comentando Convenções  
  
-   Inserir comentários em uma linha separada, em vez de no final de uma linha de código.  
  
-   Inicie o texto de comentário com uma letra maiuscula e texto de comentário final com um ponto.  
  
-   Insira um espaço entre o delimitador de comentário (') e o texto do comentário.  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Não coloque os comentários com blocos formatados de asteriscos.  
  
## <a name="program-structure"></a>Estrutura do programa  
  
-   Quando você usa o `Main` método, use o construtor padrão para novos aplicativos de console e usar `My` para argumentos de linha de comando.  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a>Diretrizes de Linguagem  
  
### <a name="string-data-type"></a>Tipo de dados da cadeia de caracteres  
  
-   Para concatenar cadeias de caracteres, use um e comercial (&).  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Para acrescentar cadeias de caracteres em loops, use o <xref:System.Text.StringBuilder> objeto.  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Delegados reduzidos em manipuladores de eventos  
 Não qualifique explicitamente os argumentos (objeto e EventArgs) para manipuladores de eventos. Se você não estiver usando os argumentos de evento que são passados para um evento (por exemplo, o remetente como objeto, e como EventArgs), usar delegados reduzidos e omitir os argumentos do evento no seu código:  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a>Tipo de Dados Sem Sinal  
  
-   Use `Integer` em vez de tipos não assinados, exceto onde eles são necessários.  
  
### <a name="arrays"></a>Matrizes  
  
-   Use a sintaxe curta quando você inicializa matrizes na linha da declaração. Por exemplo, use a sintaxe a seguir.  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Não use a sintaxe a seguir.  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Coloque o designador de matriz do tipo, não na variável. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Não use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Use a sintaxe {} quando você declara e inicializar matrizes de tipos de dados básicos. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Não use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a>Use a palavra-chave With  
 Quando você faz uma série de chamadas para um objeto, considere o uso de `With` palavra-chave:  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Use o bloco Try... Catch e instruções Using ao usar o tratamento de exceção  
 Não use `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Use a palavra-chave IsNot  
 Use o `IsNot` palavra-chave em vez de `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>Palavra-chave New  
  
-   Use instanciação curta. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     A linha anterior é equivalente a esta:  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Inicializadores de objeto de uso para novos objetos, em vez do construtor sem parâmetros:  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a>Tratamento de Evento  
  
-   Use `Handles` em vez de `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Use `AddressOf`e não instanciar o delegado explicitamente:  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Quando você define um evento, use a sintaxe de curta e deixar que o compilador definir o representante:  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Não verificar se um evento é `Nothing` (null) antes de chamar o `RaiseEvent` método. `RaiseEvent` verifica se há `Nothing` antes de gerar o evento.  
  
### <a name="using-shared-members"></a>Usando membros compartilhados  
 Chamar `Shared` membros usando o nome de classe, não a partir de uma variável de instância.  
  
### <a name="use-xml-literals"></a>Use literais XML  
 Literais XML simplificam as tarefas mais comuns que você encontrar ao trabalhar com XML (por exemplo, carga, consulta e transformação). Quando você desenvolve com XML, siga estas diretrizes:  
  
-   Use literais XML para criar documentos XML e fragmentos em vez de chamar APIs XML diretamente.  
  
-   Importe os namespaces XML no nível de arquivo ou projeto para aproveitar as otimizações de desempenho para literais XML.  
  
-   Use as propriedades do eixo XML para acessar elementos e atributos em um documento XML.  
  
-   Use expressões inseridas para incluir valores e criar o XML de valores existentes em vez de usar chamadas de API, como o `Add` método:  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a>Consultas LINQ  
  
-   Use nomes significativos para variáveis de consulta:  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Fornecer nomes de elementos em uma consulta para certificar-se de que os nomes de propriedades de tipos anônimos estão corretamente em maiusculas usando Pascal de maiusculas e minúsculas:  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos. Por exemplo, se a consulta retornar um cliente, nome e uma ID de ordem, renomeá-los o em vez de deixá-los como `Name` e `ID` no resultado:  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Use a inferência de tipo na declaração de variáveis de consulta e as variáveis de intervalo:  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Alinhar as cláusulas de consulta sob o `From` instrução:  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Use `Where` cláusulas antes de outras cláusulas de consulta para que as cláusulas de consulta mais recente operam em conjunto de dados filtrado:  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Use o `Join` cláusula para definir explicitamente uma operação de junção em vez de usar o `Where` cláusula para definir implicitamente uma operação de junção:  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de codificação segura](../../../standard/security/secure-coding-guidelines.md)
