---
title: Como determinar se um objeto .NET padrão é serializável
description: Mostra como determinar se um tipo .NET Standard pode ser serializado em tempo de execução.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537963"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a>Como determinar se um objeto .NET padrão é serializável

O .NET Standard é uma especificação que define os tipos e membros que devem estar presentes em implementações específicas do .NET que estão em conformidade com essa versão do padrão. No entanto, o .NET Standard não define se um tipo é serializável. Os tipos definidos na biblioteca do .NET Standard não são marcados com o <xref:System.SerializableAttribute> atributo. Em vez disso, a implementações específicas do .NET, como o .NET Framework e .NET Core, são livres para determinar se um determinado tipo é serializável. 

Se você tiver desenvolvido uma biblioteca que tem como alvo o .NET Standard, sua biblioteca pode ser consumida por qualquer implementação do .NET que dá suporte a .NET Standard. Isso significa que você não pode saber de antemão se um determinado tipo é serializável; Você somente pode determinar se ele é serializável em tempo de execução.

Você pode determinar se um objeto é serializável em tempo de execução ao recuperar o valor da <xref:System.Type.IsSerializable> propriedade de um <xref:System.Type> objeto que representa o tipo do objeto. O exemplo a seguir fornece uma implementação. Ele define uma `IsSerializable(Object)` método de extensão que indica se qualquer <xref:System.Object> instância pode ser serializada.

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

Em seguida, você pode passar qualquer objeto para o método para determinar se ele pode ser serializado e desserializado na implementação atual do .NET, como mostra o exemplo a seguir:

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a>Consulte também

- [Serialização binária](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
