---
title: "Propriedades autoimplementadas (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: 23
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 92e0037b73f1054673ea8060b71af5bd4db13ca3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="auto-implemented-properties-c-programming-guide"></a>Propriedades autoimplementadas (Guia de Programação em C#)
No C# 3.0 e versões posteriores, as propriedades autoimplementadas tornam a declaração de propriedade mais concisa quando nenhuma lógica adicional for necessária nos acessadores de propriedade. Elas também habilitam o código do cliente a criar objetos. Ao declarar uma propriedade, como mostrado no exemplo a seguir, o compilador cria um campo de suporte privado e anônimo que pode ser acessado somente por meio dos acessadores `get` e `set` da propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma classe simples que tem algumas propriedades autoimplementadas:  
  
 [!code-cs[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 No C# 6 e versões posteriores, é possível inicializar as propriedades autoimplementadas da mesma forma que os campos:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 A classe mostrada no exemplo anterior é mutável. O código cliente pode alterar os valores nos objetos após sua criação. Em classes complexas que contêm comportamento significativo (métodos), bem como dados, geralmente é necessário ter propriedades públicas. No entanto, para classes pequenas ou structs que apenas encapsulam um conjunto de valores (dados) e têm poucos ou nenhum comportamento, faça com que os objetos se tornem imutáveis declarando o acessador set como [privado](../../../csharp/language-reference/keywords/private.md) (imutável para consumidores) ou declarando somente um acessador get (imutável em todos os lugares, exceto no construtor).  Para obter mais informações, consulte [Como Implementar uma Classe Leve com Propriedades Autoimplementadas](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).  
  
 Os atributos são permitidos em propriedades autoimplementadas, mas, obviamente, não são permitidos nos campos de suporte, pois eles não são acessíveis por meio do código-fonte. Se for necessário utilizar um atributo no campo de suporte de uma propriedade, basta criar uma propriedade regular.  
  
## <a name="see-also"></a>Consulte também  
 [Propriedades](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)

