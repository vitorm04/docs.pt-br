---
title: "Eventos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "classes [c#], eventos"
  - "Linguagem c#, eventos"
  - "eventos [C#]"
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 43
caps.handback.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Eventos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Eventos permitem uma [classe](../../../csharp/language-reference/keywords/class.md) ou objeto para notificar outras classes ou objetos quando algo interessante ocorre. A classe que envia \(ou *gera*\) o evento é chamado de *publisher* e as classes que recebem \(ou *tratar*\) os eventos são chamados *assinantes*.  
  
 Em um aplicativo c\# Windows Forms ou Web típico, você assinar eventos gerados pelos controles como botões e caixas de listagem. Você pode usar o [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)] ambiente de desenvolvimento integrado \(IDE\) para procurar os eventos que publica um controle e selecione aqueles que você deseja manipular. O IDE adiciona automaticamente um método de manipulador de eventos vazio e o código para assinar o evento. Para obter mais informações, consulte [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## Visão geral sobre eventos  
 Eventos com as seguintes propriedades:  
  
-   O publisher determina quando um evento é gerado; os assinantes determinam a ação que é executada em resposta ao evento.  
  
-   Um evento pode ter vários assinantes. Um assinante pode manipular vários eventos de vários editores.  
  
-   Eventos que não tenham nenhum assinante nunca são gerados.  
  
-   Normalmente, os eventos são usados para sinalizar a ações do usuário, como cliques de botão ou seleções de menu em interfaces gráficas do usuário.  
  
-   Quando um evento tem vários assinantes, os manipuladores de eventos são chamados sincronicamente quando um evento é gerado. Para invocar eventos de forma assíncrona, consulte [Chamando métodos síncronos de forma assíncrona](../Topic/Calling%20Synchronous%20Methods%20Asynchronously.md).  
  
-   No [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] biblioteca de classes, eventos são baseados no <xref:System.EventHandler> delegar e <xref:System.EventArgs> classe base.  
  
## Seções relacionadas  
 Para obter mais informações, consulte:  
  
-   [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Como acionar eventos de classe base em classes derivadas](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Sincronização de thread](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)  
  
-   [Como usar um dicionário para armazenar instâncias de eventos](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Como implementar acessadores de eventos personalizados](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Capítulos do livro em destaque  
 [Delegados, eventos e expressões Lambda](http://go.microsoft.com/fwlink/?LinkId=195395) na [c\# 3.0 Cookbook, terceira edição: mais de 250 soluções para programadores de c\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Delegados e eventos](http://go.microsoft.com/fwlink/?LinkId=195418) na [aprendizado c\# 3.0: domine os fundamentos do c\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## Consulte também  
 <xref:System.EventHandler>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Criando manipuladores de eventos no Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)   
 [Programação multithreaded com o padrão assíncrono baseado em evento](../Topic/Multithreaded%20Programming%20with%20the%20Event-based%20Asynchronous%20Pattern.md)