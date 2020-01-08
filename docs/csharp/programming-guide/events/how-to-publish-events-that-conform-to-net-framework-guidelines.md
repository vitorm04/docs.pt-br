---
title: Como publicar eventos que estão em conformidade com as diretrizes C# de .NET Framework-guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: fe8334d4a6aadc8e2d1f1f5d60c96d4e8689b67f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346330"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Como publicar eventos que estão em conformidade com as diretrizesC# de .NET Framework (guia de programação)
O procedimento a seguir demonstra como adicionar eventos que seguem o padrão do .NET Framework para classes e structs. Todos os eventos na biblioteca de classes do .NET Framework se baseiam no delegado <xref:System.EventHandler>, que é definido da seguinte maneira:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> O .NET Framework 2.0 apresenta uma versão genérica desse delegado, o <xref:System.EventHandler%601>. Os exemplos a seguir mostram como usar as duas versões.  
  
 Embora os eventos nas classes que você define possam ser baseados em qualquer tipo delegado válido, até mesmo nos delegados que retornam um valor, é geralmente recomendável que você baseie seus eventos no padrão do .NET Framework usando o <xref:System.EventHandler>, conforme mostrado no exemplo a seguir.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Para publicar eventos com base no padrão EventHandler  
  
1. (Pule esta etapa e vá para a etapa 3a se você não precisar enviar dados personalizados com seu evento.) Declare a classe para seus dados personalizados em um escopo que seja visível para as classes de Publicador e de assinante. Em seguida, adicione os membros necessários para manter seus dados de evento personalizados. Neste exemplo, uma cadeia de caracteres simples é retornada.  
  
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
  
2. (Ignore esta etapa se você estiver usando a versão genérica do <xref:System.EventHandler%601>.) Declare um delegado em sua classe de publicação. Dê a ela um nome que termina com *EventHandler*. O segundo parâmetro especifica o tipo personalizado de EventArgs.  
  
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
  
## <a name="see-also"></a>Veja também

- <xref:System.Delegate>
- [Guia de Programação em C#](../index.md)
- [Eventos](./index.md)
- [Delegados](../delegates/index.md)
