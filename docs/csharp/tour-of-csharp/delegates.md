---
title: Delegados em C# - um tour pela linguagem C#
description: Aprenda a associação tardia com delegados C#
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159163"
---
# <a name="delegates"></a>Delega

Um ***delegado*** é um tipo que representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos. Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros. Os delegados são semelhantes ao conceito de ponteiros de função encontrados em algumas outras línguas. Ao contrário dos ponteiros de função, os delegados são orientados a objetos e seguros para o tipo.

O exemplo a seguir declara e usa um tipo delegado chamado `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Uma instância do tipo delegado `Function` pode fazer referência a qualquer método que usa um argumento `double` e retorna um valor `double`. O método `Apply` aplica uma determinada função aos elementos de um `double[]`, retornando um `double[]` com os resultados. No método `Main`, `Apply` é usado para aplicar três funções diferentes para um `double[]`.

Um delegado pode referenciar um método estático (como `Square` ou `Math.Sin` no exemplo anterior) ou um método de instância (como `m.Multiply` no exemplo anterior). Um delegado que referencia um método de instância também referencia um objeto específico, e quando o método de instância é invocado por meio do delegado, esse objeto se torna `this` na invocação.

Os delegados também podem ser criados usando funções anônimas, que são "métodos inline" que são criados quando declarados. As funções anônimas podem ver as variáveis locais dos métodos ao redor. O exemplo a seguir não cria uma classe:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Um delegado não sabe ou se preocupa com a classe do método que ele se refere; tudo o que importa é que o método referenciado tem os mesmos parâmetros e tipo de retorno que o delegado.

>[!div class="step-by-step"]
>[Próximo](interfaces.md)
>[anterior](attributes.md)
