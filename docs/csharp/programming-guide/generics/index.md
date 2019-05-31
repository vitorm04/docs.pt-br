---
title: Genéricos – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: e32eb7c60e01ca72824ffb3a1e1269cf34650f5a
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423394"
---
# <a name="generics-c-programming-guide"></a>Genéricos (Guia de Programação em C#)
Genéricos foram adicionados à versão 2.0 da linguagem C# e o common language runtime (CLR). Genéricos apresentam ao .NET Framework o conceito de parâmetros de tipo, que possibilitam a criação de classes e métodos que adiam a especificação de um ou mais tipos até que a classe ou método seja declarado e instanciado pelo código do cliente. Por exemplo, ao usar um parâmetro de tipo genérico T, você pode escrever uma única classe que outro código de cliente pode usar sem incorrer o custo ou corre o risco de conversões de tempo de execução ou operações de conversão boxing, conforme mostrado aqui:  
  
 [!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]  

As classes e métodos genéricos combinam a capacidade de reutilização, a segurança de tipos e a eficiência de uma maneira que suas contrapartes não genéricas não conseguem. Os genéricos são usados com mais frequência com coleções e com os métodos que operam nelas. A versão 2.0 da biblioteca de classes do .NET Framework fornece um novo namespace, <xref:System.Collections.Generic>, que contém várias classes de coleção novas com base em genéricos. É recomendável que todos os aplicativos que se destinam ao .NET Framework 2.0 e posterior usem as novas classes de coleção genéricas em vez das homólogas não genéricas mais antigas, como a <xref:System.Collections.ArrayList>. Para saber mais, confira [Genéricos no .NET](../../../standard/generics/index.md).  
  
 É claro que você também pode criar tipos e métodos genéricos personalizados para fornecer suas próprias soluções e padrões de design generalizados que sejam fortemente tipados e eficientes. O exemplo de código a seguir mostra uma classe de lista vinculada genérica simples para fins de demonstração. (Na maioria dos casos, você deve usar a classe <xref:System.Collections.Generic.List%601>, fornecida pela biblioteca de classes .NET Framework, em vez de criar a sua própria classe). O parâmetro de tipo `T` é usado em vários locais em que um tipo concreto normalmente seria usado para indicar o tipo do item armazenado na lista. Ele é usado das seguintes maneiras:  
  
- Como o tipo de um parâmetro de método no método `AddHead`.  
  
- Como o tipo de retorno da propriedade `Data` na classe `Node` aninhada.  
  
- Como o tipo de `data` do membro particular na classe aninhada.  
  
 Observe que T está disponível para a classe `Node` aninhada. Quando `GenericList<T>` é instanciada com um tipo concreto, por exemplo como um `GenericList<int>`, cada ocorrência de `T` será substituída por `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 O exemplo de código a seguir mostra como o código cliente usa a classe `GenericList<T>` genérica para criar uma lista de inteiros. Ao simplesmente alterar o argumento de tipo, o código a seguir poderia facilmente ser modificado para criar listas de cadeias de caracteres ou qualquer outro tipo personalizado:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="generics-overview"></a>Visão geral de genéricos  
  
- Use tipos genéricos para maximizar a reutilização de código, o desempenho e a segurança de tipo.  
  
- O uso mais comum de genéricos é para criar classes de coleção.  
  
- A biblioteca de classes do .NET Framework contém várias classes de coleção de genéricos novos no namespace <xref:System.Collections.Generic>. Eles devem ser usados sempre que possível, em vez de classes como <xref:System.Collections.ArrayList> no namespace <xref:System.Collections>.  
  
- Você pode criar suas próprias interfaces genéricas, classes, métodos, eventos e delegados.  
  
- Classes genéricas podem ser restringidas para habilitar o acesso aos métodos em tipos de dados específicos.  
  
- Informações sobre os tipos que são usados em um tipo de dados genérico podem ser obtidas no tempo de execução por meio de reflexão.  
  
## <a name="related-sections"></a>Seções relacionadas  
 Para saber mais:  
  
- [Parâmetros de tipo genérico](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
- [Restrições a parâmetros de tipo](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
- [Classes genéricas](../../../csharp/programming-guide/generics/generic-classes.md)  
  
- [Interfaces genéricas](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
- [Métodos genéricos](../../../csharp/programming-guide/generics/generic-methods.md)  
  
- [Delegados genéricos](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
- [Diferenças entre modelos C++ e genéricos C#](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
- [Genéricos e reflexão](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
- [Genéricos em tempo de execução](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 Para obter mais informações, consulte a [Especificação da linguagem C#](~/_csharplang/spec/types.md#constructed-types).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>
- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Tipos](../../../csharp/programming-guide/types/index.md)
- [\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)
- [\<typeparamref>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
- [Genéricos no .NET](../../../standard/generics/index.md)
