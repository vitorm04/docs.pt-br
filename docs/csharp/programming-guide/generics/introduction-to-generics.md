---
title: Introdução aos genéricos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: d09cc686e934f722193cb4671d25671f7f4ef5f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978508"
---
# <a name="introduction-to-generics-c-programming-guide"></a>Introdução aos genéricos (Guia de Programação em C#)
As classes e métodos genéricos combinam a capacidade de reutilização, a segurança de tipos e a eficiência de uma maneira que suas contrapartes não genéricas não conseguem. Os genéricos são usados com mais frequência com coleções e com os métodos que operam nelas. A versão 2.0 da biblioteca de classes do .NET Framework fornece um novo namespace, <xref:System.Collections.Generic>, que contém várias classes de coleção novas com base em genéricos. É recomendável que todos os aplicativos que se destinam ao .NET Framework 2.0 e posterior usem as novas classes de coleção genéricas em vez das homólogas não genéricas mais antigas, como a <xref:System.Collections.ArrayList>. Para saber mais, confira [Genéricos no .NET](../../../standard/generics/index.md).  
  
 É claro que você também pode criar tipos e métodos genéricos personalizados para fornecer suas próprias soluções e padrões de design generalizados que sejam fortemente tipados e eficientes. O exemplo de código a seguir mostra uma classe de lista vinculada genérica simples para fins de demonstração. (Na maioria dos casos, você deve usar a classe <xref:System.Collections.Generic.List%601>, fornecida pela biblioteca de classes .NET Framework, em vez de criar a sua própria classe). O parâmetro de tipo `T` é usado em vários locais em que um tipo concreto normalmente seria usado para indicar o tipo do item armazenado na lista. Ele é usado das seguintes maneiras:  
  
-   Como o tipo de um parâmetro de método no método `AddHead`.  
  
-   Como o tipo de retorno da propriedade `Data` na classe `Node` aninhada.  
  
-   Como o tipo de `data` do membro particular na classe aninhada.  
  
 Observe que T está disponível para a classe `Node` aninhada. Quando `GenericList<T>` é instanciada com um tipo concreto, por exemplo como um `GenericList<int>`, cada ocorrência de `T` será substituída por `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 O exemplo de código a seguir mostra como o código cliente usa a classe `GenericList<T>` genérica para criar uma lista de inteiros. Ao simplesmente alterar o argumento de tipo, o código a seguir poderia facilmente ser modificado para criar listas de cadeias de caracteres ou qualquer outro tipo personalizado:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Genéricos](../../../csharp/programming-guide/generics/index.md)
