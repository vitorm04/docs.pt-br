---
title: "Eventos (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6a913a615de8185bb358376def1e2a051bdaa951
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="events-c-programming-guide"></a>Eventos (Guia de Programação em C#)
Eventos permitem que uma [classe](../../../csharp/language-reference/keywords/class.md) ou objeto notifique outras classes ou objetos quando algo interessante ocorre. A classe que envia (ou *aciona*) o evento é chamada de *editor* e as classes que recebem (ou *manipulam*) os eventos são chamadas *assinantes*.  
  
 Em um aplicativo Windows Forms em C# ou Web típico, você assina eventos acionados pelos controles, como botões e caixas de listagem. Você pode usar o IDE [!INCLUDE[csprcs](~/includes/csprcs-md.md)] (ambiente de desenvolvimento integrado) para procurar os eventos que um controle publica e selecionar aqueles que você deseja manipular. O IDE adiciona automaticamente um método de manipulador de eventos vazio e o código para assinar o evento. Para obter mais informações, consulte [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="events-overview"></a>Visão geral sobre eventos  
 Os eventos têm as seguintes propriedades:  
  
-   O editor determina quando um evento é acionado. Os assinantes determinam a ação que é executada em resposta ao evento.  
  
-   Um evento pode ter vários assinantes. Um assinante pode manipular vários eventos de vários publicadores.  
  
-   Eventos que não têm assinantes nunca são acionados.  
  
-   Normalmente, os eventos são usados para sinalizar ações do usuário, como cliques de botão ou seleções de menu em interfaces gráficas do usuário.  
  
-   Quando um evento tem vários assinantes, os manipuladores de eventos são invocados sincronicamente quando um evento é acionado. Para invocar eventos de forma assíncrona, consulte [Chamando métodos síncronos assincronamente](https://msdn.microsoft.com/library/2e08f6yc).  
  
-   Na biblioteca de classes do [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], os eventos são baseados no delegado <xref:System.EventHandler> e na classe base <xref:System.EventArgs>.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para obter mais informações, consulte:  
  
-   [Como realizar e cancelar a assinatura de eventos](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Como acionar eventos de classe base em classes derivadas](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Como implementar eventos de interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Sincronização de Thread ](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [Como usar um dicionário para armazenar instâncias de eventos](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Como implementar acessadores de eventos personalizados](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>Capítulos do Livro em Destaque  
 [Expressões lambda, eventos e delegados](http://go.microsoft.com/fwlink/?LinkId=195395) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Delegados e eventos](http://go.microsoft.com/fwlink/?LinkId=195418) em [Learning C# 3.0: Master the fundamentals of C# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.EventHandler>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Criando manipuladores de eventos no Windows Forms](https://msdn.microsoft.com/library/dacysss4.aspx)   
 [Programação multi-threaded com o padrão assíncrono baseado em evento](https://msdn.microsoft.com/library/hkasytyf)

