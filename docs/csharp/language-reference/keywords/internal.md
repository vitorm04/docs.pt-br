---
title: internal – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: 8d787f8deb8f3b7d1e59d99e71662960a5c04e15
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652079"
---
# <a name="internal-c-reference"></a>internal (Referência de C#)
A palavra-chave `internal` é um [modificador de acesso](../../../csharp/language-reference/keywords/access-modifiers.md) para tipos e membros de tipo. 
  
 > Esta página aborda o acesso `internal`. A palavra-chave `internal` também faz parte do modificador de acesso [`protected internal`](./protected-internal.md).
  
Tipos ou membros internos são acessíveis somente em arquivos no mesmo assembly, como neste exemplo:  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 Para obter uma comparação de `internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) e [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Para obter mais informações sobre assemblies, consulte [Assemblies e o cache de assembly global](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).  
  
 Um uso comum do acesso interno é no desenvolvimento baseado em componente, porque ele permite que um grupo de componentes colabore de maneira particular, sem serem expostos para o restante do código do aplicativo. Por exemplo, uma estrutura para a criação de interfaces gráficas do usuário pode fornecer as classes `Control` e `Form`, que cooperam através do uso de membros com acesso interno. Uma vez que esses membros são internos, eles não são expostos ao código que está usando a estrutura.  
  
 É um erro fazer referência a um tipo ou um membro com acesso interno fora do assembly no qual ele foi definido.  
  
## <a name="example"></a>Exemplo  
 Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly1_a.cs`. O primeiro arquivo contém uma classe base interna `BaseClass`. No segundo arquivo, uma tentativa de instanciar a `BaseClass` produzirá um erro.  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, use os mesmos arquivos que você usou no exemplo 1 e altere o nível de acessibilidade da `BaseClass` para `public`. Também altere o nível de acessibilidade do membro `IntM` para `internal`. Nesse caso, você pode instanciar a classe, mas não pode acessar o membro interno.  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](../language-specification/index.md). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)
- [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)
- [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [private](../../../csharp/language-reference/keywords/private.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
