---
title: Propriedades autoimplementadas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 92d20ec305fcbc824a929459ff69a29c22b2ff34
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971271"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Propriedades autoimplementadas (Guia de Programação em C#)
No C# 3.0 e versões posteriores, as propriedades autoimplementadas tornam a declaração de propriedade mais concisa quando nenhuma lógica adicional for necessária nos acessadores de propriedade. Elas também habilitam o código do cliente a criar objetos. Ao declarar uma propriedade, como mostrado no exemplo a seguir, o compilador cria um campo de suporte privado e anônimo que pode ser acessado somente por meio dos acessadores `get` e `set` da propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra uma classe simples que tem algumas propriedades autoimplementadas:  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 No C# 6 e versões posteriores, é possível inicializar as propriedades autoimplementadas da mesma forma que os campos:  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 A classe mostrada no exemplo anterior é mutável. O código cliente pode alterar os valores nos objetos após sua criação. Em classes complexas que contêm comportamento significativo (métodos), bem como dados, geralmente é necessário ter propriedades públicas. No entanto, para classes pequenas ou structs que apenas encapsulam um conjunto de valores (dados) e têm poucos ou nenhum comportamento, faça com que os objetos se tornem imutáveis declarando o acessador set como [privado](../../language-reference/keywords/private.md) (imutável para consumidores) ou declarando somente um acessador get (imutável em todos os lugares, exceto no construtor).  Para obter mais informações, consulte [como implementar uma classe leve com propriedades implementadas automaticamente](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
  
## <a name="see-also"></a>Consulte também

- [Propriedades](./properties.md)
- [Modificadores](/dotnet/csharp/language-reference/keywords)
