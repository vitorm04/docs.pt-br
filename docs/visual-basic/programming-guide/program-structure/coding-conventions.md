---
title: Convenções de codificação do Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: e036792cf33082fa78cf243887b8ac7db7f8ad5a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981485"
---
# <a name="visual-basic-coding-conventions"></a>Convenções de codificação do Visual Basic
A Microsoft desenvolve exemplos e documentação que seguem as diretrizes neste tópico. Se você seguir as mesmas convenções de codificação, você pode obter os seguintes benefícios:  
  
-   Seu código terá uma aparência consistente, para que os leitores possam focar melhor conteúdo, não o layout.  
  
-   Os leitores entendem seu código mais rapidamente porque podem fazer suposições com base na experiência anterior.  
  
-   Você pode copiar, alterar e manter o código mais facilmente.  
  
-   Você ajuda a garantir que seu código Demonstre as "práticas recomendadas" para o Visual Basic.  
  
## <a name="naming-conventions"></a>Convenções de nomenclatura  
  
-   Para obter informações sobre como nomear diretrizes, consulte [diretrizes de nomenclatura](../../../standard/design-guidelines/naming-guidelines.md) tópico.  
  
-   Não use "Meu" ou "Meu" como parte de um nome de variável. Esta prática cria confusão com o `My` objetos.  
  
-   Você não precisa alterar os nomes de objetos no código gerado automaticamente para torná-los de acordo com as diretrizes.  
  
## <a name="layout-conventions"></a>Convenções de Layout  
  
-   Insira guias como espaços e use o recuo inteligente com recuos de quatro espaços.  
  
-   Use **(reformatação) do código de reformatação** para reformatar o código no editor de códigos. Para obter mais informações, consulte [opções, Editor de texto, básico (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Use apenas uma declaração por linha. Não use o caractere de separador de linha (:) do Visual Basic.  
  
-   Evite usar o caractere de continuação de linha explícita "_" em favor da continuação implícita de linha sempre que a linguagem permitir.  
  
-   Use apenas uma declaração por linha.  
  
-   Se **(reformatação) do código de reformatação** não formatar linhas de continuação automaticamente, recue manualmente continuação linhas uma parada de tabulação. No entanto, sempre alinhado à esquerda itens em uma lista.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Adicione pelo menos uma linha em branco entre as definições de método e propriedade.  
  
## <a name="commenting-conventions"></a>Comentando Convenções  
  
-   Colocar comentários em uma linha separada, em vez de no final de uma linha de código.  
  
-   Inicie o texto do comentário com uma letra maiuscula e o texto de comentário final com um ponto.  
  
-   Insira um espaço entre o delimitador de comentário (') e o texto do comentário.  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
-   Não coloque comentários com blocos formatados de asteriscos.  
  
## <a name="program-structure"></a>Estrutura do programa  
  
-   Quando você usa o `Main` método, use a compilação padrão para novos aplicativos de console e usar `My` para argumentos de linha de comando.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Diretrizes de Linguagem  
  
### <a name="string-data-type"></a>Tipo de dados da cadeia de caracteres  
  
-   Para concatenar cadeias de caracteres, use um e comercial (&).  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
-   Para acrescentar cadeias de caracteres em loops, use o <xref:System.Text.StringBuilder> objeto.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Representantes reduzidos nos manipuladores de eventos  
 Não qualifique explicitamente os argumentos (objeto e EventArgs) para manipuladores de eventos. Se você não estiver usando os argumentos do evento que são passados para um evento (por exemplo, remetente como objeto, e como EventArgs), use representantes reduzidos e deixe os argumentos de evento em seu código:  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>Tipo de Dados Sem Sinal  
  
-   Use `Integer` em vez de tipos sem sinal, exceto onde forem necessários.  
  
### <a name="arrays"></a>Matrizes  
  
-   Use a sintaxe abreviada ao inicializar matrizes na linha da declaração. Por exemplo, use a sintaxe a seguir.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     Não use a sintaxe a seguir.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
-   Coloca o designador no tipo, não na variável. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     Não use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
-   Use a sintaxe {} quando você declarar e inicializar matrizes de tipos de dados básicos. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Não use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>Use o com a palavra-chave  
 Quando você faz uma série de chamadas para um objeto, considere o uso de `With` palavra-chave:  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Use a instrução Try... Catch e instruções Using ao usar o tratamento de exceções  
 Não use `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Use a palavra-chave IsNot  
 Use o `IsNot` palavra-chave, em vez de `Not...Is Nothing`.  
  
### <a name="new-keyword"></a>Nova palavra-chave  
  
-   Use a instanciação breve. Por exemplo, use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     A linha anterior é equivalente a esta:  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
-   Use inicializadores de objeto para novos objetos em vez do construtor sem parâmetros:  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Tratamento de Evento  
  
-   Use `Handles` em vez de `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
-   Use `AddressOf`e não uma instância do representante explicitamente:  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
-   Quando você define um evento, use a sintaxe abreviada e deixar que o compilador definir o delegado:  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
-   Não verificar se um evento é `Nothing` (null) antes de chamar o `RaiseEvent` método. `RaiseEvent` verifica se há `Nothing` antes que ele gera o evento.  
  
### <a name="using-shared-members"></a>Usando membros compartilhados  
 Chamar `Shared` membros usando o nome de classe, não de uma variável de instância.  
  
### <a name="use-xml-literals"></a>Usar literais XML  
 Literais XML simplificam as tarefas mais comuns encontrados ao trabalhar com XML (por exemplo, carregamento, consulta e transformação). Quando você desenvolve com XML, siga estas diretrizes:  
  
-   Use literais XML para criar documentos XML e fragmentos em vez de chamar APIs XML diretamente.  
  
-   Importe os namespaces XML no nível do arquivo ou projeto para tirar proveito das otimizações de desempenho para literais XML.  
  
-   Use as propriedades do eixo XML para acessar elementos e atributos em um documento XML.  
  
-   Usar expressões inseridas para incluir valores e criar o XML de valores existentes em vez de usar chamadas à API, como o `Add` método:  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>Consultas LINQ  
  
-   Use nomes significativos para variáveis de consulta:  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
-   Fornecer nomes de elementos em uma consulta para certificar-se de que os nomes de propriedade de tipos anônimos foram capitalizados corretamente usando Pascal de maiusculas e minúsculas:  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
-   Renomeie propriedades quando os nomes de propriedades no resultado forem ambíguos. Por exemplo, se sua consulta retornar um cliente, nome e uma ID de pedido, renomeá-los o em vez de deixá-los como `Name` e `ID` no resultado:  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
-   Use a inferência de tipo na declaração de variáveis de consulta e intervalo:  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
-   Alinhe cláusulas de consulta sob o `From` instrução:  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
-   Use `Where` cláusulas antes de outras cláusulas de consulta para que cláusulas de consulta posteriores operem no conjunto filtrado de dados:  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
-   Use o `Join` cláusula para definir explicitamente uma operação de junção em vez de usar o `Where` cláusula para definir implicitamente uma operação de junção:  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Consulte também
- [Diretrizes de codificação segura](../../../standard/security/secure-coding-guidelines.md)
