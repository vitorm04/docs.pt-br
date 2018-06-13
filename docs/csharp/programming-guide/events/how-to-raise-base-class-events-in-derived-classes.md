---
title: Como acionar eventos de classe base em classes derivadas (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: e064c318f16c2fe87aa980b7dec7468b1e61ab25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320086"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Como acionar eventos de classe base em classes derivadas (Guia de Programação em C#)
O exemplo simples a seguir mostra o modo padrão para declarar os eventos em uma classe base para que eles também possam ser gerados das classes derivadas. Esse padrão é amplamente usado em classes do Windows Forms em uma biblioteca de classes de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Quando você cria uma classe que pode ser usada como uma classe base para outras classes, deve considerar o fato de que os eventos são um tipo especial de delegado que pode ser invocado apenas de dentro da classe que os declarou. As classes derivadas não podem invocar diretamente eventos declarados dentro da classe base. Embora, às vezes, você possa desejar um evento que possa ser gerado apenas pela classe base, na maioria das vezes você deve habilitar a classe derivada para invocar os eventos de classe base. Para fazer isso, você pode criar um método de invocação protegido na classe base que encapsula o evento. Chamando ou substituindo esse método de invocação, as classes derivadas podem invocar o evento diretamente.  
  
> [!NOTE]
>  Não declare eventos virtuais em uma classe base e substitua-os em uma classe derivada. O compilador C# não lida com eles corretamente e é imprevisível se um assinante do evento derivado realmente estará assinando o evento de classe base.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Eventos](../../../csharp/programming-guide/events/index.md)  
 [Delegados](../../../csharp/programming-guide/delegates/index.md)  
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Criando manipuladores de eventos no Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
