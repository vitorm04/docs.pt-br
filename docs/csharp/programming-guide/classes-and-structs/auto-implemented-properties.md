---
title: Propriedades autoimplementadas – Guia de Programação em C#
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170319"
---
# <a name="auto-implemented-properties-c-programming-guide"></a>Propriedades autoimplementadas (Guia de Programação em C#)

No C# 3.0 e versões posteriores, as propriedades autoimplementadas tornam a declaração de propriedade mais concisa quando nenhuma lógica adicional for necessária nos acessadores de propriedade. Elas também habilitam o código do cliente a criar objetos. Ao declarar uma propriedade, como mostrado no exemplo a seguir, o compilador cria um campo de suporte privado e anônimo que pode ser acessado somente por meio dos acessadores `get` e `set` da propriedade.
  
## <a name="example"></a>Exemplo

O exemplo a seguir mostra uma classe simples que tem algumas propriedades autoimplementadas:  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

Você não pode declarar propriedades implementadas automaticamente em interfaces. Propriedades implementadas automaticamente declaram um campo de backup de instância privada e as interfaces não podem declarar campos de ocorrência. Declarar uma propriedade em uma interface sem definir um corpo declara uma propriedade com acessórios que devem ser implementados por cada tipo que implementa essa interface.

No C# 6 e versões posteriores, é possível inicializar as propriedades autoimplementadas da mesma forma que os campos:  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

A classe mostrada no exemplo anterior é mutável. O código do cliente pode alterar os valores em objetos após a criação. Em classes complexas que contêm comportamentos significativos (métodos) e dados, muitas vezes é necessário ter propriedades públicas. No entanto, para classes pequenas ou structs que apenas encapsulam um conjunto de valores (dados) e têm poucos ou nenhum comportamento, faça com que os objetos se tornem imutáveis declarando o acessador set como [privado](../../language-reference/keywords/private.md) (imutável para consumidores) ou declarando somente um acessador get (imutável em todos os lugares, exceto no construtor).  Para obter mais informações, consulte [Como implementar uma classe leve com propriedades auto-implementadas.](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)

## <a name="see-also"></a>Confira também

- [Propriedades](./properties.md)
- [Modificadores](/dotnet/csharp/language-reference/keywords)
