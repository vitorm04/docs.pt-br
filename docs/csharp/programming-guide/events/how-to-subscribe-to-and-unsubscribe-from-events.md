---
title: "Como realizar e cancelar a assinatura de eventos (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "Editor de Código, manipuladores de eventos"
  - "manipuladores de eventos [C#], criando"
  - "eventos [C#], criando usando o IDE"
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como realizar e cancelar a assinatura de eventos (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você se inscreve a um evento publicado por outra classe quando deseja escrever código personalizado que é invocado quando o evento acontece.  Por exemplo, você pode assinar um botão `click` evento para tornar seu aplicativo faça algo útil quando o usuário clica no botão.  
  
### Para se inscrever em eventos usando o IDE de Visual Studio  
  
1.  Se você não conseguir ver o  **Propriedades** janela, na  **Design** exibir, clique com o botão direito do formulário ou controle para o qual você deseja criar um manipulador de eventos e, em seguida, selecione  **Propriedades**.  
  
2.  Em relação a  **Propriedades** janela, clique no  **eventos** ícone.  
  
3.  Clique duas vezes no evento que você deseja criar, por exemplo o `Load` evento.  
  
     [!INCLUDE[csprcs](../../../csharp/includes/csprcs_md.md)]cria um método do manipulador de evento vazio e o adiciona ao seu código.  Como alternativa, você pode adicionar o código manualmente no  **código** modo de exibição.  Por exemplo, linhas de código a seguir declaram um método de manipulador de eventos que será chamado quando o `Form` classe gera o `Load` evento.  
  
     [!CODE [csProgGuideEvents#11](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEvents#11)]  
  
     A linha de código que é necessário para assinar o evento é gerada automaticamente na `InitializeComponent` método no arquivo Form1 no seu projeto.  Se parece com isto:  
  
    ```  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### Para inscrever\-se através de programação eventos  
  
1.  Defina um método de manipulação de evento cuja assinatura esteja de acordo com a assinatura do delegate para o evento.  Por exemplo, se o evento se baseia o <xref:System.EventHandler> tipo de delegado, o código a seguir representa o stub do método:  
  
    ```  
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Use o operador de atribuição de adição \(`+=`\) para anexar o seu manipulador de eventos ao evento.  O exemplo a seguir, vamos supor que um objeto chamado `publisher` tem um evento chamado `RaiseCustomEvent`.  Observe que a classe subscriber necessita de uma referência à classe publisher para se inscrever aos seus eventos.  
  
    ```  
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Observe que a sintaze anterior é nova no C\# 2.0.  É exatamente equivalente a sintaxe C\# 1.0 em que o delegado encapsular deve ser explicitamente criado usando o `new` palavra\-chave:  
  
    ```  
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Um manipulador de eventos também pode ser adicionado através do uso de uma expressão lambda:  
  
    ```  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Para obter mais informações, consulte [Como usar expressões lambda fora do LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### Para se inscrever em eventos usando um método anônimo  
  
-   Se você não precisará cancelar a inscrição para um evento posteriormente, você pode usar o operador de atribuição de adição \(`+=`\) para anexar um método anônimo para o evento.  O exemplo a seguir, vamos supor que um objeto chamado `publisher` tem um evento chamado `RaiseCustomEvent` e que uma `CustomEventArgs` classe também foi definida para executar algum tipo de informações sobre o evento especializado.  Observe que a classe do assinante precisa de uma referência a `publisher` para se inscrever para seus eventos.  
  
    ```  
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     É importante observar que você não pode facilmente cancelar a inscrição a um evento se você utilizou uma função anônima para se inscrever.  Para cancelar a inscrição neste cenário, é necessário voltar ao código onde você se inscreveu ao evento, armazenar o método anônimo numa variável delegate, e então adicionar o delegate ao evento.  Em geral, recomendamos que você não use funções anônimas para se inscrever aos eventos se você tiver que cancelar a inscrição ao evento mais tarde no seu código.  Para obter mais informações sobre funções anônimas, consulte [Funções anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## Cancelamento de inscrição  
 Para evitar que o manipulador de evento seja invocado quando o evento ocorre, cancele a inscrição ao evento.  Para evitar vazamento de recursos, você deve cancelar a inscrição a eventos antes que você libere de um objeto assinante.  Até que você cancele a inscrição a um evento, o delegate multicast que suporta o evento no objeto publicador tem uma referência ao delegate que encapsula o manipulador do evento no assinante.  Enquanto o objeto publicador tiver aquela referência, a coleção de lixo \(garbage collection\) não irá excluir o objeto assinante.  
  
#### A inscrição de um evento  
  
-   Use o operador de atribuição de subtração \(`-=`\) a inscrição de um evento:  
  
    ```  
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Quando todos os assinantes têm não inscrito em um evento, a instância do evento na classe publisher estiver definida como `null`.  
  
## Consulte também  
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)   
 [Como publicar eventos em conformidade com as diretrizes do .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)   
 [Operador \-\=](../../../csharp/language-reference/operators/subtraction-assignment-operator-1.md)   
 [Operador \+\=](../../../csharp/language-reference/operators/addition-assignment-operator.md)