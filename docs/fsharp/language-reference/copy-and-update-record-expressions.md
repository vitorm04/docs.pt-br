---
title: 'Copiar e atualizar as expressões de registros (F #)'
description: Saiba como escrever um 'Copiar e atualizar registro expression' que copia um existente atualizações de registro, campos de especificado e retorna o registro atualizado.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: 000746b6e76349ae6d8f338519a58034f4e29020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563053"
---
# <a name="copy-and-update-record-expressions"></a>Copiar e atualizar expressões de registro

Um *copiar e atualizar registro expressão* é uma expressão que copia um registro existente, atualiza campos especificados e retorna o registro atualizado.


## <a name="syntax"></a>Sintaxe

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Comentários
Os registros são imutáveis, por padrão, para que nenhuma atualização para um registro existente é possível. Para criar um registro atualizado em todos os campos de um registro precisa ser especificado novamente. Para simplificar essa tarefa uma *copiar e atualizar a expressão de registro* pode ser usado. Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificados pela expressão.
Isso pode ser útil quando você precisa copiar um registro existente e possivelmente alterar alguns dos valores de campo.

Veja, por exemplo, um registro recém-criada.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Se você atualizar somente no campo de registro de que você pode usar o *copiar e atualizar registro expressão* como a seguir:

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Consulte também
[Registros](records.md)

[Referência da Linguagem F#](index.md)
