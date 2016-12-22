---
title: "Como implementar eventos de interface (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
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
  - "eventos [C#], em interfaces"
  - "interfaces [C#], implementação de eventos em classes"
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como implementar eventos de interface (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um  [interface](../../../csharp/language-reference/keywords/interface.md) pode declarar um  [evento](../../../csharp/language-reference/keywords/event.md).  O exemplo a seguir mostra como implementar eventos de interface em uma classe.  Basicamente as regras são as mesmas ao implementar qualquer propriedade ou método de interface.  
  
### Para implementar eventos de interface em uma classe  
  
-   Declare o evento na sua classe e, em seguida, chamá\-la nas áreas apropriadas.  
  
    ```  
    namespace ImplementInterfaceEvents  
    {  
        public interface IDrawingObject  
        {  
            event EventHandler ShapeChanged;  
        }  
        public class MyEventArgs : EventArgs   
        {  
            // class members  
        }  
        public class Shape : IDrawingObject  
        {  
            public event EventHandler ShapeChanged;  
            void ChangeShape()  
            {  
                // Do something here before the event…  
  
                OnShapeChanged(new MyEventArgs(/*arguments*/));  
  
                // or do something here after the event.   
            }  
            protected virtual void OnShapeChanged(MyEventArgs e)  
            {  
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## Exemplo  
 O exemplo a seguir mostra como tratar da situação menos comuns em que sua classe herda de duas ou mais interfaces e cada interface tem um evento com o mesmo nome.  Nessa situação, você deve fornecer uma implementação de interface explícita para pelo menos um dos eventos.  Quando você escreve uma implementação de interface explícita para um evento, você também deve escrever o `add` e `remove` acessadores de evento.  Normalmente, eles são fornecidos pelo compilador, mas nesse caso o compilador não pode fornecer\-lhes.  
  
 Ao fornecer seus próprios acessadores, você pode especificar se os dois eventos são representados pelo mesmo evento na sua classe, ou por eventos diferentes.  Por exemplo, se os eventos devem ser gerados em horas diferentes, de acordo com as especificações de interface, você pode associar cada evento de uma implementação separada na sua classe.  No exemplo a seguir, os assinantes determinam qual `OnDraw` evento receberão por projeção a referência de forma a qualquer um `IShape` ou um `IDrawingObject`.  
  
 [!CODE [csProgGuideEvents#10](../CodeSnippet/VS_Snippets_VBCSharp/csProgGuideEvents#10)]  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Eventos](../../../csharp/programming-guide/events/index.md)   
 [Delegados](../../../csharp/programming-guide/delegates/index.md)   
 [Implementação de interface explícita](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)   
 [Como acionar eventos de classe base em classes derivadas](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)