---
title: "Como implementar acessadores de eventos personalizados (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "acessadores [C#], acessadores de eventos"
  - "acessador add [C#]"
  - "eventos [C#], acessador add"
  - "eventos [C#], acessador remove"
  - "acessador remove [C#]"
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como implementar acessadores de eventos personalizados (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um evento é um tipo especial de delegado multicast que pode ser chamado apenas de dentro da classe declarada na.  Código do cliente se inscreve para o evento, fornecendo uma referência a um método que deve ser chamado quando o evento é acionado.  Esses métodos são adicionados à lista de invocação de delegado por meio de acessadores de evento, que se assemelham às acessadores da propriedade, exceto que os acessadores de evento são nomeados `add` e `remove`.  Na maioria dos casos, você não precisa fornecer acessadores de evento personalizado.  Quando nenhum acessador do evento personalizado é fornecidos em seu código, o compilador adicionará automaticamente.  No entanto, em alguns casos você terá que fornecer um comportamento personalizado.  Por exemplo, é mostrado no tópico [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## Exemplo  
 O exemplo a seguir mostra como implementar personalizados adicionar e remover acessadores de evento.  Embora você pode substituir qualquer código dentro dos acessadores, recomendamos que você bloqueie o evento antes de adicionar ou remover um novo método de manipulador de eventos.  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
  
```  
  
## Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)