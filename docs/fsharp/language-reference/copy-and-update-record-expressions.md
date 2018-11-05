---
title: 'Copiar e atualizar expressões de registro (F #)'
description: Saiba como escrever um 'Copiar e atualizar registro expression' que copia um existente atualizações de registro, campos de especificado e retorna o registro atualizado.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45990837"
---
# <a name="copy-and-update-record-expressions"></a>Copiar e atualizar expressões de registro

Um *copiar e atualizar registro expressão* é uma expressão que copia um registro existente, atualiza os campos especificados e retorna o registro atualizado.

## <a name="syntax"></a>Sintaxe

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Comentários

Os registros são imutáveis, por padrão, para que nenhuma atualização para um registro existente seja possível. Para criar um registro atualizado em todos os campos de um registro precisa ser especificado novamente. Para simplificar essa tarefa uma *copiar e atualizar registro expressão* pode ser usado. Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificados pela expressão.
Isso pode ser útil quando você tem que copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.

Veja, por exemplo, um registro recém-criado.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Se você atualizar somente no campo desse registro, você pode usar o *copiar e atualizar registro expressão* semelhante ao seguinte:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Consulte também

- [Registros](records.md)
- [Referência da Linguagem F#](index.md)
