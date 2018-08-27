---
title: protected (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 2da8211ac21a5016478e7b881e7f2f9925b49cef
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001328"
---
# <a name="protected-c-reference"></a>protected (Referência de C#)
A palavra-chave `protected` é um modificador de acesso de membro. 

 > Esta página aborda o acesso `protected`. A palavra-chave `protected` também faz parte dos modificadores de acesso [`protected internal`](./protected-internal.md) e [`private protected`](./private-protected.md). 

Um membro protegido é acessível dentro de sua classe e por instâncias da classe derivada. 

Para obter uma comparação de `protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md). 
  
## <a name="example"></a>Exemplo  
 Um membro protegido de uma classe base será acessível em uma classe derivada somente se o acesso ocorrer por meio do tipo da classe derivada. Por exemplo, considere o seguinte segmento de código:  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 A instrução `a.x = 10` gera um erro porque ela é feita dentro do método estático Main e não em uma instância da classe B.  
  
 Membros de struct não podem ser protegidos porque o struct não pode ser herdado.  
  
## <a name="example"></a>Exemplo  
 Nesse exemplo, a classe `DerivedPoint` é derivada de `Point`. Portanto, você pode acessar os membros protegidos da classe base diretamente da classe derivada.  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 Se você alterar os níveis de acesso de `x` e `y` para [private](../../../csharp/language-reference/keywords/private.md), o compilador emitirá as mensagens de erro:  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## 

- [Referência de C#](../../../csharp/language-reference/index.md)  
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
- [Modificadores de acesso](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [Modificadores](../../../csharp/language-reference/keywords/modifiers.md)  
- [public](../../../csharp/language-reference/keywords/public.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [internal](../../../csharp/language-reference/keywords/internal.md)  
- [Questões de segurança de palavras-chave virtuais internas](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))