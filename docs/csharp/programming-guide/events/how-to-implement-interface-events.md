---
title: "Como implementar eventos de interface (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 944b894e7e5f305d35d4db96d7426bf05322ca54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Como implementar eventos de interface (Guia de Programação em C#)
Um [interface](../../../csharp/language-reference/keywords/interface.md) pode declarar uma [evento](../../../csharp/language-reference/keywords/event.md). O exemplo a seguir mostra como implementar eventos de interface em uma classe. Basicamente, as regras são as mesmas aplicadas à implementação de qualquer método ou propriedade de interface.  
  
### <a name="to-implement-interface-events-in-a-class"></a>Implementar eventos de interface em uma classe  
  
-   Declare o evento na classe e, em seguida, invoque-o nas áreas apropriadas.  
  
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
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como lidar com a situação menos comum, na qual a classe herda de duas ou mais interfaces e cada interface tem um evento com o mesmo nome. Nessa situação, é necessário fornecer uma implementação explícita da interface para pelo menos um dos eventos. Ao gravar uma implementação explícita da interface de um evento, também é necessário gravar os acessadores de evento `add` e `remove`. Normalmente, eles são fornecidos pelo compilador, mas nesse caso o compilador não pode fornecê-los.  
  
 Ao fornecer acessadores próprios, é possível especificar se os dois eventos são representados pelo mesmo evento na classe ou por eventos diferentes. Por exemplo, se os eventos forem gerados em horários diferentes, de acordo com as especificações da interface, será possível associar cada evento a uma implementação separada na classe. No exemplo a seguir, os assinantes determinam qual evento `OnDraw` receberão ao converter a referência de forma para um `IShape` ou um `IDrawingObject`.  
  
 [!code-csharp[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Eventos](../../../csharp/programming-guide/events/index.md)  
 [Delegados](../../../csharp/programming-guide/delegates/index.md)  
 [Implementação de interface explícita](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 [Como acionar eventos de classe base em classes derivadas](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
