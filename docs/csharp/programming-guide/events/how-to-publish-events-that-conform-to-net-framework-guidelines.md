---
title: Como publicar eventos que estejam em conformidade com as Diretrizes-Quadro .NET - Guia de Programação C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167514"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Como publicar eventos que estejam em conformidade com as Diretrizes-Quadro .NET (Guia de Programação C#)
O procedimento a seguir demonstra como adicionar eventos que seguem o padrão do .NET Framework para classes e structs. Todos os eventos na biblioteca de classes do .NET Framework se baseiam no delegado <xref:System.EventHandler>, que é definido da seguinte maneira:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> O .NET Framework 2.0 apresenta uma versão genérica desse delegado, o <xref:System.EventHandler%601>. Os exemplos a seguir mostram como usar as duas versões.  
  
 Embora os eventos nas classes que você define possam ser baseados em qualquer tipo delegado válido, até mesmo nos delegados que retornam um valor, é geralmente recomendável que você baseie seus eventos no padrão do .NET Framework usando o <xref:System.EventHandler>, conforme mostrado no exemplo a seguir.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Para publicar eventos com base no padrão EventHandler  
  
1. (Pule esta etapa e vá para a Etapa 3a se você não tiver que enviar dados personalizados com o seu evento.) Declare a classe para seus dados personalizados em um escopo visível para suas classes de editores e assinantes. Em seguida, adicione os membros necessários para manter seus dados de evento personalizados. Neste exemplo, uma cadeia de caracteres simples é retornada.  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }
    }  
    ```  
  
2. (Pule esta etapa se estiver <xref:System.EventHandler%601> usando a versão genérica de .) Declare um delegado em sua aula de publicação. Dê a ela um nome que termina com *EventHandler*. O segundo parâmetro especifica o tipo personalizado de EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Declare o evento em sua classe de publicação, usando uma das etapas a seguir.  
  
    1. Se você não tiver uma classe EventArgs personalizada, o tipo de evento será o delegado EventHandler não genérico. Você não precisa declarar o delegado porque ele já está declarado no namespace <xref:System> que está incluído quando você cria seu projeto do C#. Adicione o seguinte código à sua classe publicadora.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Se você estiver usando a versão não genérica de <xref:System.EventHandler> e você tem uma classe personalizada derivada de <xref:System.EventArgs>, declare o evento dentro de sua classe de publicação e use o delegado da etapa 2 como o tipo.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Se você estiver usando a versão genérica, não é necessário um delegado personalizado. Em vez disso, na sua classe de publicação, especifique o tipo de evento como `EventHandler<CustomEventArgs>`, substituindo o nome da sua própria classe entre os colchetes angulares.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra as etapas anteriores, usando uma classe EventArgs personalizada e o <xref:System.EventHandler%601> como o tipo de evento.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Delegate>
- [C# Guia de Programação](../index.md)
- [Eventos](./index.md)
- [Delega](../delegates/index.md)
