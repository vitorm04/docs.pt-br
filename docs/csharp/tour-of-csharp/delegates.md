---
title: "Representantes do C# – um tour pela linguagem C# | Microsoft Docs"
description: "Aprenda a associação tardia com delegados C#"
keywords: ".NET, csharp, delegado, lambda, associação tardia"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 217fd974f547a4a84b328979ee94ee634038b213
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---

# Delegados
<a id="delegates" class="xliff"></a>

Um ***delegado*** é um tipo que representa referências aos métodos com uma lista de parâmetros e tipo de retorno específicos. Delegados possibilitam o tratamento de métodos como entidades que podem ser atribuídos a variáveis e passadas como parâmetros. Os delegados são parecidos com o conceito de ponteiros de função em outras linguagens, mas ao contrário dos ponteiros de função, os delegados são orientados a objetos e fortemente tipados.

O exemplo a seguir declara e usa um tipo delegado chamado `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Uma instância do tipo delegado `Function` pode fazer referência a qualquer método que usa um argumento `double` e retorna um valor `double`. O método `Apply` aplica uma determinada função aos elementos de um `double[]`, retornando um `double[]` com os resultados. No método `Main`, `Apply` é usado para aplicar três funções diferentes para um `double[]`.

Um delegado pode referenciar um método estático (como `Square` ou `Math.Sin` no exemplo anterior) ou um método de instância (como `m.Multiply` no exemplo anterior). Um delegado que referencia um método de instância também referencia um objeto específico, e quando o método de instância é invocado por meio do delegado, esse objeto se torna `this` na invocação.

Os delegados podem ser criados usando funções anônimas, que são "métodos embutidos" criados dinamicamente. As funções anônimas podem ver as variáveis locais dos métodos ao redor. Assim, o exemplo de multiplicador acima pode ser gravado mais facilmente sem usar uma classe de multiplicador:

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Uma propriedade interessante e útil de um delegado é que ele não sabe ou se importa com a classe do método que referencia; o que importa é que o método referenciado tem os mesmos parâmetros e o tipo de retorno do delegado.

>[!div class="step-by-step"]
[Anterior](enums.md)
[Próximo](attributes.md)

