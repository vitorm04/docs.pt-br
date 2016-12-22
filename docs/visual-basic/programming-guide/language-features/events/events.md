---
title: "Eventos (Visual Basic) | Microsoft Docs"
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
  - "eventos [Visual Basic]"
  - "eventos [Visual Basic], sobre eventos"
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eventos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Enquanto você pode visualizar um projeto [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] como uma série de procedimentos que executam em uma sequência, na realidade, a maioria dos programas são orientados a eventos — o que significa que o fluxo de execução é determinado pelas externas ocorrências chamadas  *eventos* .  
  
 Um evento é um sinal que informa a um aplicativo que algo importante ocorreu.  Por exemplo, quando um usuário clica em um controle em um formulário, o formulário pode lançar um evento `Click` e chamar um procedimento que manipula o evento.  Eventos também permitem que tarefas separadas se comuniquem.  Digamos que, por exemplo, seu aplicativo execute uma tarefa de classificação separadamente do aplicativo principal.  Se um usuário cancelar a classificação, o aplicativo pode enviar um evento Cancelar instruindo o processo de classificação para parar.  
  
## Termos e Conceitos de Evento  
 Esta seção descreve os termos e conceitos usados com eventos em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
### Declarando Eventos  
 Você declara eventos dentro de classes, estruturas, módulos e interfaces usando a palavra\-chave `Event`, como no exemplo a seguir:  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]  
  
### Disparando Eventos  
 Um evento é como uma mensagem anunciando que algo importante ocorreu.  O ato de transmitir a mensagem é chamado *Disparo* de evento.  Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)],você dispara eventos com a instrução `RaiseEvent`, como no exemplo a seguir:  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]  
  
 Eventos devem ser disparados dentro do escopo da classe, módulo ou estrutura onde eles são declarados.  Por exemplo, um classe derivada não pode disparar eventos herdados de um classe base.  
  
### Remetentes de Evento  
 Qualquer objeto capaz de dispara um evento é um  *Remetente de Evento* ,também conhecido como uma  *fonte de evento* .  Formulários, controles e objetos definidos pelo usuário são exemplos de remetentes de eventos.  
  
### Manipuladores de Eventos  
 *Manipuladores de eventos* são procedimentos que são chamados quando ocorre um evento correspondente.  Você pode usar qualquer sub\-rotina válida com uma assinatura correspondente como um manipulador de eventos.  Entretanto, você não pode usar uma função como um manipulador de eventos, porque ela não retorna um valor para a fonte de eventos.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usa uma convenção de nomeclatura padrão para manipuladores de eventos que combina o nome do remetente do evento, um sublinhado e o nome do evento.  Por exemplo, o evento `Click` de um botão chamado `button1` será nomeado `Sub button1_Click`.  
  
> [!NOTE]
>  Recomendamos que você use esta convenção de nomeclatura quando definir manipuladores de eventos para seus próprios eventos, mas ela não é necessário; você pode usar qualquer nome de sub\-rotina válido.  
  
## Associando Eventos Manipuladores de Eventos  
 Antes uma manipulador de eventos se tornar útil, você deve primeiro associá\-lo com um evento usando uma instrução `Handles` ou `AddHandler`.  
  
### WithEvents e Cláusula Handles  
 A instrução `WithEvents` e a cláusula `Handles` fornecem uma maneira declarativa de especificar os manipuladores de eventos.  Um evento gerado por um objeto declarado com a palavra\-chave `WithEvents` pode ser tratado por qualquer procedimento com uma instrução `Handles` para esse evento, conforme mostrado no exemplo o seguir:  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]  
  
 A instrução `WithEvents` e a cláusula `Handles` geralmente são a melhor opção para manipuladores de eventos pois a sintaxe declarativa usada torna mais fácil de codificar, ler e depurar a manipulação de eventos.  No entanto, esteja ciente das seguintes limitações sobre o uso de variáveis `WithEvents`:  
  
-   Não é possível usar uma variável `WithEvents` como um variável de objeto.  Ou seja, você não pode declará\-la como `Object` — você deve especificar o nome da classe quando você declarar a variável.  
  
-   Porque compartilhado eventosnão são vinculado às ocorrências da classe, não é possível usar `WithEvents` declarativamente manipular eventos compartilhados.  Da mesma forma, você não pode usar `WithEvents` ou `Handles` para manipular eventos de um `Structure`.  Em ambos os casos, você pode usar a instrução `AddHandler` para manipular esses eventos.  
  
