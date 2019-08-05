---
title: extern alias – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: cfb662203216aa6ca208ceec20d55164c65163dc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626653"
---
# <a name="extern-alias-c-reference"></a>extern alias (Referência de C#)
Talvez seja necessário referenciar duas versões de assemblies que têm os mesmos nomes de tipo totalmente qualificado. Por exemplo, você pode ter que usar duas ou mais versões de um assembly no mesmo aplicativo. Ao usar um alias de assembly externo, os namespaces de cada assembly podem ser encapsulados dentro de namespaces de nível raiz nomeados pelo alias, permitindo que eles sejam utilizados no mesmo arquivo.  
  
> [!NOTE]
>  A palavra-chave [extern](../../../csharp/language-reference/keywords/extern.md) também é usada como um modificador de método, declarando um método escrito em código não gerenciado.  
  
 Para referenciar dois assemblies com os mesmos nomes de tipo totalmente qualificado, um alias deve ser especificado em um prompt de comando, da seguinte maneira:  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Isso cria os alias externos `GridV1` e `GridV2`. Para usar esses aliases de dentro de um programa, referencie-os usando a palavra-chave `extern`. Por exemplo:  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Cada declaração de alias externo apresenta um namespace de nível raiz adicional que funciona de forma paralela (mas não dentro) com o namespace global. Portanto, os tipos de cada assembly podem ser referenciados sem ambiguidade, usando seus nomes totalmente qualificados, enraizados no alias de namespace apropriado.  
  
 No exemplo anterior, `GridV1::Grid` seria o controle de grade da `grid.dll` e `GridV2::Grid` seria o controle de grade da `grid20.dll`.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Referência de C#](../../../csharp/language-reference/index.md)
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)
- [:: ??](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [/reference (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)
