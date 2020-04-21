---
title: Copiar e atualizar expressões de registro
description: Aprenda a escrever uma expressão de 'copiar e atualizar' que copie um registro ou registro anônimo existente, atualize campos especificados e devolva o registro atualizado ou o registro anônimo.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739283"
---
# <a name="copy-and-update-record-expressions"></a>Copiar e atualizar expressões de registro

Uma *expressão de registro de cópia e atualização* é uma expressão que copia um registro existente, atualiza campos especificados e retorna o registro atualizado.

## <a name="syntax"></a>Sintaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Comentários

Registros e registros anônimos são imutáveis por padrão, portanto não é possível atualizar um registro existente. Para criar um registro atualizado, todos os campos de um registro teriam que ser especificados novamente. Para simplificar essa tarefa, uma *expressão de cópia e atualização* pode ser usada. Essa expressão pega um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e do campo ausente especificado pela expressão.

Isso pode ser útil quando você tem que copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.

Por exemplo, um registro recém-criado.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Para atualizar apenas dois campos nesse registro, você pode usar a *expressão de registro de cópia e atualização:*

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Confira também

- [Registros](records.md)
- [Registros Anônimos](anonymous-records.md)
- [Referência de idioma F#](index.md)
