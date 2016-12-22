---
title: "Modificador new (Refer&#234;ncia de C#) | Microsoft Docs"
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
  - "palavra-chave de modificador new [C#]"
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
caps.latest.revision: 28
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Modificador new (Refer&#234;ncia de C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Quando usado como um modificador de declaração, o `new` palavra\-chave oculta explicitamente um membro que é herdado de uma classe base.  Quando você oculta um membro herdado, a versão derivada do membro substitui a versão da classe base.  Embora você possa ocultar membros sem usar o `new` modificador, você obtém um aviso do compilador.  Se você usar `new` para ocultar explicitamente um membro, suprime o aviso.  
  
 Para ocultar um membro herdado, declare\-o na classe derivada usando o mesmo nome de membro e modificá\-lo com o `new` palavra\-chave.  Por exemplo:  
  
 [!code-cs[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 Neste exemplo, `BaseC.Invoke` oculto por `DerivedC.Invoke`.  O campo `x` não é afetado porque ele não está oculto por um nome semelhante.  
  
 Ocultação por meio da herança de nome escolhe uma das seguintes formas:  
  
-   Em geral, uma constante, campo, propriedade ou tipo que é apresentado em uma classe ou estrutura oculta todos os membros da classe base que compartilham seu nome.  Há casos especiais.  Por exemplo, se você declarar um novo campo com nome `N` têm um tipo que não seja invocá\-lo e um tipo base declara `N` para ser um método, o novo campo não oculta a declaração base na sintaxe de chamada.  Consulte o [especificação da linguagem c\#](http://go.microsoft.com/fwlink/?LinkId=199552) para obter detalhes \(consulte a seção "Pesquisa de membro" na seção "Expressions"\).  
  
-   Um método introduzido em uma classe ou struct oculta propriedades, campos e tipos que compartilham esse nome na classe base.  Ele também oculta todos os métodos da classe base que têm a mesma assinatura.  
  
-   Um indexador introduzido em uma classe ou struct oculta todos os indexadores de classe base que têm a mesma assinatura.  
  
 É um erro usar ambos `new` e [substituir](../../../csharp/language-reference/keywords/override.md) no mesmo membro, porque os dois modificadores têm significados mutuamente exclusivos.  O `new` modificador cria um novo membro com o mesmo nome e faz com que o membro original ficam ocultas.  O `override` modificador estende a implementação de um membro herdado.  
  
 Usando o `new` modificador em uma declaração que não oculta um membro herdado gera um aviso.  
  
## Exemplo  
 Neste exemplo, uma classe base, `BaseC`, e uma classe derivada, `DerivedC`, use o mesmo nome do campo `x`, que oculta o valor do campo herdado.  O exemplo demonstra o uso do `new` modificador.  Ele também demonstra como acessar os membros ocultos da classe base usando seus nomes totalmente qualificados.  
  
 [!code-cs[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## Exemplo  
 Neste exemplo, uma classe aninhada oculta uma classe que tem o mesmo nome na classe base.  O exemplo demonstra como usar o `new` modificador para eliminar a mensagem de aviso e como acessar os membros de classe oculta usando seus nomes totalmente qualificados.  
  
 [!code-cs[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 Se você remover o `new` modificador, o programa ainda será compilado e executado, mas você receberá o seguinte aviso:  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [Palavras\-chave C\#](../../../csharp/language-reference/keywords/index.md)   
 [Palavras\-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)   
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)   
 [Controle de versão com as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [Quando usar as palavras\-chave override e new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)