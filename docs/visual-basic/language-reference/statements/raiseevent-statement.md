---
title: "Instru&#231;&#227;o RaiseEvent | Microsoft Docs"
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
  - "vb.RaiseEventMethod"
  - "vb.RaiseEvent"
  - "RaiseEvent"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "manipuladores de eventos, conectando eventos a"
  - "Instrução RaiseEvent"
  - "disparando eventos, Instrução RaiseEvent"
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o RaiseEvent
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dispara um evento declarado no nível de módulo dentro uma classe, formulário ou documento.  
  
## Sintaxe  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## Partes  
 `eventname`  
 Obrigatório.  Nome do evento para Disparar.  
  
 `argumentlist`  
 Opcional.  Lista delimitada por vírgulas de variáveis, matrizes ou expressões.  O `argumentlist` argumento deve estar entre parênteses.  Se não houver nenhum argumento, os parênteses devem ser omitidos.  
  
## Comentários  
 Os `eventname` é o nome de um evento é declarado dentro do módulo.  Ele segue as convenções de nomenclatura de variáveis de Visual Basic.  
  
 Se o evento não foi declarado dentro do módulo no qual ele é disparado, ocorrerá um erro.  O fragmento de código a seguir ilustra uma declaração de evento e um procedimento no qual o evento é gerado.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Não é possível usar `RaiseEvent` para gerar eventos que não são explicitamente declarados no módulo.  Por exemplo, todos os formulários herdam uma <xref:System.Windows.Forms.Control.Click> o evento de <xref:System.Windows.Forms.Form?displayProperty=fullName>, não pode ser elevada usando `RaiseEvent` em um formulário derivado.  Se você declarar um `Click` evento no módulo de formulário, as sombras do formulário próprio <xref:System.Windows.Forms.Control.Click> evento.  Você ainda pode invocar o formulário <xref:System.Windows.Forms.Control.Click> evento chamando o <xref:System.Windows.Forms.Control.OnClick%2A> método.  
  
 Por padrão, um evento definido em Visual Basic dispara seus manipuladores de eventos na ordem em que as conexões são estabelecidas.  Como os eventos podem ter `ByRef` parâmetros, um processo que conecta mais tarde poderá receber a parâmetros que foram alterados por um manipulador de eventos anterior.  Depois de executar os manipuladores de eventos, o Controlador é retornado para a sub\-rotina que disparou o evento.  
  
> [!NOTE]
>  Eventos não compartilhados não devem ser elevados dentro do construtor da classe em que elas são declaradas.  Embora esses eventos não causem erros de tempo de execução, eles podem não ser detectadas por manipuladores de evento associado.  Use o `Shared` modificador para criar um evento compartilhado se você precisar elevar um evento de um construtor.  
  
> [!NOTE]
>  Você pode alterar o comportamento padrão de eventos, definindo um evento personalizado.  Para eventos personalizados, a instrução `RaiseEvent` chama o evento do acessador `RaiseEvent`.  Para obter mais informações sobre eventos personalizados, consulte [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## Exemplo  
 O exemplo a seguir usa os eventos com a contagem regressiva de segundos de 10 a 0.  O código ilustra vários dos métodos relacionados a eventos, propriedades e instruções, incluindo o `RaiseEvent` instrução.  
  
 A classe que gera um evento é a origem de evento, e os métodos que processam o evento são os manipuladores de eventos.  Uma fonte de eventos pode ter vários manipuladores para eventos que ela gera.  Quando a classe gera o evento, esse evento é gerado em cada classe que decidiu manipular eventos para essa instância do objeto.  
  
 O exemplo também usa um formulário \(`Form1`\) com um botão \(`Button1`\) e um caixa de texto \(`TextBox1`\).  Quando você clica no botão, a primeira caixa de texto exibe uma contagem regressiva de 10 para 0 segundos.  Quando o tempo total \(10 segundos\) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
 O código `Form1` especifica os estados do formulário inicial e de terminal.  Ele também contém o código executado quando os eventos são gerados.  
  
 Para usar este exemplo, abra um novo projeto de aplicativo do Windows, adicione um botão denominado `Button1` e uma caixa de texto denominada `TextBox1` para o formulário principal, chamado `Form1`.  Em seguida, clique com o botão direito do formulário e clique em  **Exibir código** para abrir o Editor de código.  
  
 Adicionar um `WithEvents` para a seção de declarações de variável de `Form1` classe.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## Exemplo  
 Adicione o seguinte código para o evento `Form1` .  Substituir qualquer procedimentos duplicados que podem existir, como `Form_Load`, ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Pressione F5 para executar o exemplo anterior e clique no botão  **Iniciar**.  A primeira caixa de texto inicia a contagem regressiva de segundos.  Quando o tempo total \(10 segundos\) tiver decorrido, a primeira caixa de texto exibe "Concluído".  
  
> [!NOTE]
>  O método `My.Application.DoEvents` não processa os eventos da exatamente a mesma forma como faz o formulário.  Para permitir que o formulário manipular os eventos diretamente, você pode usar multithreading.  Para obter mais informações, consulte [Threading](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Consulte também  
 [Eventos](../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Instrução Event](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Instrução AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Instrução RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)