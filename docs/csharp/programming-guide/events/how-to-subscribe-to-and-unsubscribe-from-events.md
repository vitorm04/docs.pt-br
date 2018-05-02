---
title: Como realizar e cancelar a assinatura de eventos (Guia de Programação em C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ecb65a2156f83d9da722329ff6159bb08e464eaa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Como realizar e cancelar a assinatura de eventos (Guia de Programação em C#)
Você assina um evento publicado por outra classe quando quer escrever um código personalizado que é chamado quando esse evento é gerado. Por exemplo, você pode assinar o evento `click` de um botão para fazer com que seu aplicativo faça algo útil quando o usuário clicar no botão.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Para assinar eventos usando o IDE do Visual Studio  
  
1.  Se você não vir a janela **Propriedades**, no modo de exibição de **Design**, clique com o botão direito do mouse no formulário ou controle para o qual deseja criar um manipulador de eventos e selecione **Propriedades**.  
  
2.  Na parte superior da janela **Propriedades**, clique no ícone **Eventos**.  
  
3.  Clique duas vezes no evento que deseja criar, por exemplo, o evento `Load`.  
  
     O Visual C# cria um método de manipulador de eventos vazio e adiciona-o ao código. Como alternativa, você pode adicionar o código manualmente no modo de exibição **Código**. Por exemplo, as linhas de código a seguir declaram um método de manipulador de eventos que será chamado quando a classe `Form` gerar o evento `Load`.  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     A linha de código que é necessária para assinar o evento também é gerada automaticamente no método `InitializeComponent` no arquivo Form1.Designer.cs em seu projeto. Ele é semelhante a isto:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Para assinar eventos de forma programática  
  
1.  Defina um método de manipulador de eventos cuja assinatura corresponda à assinatura do delegado do evento. Por exemplo, se o evento se basear no tipo de delegado <xref:System.EventHandler>, o código a seguir representará o stub do método:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Use o operador de atribuição de adição (`+=`) para anexar seu manipulador de eventos ao evento. No exemplo a seguir, suponha que um objeto chamado `publisher` tem um evento chamado `RaiseCustomEvent`. Observe que a classe do assinante precisa de uma referência à classe do editor para assinar seus eventos.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Observe que a sintaxe anterior é nova no C# 2.0. Ela é exatamente equivalente à sintaxe C# 1.0, em que o delegado de encapsulamento deve ser criado explicitamente usando a palavra-chave `new`:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Um manipulador de eventos também pode ser adicionado usando uma expressão lambda:  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Para obter mais informações, consulte [Como usar expressões lambda fora do LINQ (C#)](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Para assinar eventos usando um método anônimo  
  
-   Se não precisar cancelar a assinatura de um evento posteriormente, você pode usar o operador de atribuição de adição (`+=`) para anexar um método anônimo ao evento. No exemplo a seguir, suponha que um objeto chamado `publisher` tenha um evento chamado `RaiseCustomEvent` e que uma classe `CustomEventArgs` também tenha sido definida para conter algum tipo de informação de evento específico. Observe que a classe do assinante precisa de uma referência a `publisher` para assinar seus eventos.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     É importante observar que você não pode, com facilidade, cancelar a assinatura de um evento se tiver usado uma função anônima para assiná-lo. Para cancelar a assinatura nesse cenário, é necessário voltar ao código em que você assinou o evento, armazenar o método anônimo em uma variável do delegado e, então, adicionar o delegado ao evento. De modo geral, é recomendável que você não use funções anônimas para assinar eventos se precisar cancelar a assinatura do evento posteriormente no código. Para obter mais informações sobre funções anônimas, consulte [Funções anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Cancelando a assinatura  
 Para impedir que o manipulador de eventos seja invocado quando o evento for gerado, cancele a assinatura do evento. Para evitar perda de recursos, cancele a assinatura de eventos antes de descartar um objeto de assinante. Até que você cancele a assinatura de um evento, o delegado multicast subjacente ao evento no objeto de publicação terá uma referência ao delegado que encapsula o manipulador de eventos do assinante. Desde que o objeto de publicação contenha essa referência, a coleta de lixo não excluirá seu objeto de assinante.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Para cancelar a assinatura de um evento  
  
-   Use o operador de atribuição de subtração (`-=`) para cancelar a assinatura de um evento:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Quando todos os assinantes tiverem cancelado a assinatura de um evento, a instância do evento na classe do publicador será definida como `null`.  
  
## <a name="see-also"></a>Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)  
 [event](../../../csharp/language-reference/keywords/event.md)  
 [Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [Operador -= (referência do C#)](../../language-reference/operators/subtraction-assignment-operator.md)  
 [Operador +=](../../../csharp/language-reference/operators/addition-assignment-operator.md)