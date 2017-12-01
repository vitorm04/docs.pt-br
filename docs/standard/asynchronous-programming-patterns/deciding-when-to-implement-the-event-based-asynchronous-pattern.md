---
title: "Decidindo quando implementar o padrão assíncrono baseado em evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48de1b736c251a61a2ad34975c77bc2bca139626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Decidindo quando implementar o padrão assíncrono baseado em evento
O padrão assíncrono baseado em evento fornece um padrão para expor o comportamento assíncrono de uma classe. Com a introdução deste padrão, o [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] define dois padrões para expor o comportamento assíncrono: o padrão assíncrono baseado no <xref:System.IAsyncResult?displayProperty=nameWithType> interface e o padrão de evento. Este tópico descreve quando é apropriado para implementar ambos os padrões.  
  
 Para obter mais informações sobre a programação assíncrona com o <xref:System.IAsyncResult> interface, consulte [padrão assíncrono baseado em evento (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
## <a name="general-principles"></a>Princípios gerais  
 Em geral, você deve expor recursos assíncronos usando o padrão de assíncrono baseado em evento sempre que possível. No entanto, há alguns requisitos que o padrão de evento não pode atender. Nesses casos, talvez seja necessário implementar o <xref:System.IAsyncResult> padrão além do padrão baseado em evento.  
  
> [!NOTE]
>  É raro para o <xref:System.IAsyncResult> padrão a ser implementada sem o padrão de evento também sendo implementado.  
  
## <a name="guidelines"></a>Diretrizes  
 A lista a seguir descreve as diretrizes de quando você deve implementar o padrão assíncrono baseado em evento:  
  
-   Use o padrão de evento como a API padrão para expor o comportamento assíncrono para sua classe.  
  
-   Não exponha o <xref:System.IAsyncResult> padrão quando a classe é usada principalmente em um aplicativo cliente, por exemplo, Windows Forms.  
  
-   Apenas expor o <xref:System.IAsyncResult> padrão quando é necessário para atender às suas necessidades. Por exemplo, compatibilidade com uma API existente pode exigir que você exponha o <xref:System.IAsyncResult> padrão.  
  
-   Não exponha o <xref:System.IAsyncResult> padrão sem também expor o padrão de evento.  
  
-   Se você precisar expor o <xref:System.IAsyncResult> padrão, isso como uma opção avançada. Por exemplo, se você gerar um objeto de proxy, gerar o padrão baseado em evento por padrão, com uma opção para gerar o <xref:System.IAsyncResult> padrão.  
  
-   Sua implementação do padrão com base em eventos de compilação seu <xref:System.IAsyncResult> implementação do padrão.  
  
-   Evitar a exposição de ambas as padrão baseado em evento e o <xref:System.IAsyncResult> padrão na mesma classe. Expor o padrão com base em eventos em classes "de nível superior" e o <xref:System.IAsyncResult> padrão classes em "nível inferior". Por exemplo, comparar o padrão baseado em evento no <xref:System.Net.WebClient> componente com o <xref:System.IAsyncResult> padrão no <xref:System.Web.HttpRequest> classe.  
  
    -   Expor o padrão de evento e o <xref:System.IAsyncResult> padrão da mesma classe quando compatibilidade exija isso. Por exemplo, se você já lançou uma API que usa o <xref:System.IAsyncResult> padrão, você precisa manter o <xref:System.IAsyncResult> padrão para compatibilidade com versões anteriores.  
  
    -   Expor o padrão de evento e o <xref:System.IAsyncResult> se a complexidade de modelo de objeto resultante supera o benefício de separar as implementações do padrão da mesma classe. É melhor para expor os dois padrões em uma única classe que ao evitar expor o padrão de evento.  
  
    -   Se você deve expor ambos o padrão com base em eventos e <xref:System.IAsyncResult> padrão em uma única classe, use <xref:System.ComponentModel.EditorBrowsableAttribute> definida como <xref:System.ComponentModel.EditorBrowsableState.Advanced> para marcar o <xref:System.IAsyncResult> implementação do padrão como um recurso avançado. Isso indica a ambientes de design, como [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] IntelliSense, para não exibir o <xref:System.IAsyncResult> propriedades e métodos. Essas propriedades e métodos ainda são totalmente utilizáveis, mas o desenvolvedor trabalhando por meio do IntelliSense tem uma visão clara da API.  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Critérios para expor o padrão de IAsyncResult além do padrão baseado em evento  
 Enquanto o padrão assíncrono baseado em evento tem muitas vantagens em cenários de mencionadas anteriormente, ele tem apresenta algumas desvantagens, você deve estar ciente de desempenho é o requisito mais importante.  
  
 Há três cenários que não lida com o padrão baseado em evento, bem como a <xref:System.IAsyncResult> padrão:  
  
-   Bloqueio de espera em um<xref:System.IAsyncResult>  
  
-   Bloqueio de espera em muitas <xref:System.IAsyncResult> objetos  
  
-   Sondagem de conclusão no<xref:System.IAsyncResult>  
  
 Você pode abordar esses cenários usando o padrão baseado em evento, mas isso é mais complicado do que usando o <xref:System.IAsyncResult> padrão.  
  
 Os desenvolvedores geralmente usam o <xref:System.IAsyncResult> padrão para os serviços que normalmente têm requisitos de desempenho muito alto. Por exemplo, a sondagem para o cenário de conclusão é uma técnica de servidor de alto desempenho.  
  
 Além disso, o padrão de evento é menos eficiente do que o <xref:System.IAsyncResult> padrão porque ela cria mais objetos, especialmente <xref:System.EventArgs>, e como elas são sincronizadas entre threads.  
  
 A lista a seguir mostra algumas recomendações a seguir se você decidir usar o <xref:System.IAsyncResult> padrão:  
  
-   Apenas expor o <xref:System.IAsyncResult> padrão quando você precisar do suporte para especificamente <xref:System.Threading.WaitHandle> ou <xref:System.IAsyncResult> objetos.  
  
-   Apenas expor o <xref:System.IAsyncResult> padrão quando você tem uma API existente que usa o <xref:System.IAsyncResult> padrão.  
  
-   Se você tiver uma API existente com base no <xref:System.IAsyncResult> padrão, considere também expor o padrão baseado em evento em sua próxima versão.  
  
-   Apenas expor <xref:System.IAsyncResult> padrão se você tiver requisitos de alto desempenho que você verificou se não podem ser atendida pelo padrão baseado em evento, mas podem ser atendida pelo <xref:System.IAsyncResult> padrão.  
  
## <a name="see-also"></a>Consulte também  
 [Instruções passo a passo: implementando um componente compatível com o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Programação multi-threaded com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Implementando o Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Práticas recomendadas para a implementação do Padrão Assíncrono baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Visão Geral do Padrão Assíncrono Baseado em Evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
