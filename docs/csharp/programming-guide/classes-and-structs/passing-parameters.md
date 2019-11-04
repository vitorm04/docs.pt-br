---
title: Passando parâmetros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 22f58bda5aa5b60248902a4130f3ea9b6caa65cf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419120"
---
# <a name="passing-parameters-c-programming-guide"></a>Passando parâmetros (Guia de Programação em C#)
No C#, argumentos podem ser passados para parâmetros por valor ou por referência. A passagem por referência permite que métodos, propriedades, indexadores, operadores, construtores e membros da função alterem o valor dos parâmetros e façam essa alteração persistir no ambiente de chamada. Para passar um parâmetro por referência com a intenção de alterar o valor, use a palavra-chave `ref` ou `out`. Para passar por referência com a intenção de evitar a cópia, mas não alterar o valor, use o modificador `in`. Para simplificar, somente a palavra-chave `ref` é usada nos exemplos neste tópico. Para obter mais informações sobre a diferença entre `in`, `ref` e `out`, consulte [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) e [out](../../language-reference/keywords/out-parameter-modifier.md).  
  
 O exemplo a seguir ilustra a diferença entre parâmetros de valor e referência.  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 Para mais informações, consulte os seguintes tópicos:  
  
- [Passando parâmetros de tipo de valor](./passing-value-type-parameters.md)  
  
- [Passando parâmetros de tipo de referência](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja as [listas de argumentos](~/_csharplang/spec/expressions.md#argument-lists) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Métodos](./methods.md)
