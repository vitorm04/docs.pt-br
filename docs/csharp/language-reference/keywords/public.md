---
title: "public (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords: public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 197ef4a2a8544d439b0c34ec14bb7752b760ea06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="public-c-reference"></a>public (Referência de C#)
A palavra-chave `public` é um modificador de acesso para tipos e membros de tipo. Acesso público é o nível de acesso mais permissivo. Não há nenhuma restrição quanto ao acesso a membros públicos, como neste exemplo:  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Consulte [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) e [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) para obter mais informações.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, duas classes são declaradas, `PointTest` e `MainClass`. Os membros públicos `x` e `y` de `PointTest` são acessados diretamente de `MainClass`.  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Se alterar o nível de acesso de `public` para [particular](../../../csharp/language-reference/keywords/private.md) ou [protegido](../../../csharp/language-reference/keywords/protected.md), você receberá a mensagem de erro:  
  
 'PointTest.y' é inacessível devido ao seu nível de proteção.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
