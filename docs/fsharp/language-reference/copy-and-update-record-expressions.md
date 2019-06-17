---
title: Copiar e atualizar expressões de registro
description: Saiba como gravar um 'Copiar e atualizar expression' que copia um registro existente ou registro anônimo, as atualizações especificadas campos e retorna o registro atualizado ou o registro anônimo.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: d16f5ca337047ab2eecc8828b21d8a423bf39a1f
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041737"
---
# <a name="copy-and-update-record-expressions"></a>Copiar e atualizar expressões de registro

Um *copiar e atualizar registro expressão* é uma expressão que copia um registro existente, atualiza os campos especificados e retorna o registro atualizado.

## <a name="syntax"></a>Sintaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Comentários

Registros e registros anônimos são imutáveis por padrão, para que nenhuma atualização para um registro existente seja possível. Para criar um registro atualizado em todos os campos de um registro precisa ser especificado novamente. Para simplificar essa tarefa uma *copiar e atualizar expressão* pode ser usado. Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificados pela expressão.

Isso pode ser útil quando você tem que copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.

Veja, por exemplo, um registro recém-criado.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Se você atualizar somente no campo desse registro, você pode usar o *copiar e atualizar registro expressão* semelhante ao seguinte:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Consulte também

- [Registros](records.md)
- [Registros anônimos](anonymous-records.md)
- [Referência da Linguagem F#](index.md)
