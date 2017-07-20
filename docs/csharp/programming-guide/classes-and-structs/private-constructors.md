---
title: "Construtores particulares (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: 19
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: e2ac39bc642cf5379d4a8e8f9c74068b93b0b5b4
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="private-constructors-c-programming-guide"></a>Construtores particulares (Guia de Programação em C#)
Um construtor particular é um construtor de instância especial. Normalmente, ele é usado em classes que contêm apenas membros estáticos. Se uma classe tiver um ou mais construtores particulares e nenhum construtor público, outras classes (exceto as classes aninhadas) não poderão criar instâncias dessa classe. Por exemplo:  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 A declaração do construtor vazio impede a geração automática de um construtor padrão. Observe que, se você não usar um modificador de acesso com o construtor, ele ainda será privado por padrão. No entanto, o modificador [private](../../../csharp/language-reference/keywords/private.md) geralmente é usado explicitamente para deixar claro que a classe não pode ser instanciada.  
  
 Construtores particulares são usados para impedir a criação de instâncias de uma classe quando não há métodos ou campos de instância, como a classe <xref:System.Math> ou quando um método é chamado para obter uma instância de uma classe. Se todos os métodos na classe forem estáticos, considere deixar toda a classe estática. Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Exemplo  
 A seguir, temos um exemplo de uma classe usando um construtor particular.  
  
 [!code-cs[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 Observe que se você remover a marca de comentário da seguinte instrução do exemplo, ela gerará um erro porque o construtor está inacessível devido a seu nível de proteção:  
  
 [!code-cs[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)
