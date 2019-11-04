---
title: Construtores particulares – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 918d39b8aed25395106942524baa3b51221933dc
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418872"
---
# <a name="private-constructors-c-programming-guide"></a>Construtores particulares (Guia de Programação em C#)
Um construtor particular é um construtor de instância especial. Normalmente, ele é usado em classes que contêm apenas membros estáticos. Se uma classe tiver um ou mais construtores particulares e nenhum construtor público, outras classes (exceto as classes aninhadas) não poderão criar instâncias dessa classe. Por exemplo:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 A declaração do construtor vazio impede a geração automática de um construtor sem parâmetro. Observe que, se você não usar um modificador de acesso com o construtor, ele ainda será privado por padrão. No entanto, o modificador [private](../../language-reference/keywords/private.md) geralmente é usado explicitamente para deixar claro que a classe não pode ser instanciada.  
  
 Construtores particulares são usados para impedir a criação de instâncias de uma classe quando não há métodos ou campos de instância, como a classe <xref:System.Math> ou quando um método é chamado para obter uma instância de uma classe. Se todos os métodos na classe forem estáticos, considere deixar toda a classe estática. Para obter mais informações, consulte [Classes Estáticas e Membros de Classes Estáticas](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Exemplo  
 A seguir, temos um exemplo de uma classe usando um construtor particular.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Observe que se você remover a marca de comentário da seguinte instrução do exemplo, ela gerará um erro porque o construtor está inacessível devido a seu nível de proteção:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  

Para obter mais informações, veja [Construtores privados](~/_csharplang/spec/classes.md#private-constructors) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction). A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Classes e Structs](./index.md)
- [Construtores](./constructors.md)
- [Finalizadores](./destructors.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
