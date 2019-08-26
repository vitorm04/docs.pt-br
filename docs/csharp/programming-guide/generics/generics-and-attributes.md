---
title: Genéricos e atributos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 99a24a7069145dfad5ce6c9c91f2a8653eb9a224
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589634"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Genéricos e atributos (Guia de Programação em C#)
Atributos podem ser aplicados a tipos genéricos da mesma forma que a tipos não genéricos. Para obter mais informações sobre a aplicação de atributos, consulte [Atributos](../concepts/attributes/index.md).  
  
 Atributos personalizados são permitidos somente para referenciar tipos genéricos abertos, que são tipos genéricos para os quais nenhum argumento de tipo é fornecido e tipos genéricos construídos fechados, que fornecem argumentos para todos os parâmetros de tipo.  
  
 Os exemplos a seguir usam esse atributo personalizado:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Um atributo pode referenciar um tipo genérico aberto:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Especifica vários parâmetros de tipo usando a quantidade apropriada de vírgulas. Neste exemplo, `GenericClass2` tem dois parâmetros de tipo:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Um atributo pode referenciar um tipo genérico construído fechado:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Um atributo que referencia um parâmetro de tipo genérico causará um erro em tempo de compilação:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Um tipo genérico não pode herdar de <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Para obter informações sobre um tipo genérico ou um parâmetro de tipo em tempo de execução, é possível usar os métodos do <xref:System.Reflection>. Para obter mais informações, consulte [Genéricos e Reflexão](./generics-and-reflection.md)  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../index.md)
- [Genéricos](./index.md)
- [Atributos](../../../standard/attributes/index.md)
