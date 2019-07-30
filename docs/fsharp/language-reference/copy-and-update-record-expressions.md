---
title: Copiar e atualizar expressões de registro
description: Saiba como escrever uma ' copiar e atualizar expressão ' que copia um registro ou registro anônimo existente, atualiza campos especificados e retorna o registro atualizado ou o registro anônimo.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630382"
---
# <a name="copy-and-update-record-expressions"></a>Copiar e atualizar expressões de registro

Uma *expressão para copiar e atualizar registro* é uma expressão que copia um registro existente, atualiza campos especificados e retorna o registro atualizado.

## <a name="syntax"></a>Sintaxe

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>Comentários

Registros e registros anônimos são imutáveis por padrão, para que não haja nenhuma atualização para um registro existente possível. Para criar um registro atualizado, todos os campos de um registro teriam que ser especificados novamente. Para simplificar essa tarefa, é possível usar uma *expressão de cópia e atualização* . Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificado pela expressão.

Isso pode ser útil quando você precisa copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.

Considere uma instância de um registro recém-criado.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Se você atualizar apenas no campo do registro, poderá usar a *expressão copiar e atualizar registro* como a seguinte:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Consulte também

- [Registros](records.md)
- [Registros anônimos](anonymous-records.md)
- [Referência da Linguagem F#](index.md)
