---
title: Como usar propriedades indexadas no guia de C# programação da interoperabilidade com
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: aa4dc6da520fc58a99a9691aa39e412468aa02b5
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635308"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Como usar propriedades indexadas na programação de interoperabilidade COM (guia deC# programação)
As *propriedades indexadas* melhoram a maneira na qual as propriedades COM que têm parâmetros são consumidas na programação em C#. As propriedades indexadas trabalham juntamente com outras funcionalidades no Visual C#, como [argumentos nomeados e opcionais](../classes-and-structs/named-and-optional-arguments.md), um novo tipo ([dinâmico](../../language-reference/builtin-types/reference-types.md)) e [informações de tipo inseridas](../../../standard/assembly/embed-types-visual-studio.md) para melhorar a programação do Microsoft Office.  
  
 Nas versões anteriores do C#, os métodos são acessíveis como propriedades apenas se o método `get` não tem parâmetros e o método `set` tem apenas um parâmetro de valor. No entanto, nem todas as propriedades COM atendem a essas restrições. Por exemplo, a propriedade <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> do Excel tem um acessador `get` que requer um parâmetro para o nome do intervalo. No passado, como não era possível acessar a propriedade `Range` diretamente, era necessário usar o método `get_Range` em vez disso, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Em vez disso, as propriedades indexadas permitem escrever o seguinte:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> O exemplo anterior também usa o recurso [argumentos opcionais](../classes-and-structs/named-and-optional-arguments.md), que permite que você omita `Type.Missing`.  
  
 Da mesma forma, para definir o valor da propriedade `Value` de um objeto <xref:Microsoft.Office.Interop.Excel.Range> no C# 3.0 e versões anteriores, são necessários dois argumentos. Um fornece um argumento para um parâmetro opcional que especifica o tipo do valor de intervalo. O outro fornece o valor para a propriedade `Value`. Os exemplos a seguir ilustram essas técnicas. Ambos definem o valor da célula A1 como `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Em vez disso, as propriedades indexadas permitem escrever o código a seguir.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Não é possível criar propriedades indexadas de sua preferência. O recurso dá suporte apenas ao consumo de propriedades indexadas existentes.  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra um exemplo completo. Para obter mais informações sobre como configurar um projeto que acessa a API do Office, consulte [como acessar objetos de interoperabilidade do Office C# usando recursos](./how-to-access-office-onterop-objects.md).
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Veja também

- [Argumentos nomeados e opcionais](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Usando o tipo dynamic](../types/using-type-dynamic.md)
- [Como usar argumentos nomeados e opcionais na programação do Office](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Como acessar objetos de interoperabilidade do C# Office usando recursos](./how-to-access-office-onterop-objects.md)
- [Passo a passo: programação do Office](./walkthrough-office-programming.md)
