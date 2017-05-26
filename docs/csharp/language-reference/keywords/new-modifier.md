---
title: "Modificador new (Referência de C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
caps.latest.revision: 28
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3c636d50e6c871c529104d5f2985e861f9a652b2
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="new-modifier-c-reference"></a>Modificador new (Referência de C#)
Quando usada como um modificador de declaração, a palavra-chave `new` oculta explicitamente um membro herdado de uma classe base. Quando você oculta um membro herdado, a versão derivada do membro substitui a versão da classe base. Embora possa ocultar membros sem usar o modificador `new`, você obtém um aviso do compilador. Se você usar `new` para ocultar explicitamente um membro, ele suprime o aviso.  
  
 Para ocultar um membro herdado, declare-o na classe derivada usando o mesmo nome de membro e modifique-o com a palavra-chave `new`. Por exemplo:  
  
 [!code-cs[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 Neste exemplo, `BaseC.Invoke` é ocultado por `DerivedC.Invoke`. O campo `x` não é afetado porque não é ocultado por um nome semelhante.  
  
 A ocultação de nome por meio da herança assume uma das seguintes formas:  
  
-   Normalmente, uma constante, campo, propriedade ou tipo que é apresentado em uma classe ou struct oculta todos os membros da classe base que compartilham seu nome.  Há casos especiais.  Por exemplo, se você declarar que um novo campo com o nome `N` tem um tipo que não pode ser invocado e um tipo base declarar que `N` é um método, o novo campo não ocultará a declaração base na sintaxe de invocação.  Consulte a [Especificação da linguagem C#](http://go.microsoft.com/fwlink/?LinkId=199552) para obter detalhes (consulte a seção "Pesquisa de membro" na seção "Expressões").  
  
-   Um método introduzido em uma classe ou struct oculta propriedades, campos e tipos que compartilham esse nome na classe base. Ele também oculta todos os métodos da classe base que têm a mesma assinatura.  
  
-   Um indexador introduzido em uma classe ou struct oculta todos os indexadores de classe base que têm a mesma assinatura.  
  
 É um erro usar `new` e [override](../../../csharp/language-reference/keywords/override.md) no mesmo membro, porque os dois modificadores têm significados mutuamente exclusivos. O modificador `new` cria um novo membro com o mesmo nome e faz com que o membro original seja ocultado. O modificador `override` estende a implementação de um membro herdado.  
  
 Usar o modificador `new` em uma declaração que não oculta um membro herdado gera um aviso.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, uma classe base, `BaseC` e uma classe derivada, `DerivedC`, usam o mesmo nome do campo `x`, que oculta o valor do campo herdado. O exemplo demonstra o uso do modificador `new`. Ele também demonstra como acessar os membros ocultos da classe base usando seus nomes totalmente qualificados.  
  
 [!code-cs[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, uma classe aninhada oculta uma classe que tem o mesmo nome na classe base. O exemplo demonstra como usar o modificador `new` para eliminar a mensagem de aviso e como acessar os membros da classe oculta usando seus nomes totalmente qualificados.  
  
 [!code-cs[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 Se você remover o modificador `new`, o programa ainda será compilado e executado, mas você receberá o seguinte aviso:  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Palavras-chave de C#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [Controle de versão com as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [Quando usar as palavras-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
