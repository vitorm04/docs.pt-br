---
title: "Como implementar acessadores de eventos personalizados (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 71e1c16c9c6426ffb95020e4d7211dc1000f6796
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Como implementar acessadores de eventos personalizados (Guia de Programação em C#)
Um evento é um tipo especial de delegado multicast que só pode ser invocado de dentro da classe que ela está declarado. O código cliente assina o evento ao fornecer uma referência a um método que deve ser invocado quando o evento for disparado. Esses métodos são adicionados à lista de invocação do delegado por meio de acessadores de evento, que se assemelham aos acessadores de propriedade, com a exceção de que os acessadores de eventos são nomeados `add` e `remove`. Na maioria dos casos, não é necessário fornecer acessadores de eventos personalizados. Quando nenhum acessador de evento personalizado for fornecido no código, o compilador o adicionará automaticamente. No entanto, em alguns casos será necessário fornecer um comportamento personalizado. Um caso desse tipo é mostrado no tópico [Como Implementar Eventos de Interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como implementar os acessadores de eventos personalizados adicionar e remover. Embora seja possível substituir qualquer código dentro dos acessadores, é recomendável que você bloqueie o evento antes de adicionar ou remover um novo método de manipulador de eventos.  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)

