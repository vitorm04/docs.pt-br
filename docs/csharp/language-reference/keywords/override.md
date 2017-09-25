---
title: "override (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- override
- override_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 26
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
ms.openlocfilehash: 0f5a87eaa5894b61187c379c92ad785336aa79b2
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="override-c-reference"></a>override (Referência de C#)
O modificador `override` é necessário para estender ou modificar a implementação abstrata ou virtual de um método, propriedade, indexador ou evento herdado.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, a classe `Square` deve fornecer uma implementação substituída de `Area` porque `Area` é herdado do `ShapesClass` abstrato:  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 Um método `override` fornece uma nova implementação de um membro herdado de uma classe base. O método que é substituído por uma declaração `override` é conhecido como o método base substituído. O método base substituído deve ter a mesma assinatura que o método `override`. Para obter informações sobre herança, consulte [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Você não pode substituir um método não virtual ou estático. O método base substituído deve ser `virtual`, `abstract` ou `override`.  
  
 Uma declaração `override` não pode alterar a acessibilidade do método `virtual`. O método `override` e o método `virtual` devem ter o mesmo [modificador de nível de acesso](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Não é possível usar os modificadores `new`, `static` ou `virtual` para modificar um método `override`.  
  
 Uma declaração de propriedade de substituição deve especificar exatamente o mesmo modificador de acesso, tipo e nome que a propriedade herdada e a propriedade substituída deve ser `virtual`, `abstract` ou `override`.  
  
 Para obter mais informações sobre como usar a palavra-chave `override`, consulte [Controle de versão com as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo define uma classe base chamada `Employee` e uma classe derivada chamada `SalesEmployee`. A classe `SalesEmployee` inclui uma propriedade extra, `salesbonus` e substitui o método `CalculatePay` para levar isso em consideração.  
  
 [!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Herança](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [Polimorfismo](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)

