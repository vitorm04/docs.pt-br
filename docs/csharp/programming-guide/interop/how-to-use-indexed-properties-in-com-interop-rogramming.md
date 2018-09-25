---
title: Como usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 0169bfa6eb3ba01a9a88c2b247ad3f78da67d59c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208816"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Como usar propriedades indexadas na programação para interoperabilidade COM (Guia de Programação em C#)
As *propriedades indexadas* melhoram a maneira na qual as propriedades COM que têm parâmetros são consumidas na programação em C#. As propriedades indexadas trabalham juntamente com outras funcionalidades no Visual C#, como [argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), um novo tipo ([dinâmico](../../../csharp/language-reference/keywords/dynamic.md)) e [informações de tipo inseridas](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) para melhorar a programação do Microsoft Office.  
  
 Nas versões anteriores do C#, os métodos são acessíveis como propriedades apenas se o método `get` não tem parâmetros e o método `set` tem apenas um parâmetro de valor. No entanto, nem todas as propriedades COM atendem a essas restrições. Por exemplo, a propriedade <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> do Excel tem um acessador `get` que requer um parâmetro para o nome do intervalo. No passado, como não era possível acessar a propriedade `Range` diretamente, era necessário usar o método `get_Range` em vez disso, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Em vez disso, as propriedades indexadas permitem escrever o seguinte:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  O exemplo anterior também usa o recurso [argumentos opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), que permite que você omita `Type.Missing`.  
  
 Da mesma forma, para definir o valor da propriedade `Value` de um objeto <xref:Microsoft.Office.Interop.Excel.Range> no Visual C# 2008 e versões anteriores, são necessários dois argumentos. Um fornece um argumento para um parâmetro opcional que especifica o tipo do valor de intervalo. O outro fornece o valor para a propriedade `Value`. Os exemplos a seguir ilustram essas técnicas. Ambos definem o valor da célula A1 como `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Em vez disso, as propriedades indexadas permitem escrever o código a seguir.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Não é possível criar propriedades indexadas de sua preferência. O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra um exemplo completo. Para obter mais informações sobre como configurar um projeto que acessa a API do Office, consulte [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Consulte também

- [Argumentos nomeados e opcionais](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
- [Usando o tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
- [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
- [Passo a passo: programação do Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
