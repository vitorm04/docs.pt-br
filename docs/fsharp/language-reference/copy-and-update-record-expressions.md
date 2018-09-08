---
title: 'Copiar e atualizar expressões de registro (F #)'
description: Saiba como escrever um 'Copiar e atualizar registro expression' que copia um existente atualizações de registro, campos de especificado e retorna o registro atualizado.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197388"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="3aa0b-103">Copiar e atualizar expressões de registro</span><span class="sxs-lookup"><span data-stu-id="3aa0b-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="3aa0b-104">Um *copiar e atualizar registro expressão* é uma expressão que copia um registro existente, atualiza os campos especificados e retorna o registro atualizado.</span><span class="sxs-lookup"><span data-stu-id="3aa0b-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="3aa0b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3aa0b-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="3aa0b-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="3aa0b-106">Remarks</span></span>

<span data-ttu-id="3aa0b-107">Os registros são imutáveis, por padrão, para que nenhuma atualização para um registro existente seja possível.</span><span class="sxs-lookup"><span data-stu-id="3aa0b-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="3aa0b-108">Para criar um registro atualizado em todos os campos de um registro precisa ser especificado novamente.</span><span class="sxs-lookup"><span data-stu-id="3aa0b-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="3aa0b-109">Para simplificar essa tarefa uma *copiar e atualizar registro expressão* pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="3aa0b-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="3aa0b-110">Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificados pela expressão.</span><span class="sxs-lookup"><span data-stu-id="3aa0b-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="3aa0b-111">Isso pode ser útil quando você tem que copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.</span><span class="sxs-lookup"><span data-stu-id="3aa0b-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="3aa0b-112">Veja, por exemplo, um registro recém-criado.</span><span class="sxs-lookup"><span data-stu-id="3aa0b-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="3aa0b-113">Se você atualizar somente no campo desse registro, você pode usar o *copiar e atualizar registro expressão* semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="3aa0b-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="3aa0b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3aa0b-114">See also</span></span>

- [<span data-ttu-id="3aa0b-115">Registros</span><span class="sxs-lookup"><span data-stu-id="3aa0b-115">Records</span></span>](records.md)
- [<span data-ttu-id="3aa0b-116">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="3aa0b-116">F# Language Reference</span></span>](index.md)
