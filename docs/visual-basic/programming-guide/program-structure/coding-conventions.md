---
title: "Conven&#231;&#245;es de codifica&#231;&#227;o do Visual Basic | Microsoft Docs"
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
  - "convenções de codificação, Visual Basic"
  - "exemplos [Visual Basic], convenções de codificação"
  - "código do Visual Basic, convenções"
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
caps.latest.revision: 48
caps.handback.revision: 48
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conven&#231;&#245;es de codifica&#231;&#227;o do Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A Microsoft desenvolve exemplos e documentação que seguem as diretrizes contidas neste tópico.  Se você seguir as mesmas convenções de codificação, poderá obter os seguintes benefícios:  
  
-   O código terá uma aparência consistente, de modo que os leitores possam focar melhor o conteúdo, não o layout.  
  
-   Os leitores entendem seu código de forma mais rápida porque podem fazer as suposições com base na experiência anterior.  
  
-   Você pode copiar, modificar e manter o código mais facilmente.  
  
-   Você ajuda a garantir que seu código demonstre as “práticas recomendadas” para o Visual Basic.  
  
## Convenções de nomenclatura  
  
-   Para obter informações sobre como nomear diretrizes, consulte o tópico [Diretrizes de nomenclatura](../Topic/Naming%20Guidelines.md).  
  
-   Não use “Meu\/Minha” ou “meu\/minha” como parte de um nome de variável.  Esta prática cria confusão com os objetos de `My`.  
  
-   Não é necessário alterar os nomes dos objetos no código gerado automaticamente para ajustá\-los de acordo com as diretrizes.  
  
## Convenções de Layout  
  
-   Insira guias como espaços e use o recuo inteligente com recuos de quatro espaços.  
  
-   Use **Reformatação automática de código** para reformatar o código no editor de códigos.  Para obter mais informações, consulte [Opções, Editor de Texto, Básico \(Visual Basic\)](/visual-studio/ide/reference/options-text-editor-basic-visual-basic).  
  
-   Use apenas uma declaração por linha.  Não use o caractere do Visual Basic de separador \(:\).  
  
-   Evite usar o caractere de continuação de linha explícita “\_” em favor da continuação de linha implícita onde a linguagem permitir.  
  
-   Use apenas uma declaração por linha.  
  
-   Se **Reformatação automática de código** não formatar as linhas de continuação automaticamente, recue manualmente uma parada de tabulação das linhas de continuação.  No entanto, alinhe os itens sempre à esquerda em uma lista.  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   Adicione pelo menos uma linha em branco entre o método e as definições de propriedade.  
  
## Comentando Convenções  
  
-   Colocar comentários em uma linha separada, em vez no final de uma linha de código.  
  
-   Inicie o texto de comentário com uma letra maiúscula, e o texto do comentário de fim com um ponto.  
  
-   Insira um espaço entre o delimitador de comentário \('\) e o texto do comentário.  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   Não coloque comentários com blocos formatados de asteriscos.  
  
## Estrutura do Programa  
  
-   Quando você usar o método de `Main`, use a compilação padrão para novos aplicativos de console, e use `My` para argumentos de linha de comando.  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## Diretrizes de Linguagem  
  
### Tipo de dados de cadeia de caracteres  
  
-   Para concatenar as cadeias de caracteres, use um E comercial \(&\).  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   Para acrescentar cadeias de caracteres em loops, use o objeto de <xref:System.Text.StringBuilder>.  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### Representantes reduzidos nos manipuladores de eventos  
 Não qualifique explicitamente os argumentos \(objeto e EventArgs\) para manipuladores de eventos.  Se você não estiver usando os argumentos de evento passados para um evento \(por exemplo, remetente como como Object e como EventArgs\), use representantes o objeto, e como EventArgs\), use representantes reduzidos e ignore os argumentos de evento em seu código:  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### Tipo de Dados Sem Sinal  
  
-   Use `Integer` em vez dos tipos sem sinal, exceto onde forem necessários.  
  
### Matrizes  
  
-   Use a sintaxe abreviada ao inicializar matrizes na linha da declaração.  Por exemplo, a seguinte sintaxe.  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     Não use a seguinte sintaxe.  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   Colocar o designador no tipo, não na variável.  Por exemplo, a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     Não use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   Use a sintaxe {} quando ao declarar e inicializar matrizes de tipos de dados básicos.  Por exemplo, a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     Não use a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### Use a palavra\-chave With  
 Ao fazer uma série de chamadas para um objeto, considere usar a palavra\-chave `With`:  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### Use as declarações Try, Catch e Using ao usar o tratamento de exceções  
 Não use `On Error Goto`.  
  
### Use a palavra\-chave IsNot  
 Use a palavra\-chave `IsNot`, em vez de `Not...Is Nothing`.  
  
### Nova palavra\-chave  
  
-   Use a instanciação breve.  Por exemplo, a seguinte sintaxe:  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     A linha anterior é equivalente a:  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   Use inicializadores de objeto para novos objetos em vez do construtor sem parâmetros:  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### Tratamento de Evento  
  
-   Use `Handles` em vez de `AddHandler`:  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   Use `AddressOf`, e não crie uma instância do representante explicitamente:  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   Ao definir um evento, use a sintaxe abreviada, e deixe o compilador definir a delegação:  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   Não verifique se um evento é `Nothing` \(zero\) antes de chamar o método `RaiseEvent`.  `RaiseEvent` verifica `Nothing` antes que ele gere o evento.  
  
### Usando membros compartilhados  
 Chamar membros de `Shared` usando o nome da classe, não de uma variável de instância.  
  
### Use literais de XML  
 Literais XML simplificam as tarefas mais comuns que você encontrar quando você trabalha com XML \(por exemplo, o carregamento, consulta e transformação\).  Ao desenvolver com XML, siga estas diretrizes:  
  
-   Use literais de XML para criar documentos XML e fragmentos em vez de chamar diretamente as APIs de XML.  
  
-   Importe namespaces XML no nível do arquivo ou do projeto para tirar proveito das otimizações de desempenho para literais XML.  
  
-   Use as propriedades de eixo XML para acessar elementos e atributos em um documento XML.  
  
-   Usar expressões inseridas para incluir valores e criar XML a partir de valores existentes em vez de usar chamadas à API como o método de `Add`:  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### Consultas LINQ  
  
-   Use nomes significativos para as variáveis de consulta:  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   Forneça nomes de elementos em uma consulta para certificar\-se de que os nomes de propriedade de tipos anônimos foram capitalizados corretamente usando a capitalização Pascal:  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   Renomear propriedades quando os nomes de propriedade no resultado forem ambíguos.  Por exemplo, se sua consulta retornar um nome de cliente e uma identificação de ordem, renomeie\-os em vez de deixá\-los como `Name` e `ID` no resultado:  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   Use a inferência de tipos na declaração de variáveis de consulta e de variáveis de intervalo:  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   Alinhar cláusulas de consulta sob a declaração `From`:  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   Use as cláusulas `Where` antes de outras cláusulas de consulta para que as cláusulas posteriores de consulta operem no conjunto filtrado de dados:  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   Use a cláusula `Join` para definir explicitamente uma operação de associação em vez de usar a cláusula `Where` para definir implicitamente uma operação de associação:  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## Consulte também  
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)