-   Não é possível criar matrizes de `WithEvents` variáveis.  
  
 `WithEvents` variáveis permitem a um único manipulador de eventos manipular um ou mais tipo de evento, ou um ou mais manipuladores de eventos para manipular o mesmo tipo de evento.  
  
 Embora a cláusula `Handles` seja a maneira padrão de associar um manipulador de eventos com um evento, é limitada ao associar eventos com manipuladores de eventos em tempo de compilação.  
  
 Em alguns casos, como com os eventos associados com os formulários ou controles, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] automaticamente extingue um manipulador de eventos em branco e o associa com um evento.  Por exemplo, quando você clica duas vezes em um botão de comando em um formulário no modo de design, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cria um manipulador de eventos em branco e uma variável `WithEvents` para o botão de comando, como no código a seguir:  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]  
  
### AddHandler e RemoveHandler  
 A instrução `AddHandler` é semelhante à cláusula `Handles` já que ambas permitem que você especifique um manipulador de eventos.  Entretanto, `AddHandler` usado com `RemoveHandler`, fornece flexibilidade maior do que a cláusula `Handles`, permitindo que você adicione, remova e altere dinamicamente o manipulador de evento associado com um evento.  Se você quiser manipular eventos compartilhados ou eventos de uma estrutura, você deve usar `AddHandler`.  
  
 `AddHandler` necessita de dois argumentos: o nome de um evento a partir de um gerador de evento tal como um controle, e uma expressão que avalia um representante.  Você não precisa especificar explicitamente a classe representante ao usar `AddHandler`, desde que a declaração `AddressOf` sempre retorne uma referência ao representante.  O exemplo a seguir associa um manipulador de evento com um evento gerado por um objeto.  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]  
  
 `RemoveHandler`, que disconecta um evento de um manipulador de eventos, usa a mesma sintaxe de `AddHandler`.  Por exemplo:  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]  
  
 No exemplo a seguir, um manipulador de eventos está associado um evento e o evento é gerado.  O manipulador de eventos captura o evento e exibe uma mensagem.  
  
 Em seguida, o manipulador de eventos a primeiro é removido e um manipulador de eventos diferente está associado com o evento.  Quando o evento é gerado novamente, é exibida uma mensagem diferente.  
  
 Finalmente, o segundo manipulador de eventos é removido e o evento é gerado pela terceira vez.  Porque não existe mais um manipulador de eventos associado ao evento, nenhuma ação é executada.  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]  
  
## Manipulado Eventos Herdados de uma Classe Base  
 *Classes derivadas*– classes que herdam as características de uma classe base — podem tratar eventos originados por sua classe base usando o `Handles``MyBase` instrução.  
  
#### Para manipular eventos de uma classe base  
  
-   Declare um manipulador de eventos na classe derivada adicionando uma declaração `Handles MyBase.`*nomedoevento* na declaração  de seu evento manipulador de eventos, onde *nomedoevento* é o nome do evento na classe base manipulada.  Por exemplo:  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]  
  
## Seções relacionadas  
  
|Título|Descrição|  
|------------|---------------|  
|[Instruções passo a passo: declarando e acionando eventos](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Fornece uma descrição passo a passo de como declarar e disparar eventos para uma classe.|  
|[Instruções passo a passo: tratando eventos](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md)|Demonstra como escrever um procedimento de manipulador de eventos.|  
|[Como declarar eventos personalizados para evitar bloqueio](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Demonstra como definir um evento personalizado que permite que seus manipuladores de evento sejam chamados assincronamente.|  
|[Como declarar eventos personalizados para conservar memória](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Demonstra como definir um evento personalizado que utiliza a memória somente quando o evento é manipulado.|  
|[Solucionando problemas de manipuladores de eventos herdados no Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Lista problemas comuns que surgem com manipuladores evento nos componentes herdados|  
|[Eventos](../Topic/Handling%20and%20Raising%20Events.md)|Fornece uma visão geral sobre o modelo de evento no [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].|  
|[Criando manipuladores de eventos no Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)|Descreve como trabalhar com eventos associados aos objetos Windows Forms.|  
|[Delegados](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)|Fornece uma visão geral dos delegados no Visual Basic.|