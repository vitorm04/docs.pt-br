---
title: "Como publicar eventos em conformidade com as diretrizes do .NET Framework (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "eventos [C#], diretrizes de implementação"
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como publicar eventos em conformidade com as diretrizes do .NET Framework (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O procedimento a seguir demonstra como adicionar eventos que seguem o padrão [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] padrão a seu classes e estruturas.  Todos os eventos do [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] class library baseiam\-se na <xref:System.EventHandler> delegar, que é definido da seguinte maneira:  
  
```  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  O [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] apresenta uma versão genérica deste delegado, <xref:System.EventHandler%601>.  Os exemplos a seguir mostram como usar as duas versões.  
  
 Embora as classes que você define os eventos podem ser baseados em qualquer tipo de delegado válido, delegados, mesmo que retornam um valor, geralmente é recomendado que você basear seus eventos na [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] padrão usando <xref:System.EventHandler>, conforme mostrado no exemplo a seguir.  
  
### Para publicar os eventos com base no padrão EventHandler  
  
1.  \(Pule esta etapa e vá para a etapa 3a, se você não precisa enviar dados personalizados com o seu evento\). Declare a classe de dados personalizados em um escopo que é visível para as classes de seu editor e o assinante.  Em seguida, adicione membros necessários para manter seus dados de evento personalizado.  Neste exemplo, uma simple seqüência de caracteres é retornada.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
2.  \(Pule esta etapa, se você estiver usando a versão genérica do <xref:System.EventHandler%601> .\) Declare um delegado na sua classe de publicação.  Atribua um nome que termina com  *EventHandler*.  O segundo parâmetro especifica o tipo EventArgs personalizado.  
  
    ```  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Declare o evento na sua classe de publicação usando uma das etapas a seguir.  
  
    1.  Se você não tiver nenhuma classe EventArgs personalizada, seu tipo de evento será delegado EventHandler não genérico.  Você não precisa declarar o delegado porque ele já está declarado na <xref:System> espaço para nome que é incluído quando você criar o projeto C\#.  Adicione o seguinte código à sua classe do publisher.  
  
        ```  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Se você estiver usando a versão não genérica do <xref:System.EventHandler> e você tem uma classe personalizada derivada de <xref:System.EventArgs>, declarar seu evento dentro de sua classe de publicação e usar o seu representante da etapa 2 como o tipo.  
  
        ```  
        public event CustomEventHandler RaiseCustomEvent;  
  
        ```  
  
    3.  Se você estiver usando a versão genérica, não é necessário um delegado personalizado.  Em vez disso, na sua classe de publicação, você especifica o tipo de evento como `EventHandler<CustomEventArgs>`, substituindo o nome de sua própria classe entre os colchetes angulares.  
  
        ```  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## Exemplo  
 O exemplo a seguir demonstra as etapas anteriores, usando uma classe EventArgs personalizada e <xref:System.EventHandler%601> como o tipo de evento.  
  
 [!CODE [csProgGuideEvents#2](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEvents#2)]  
  
## Consulte também  
 <xref:System.Delegate>   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)