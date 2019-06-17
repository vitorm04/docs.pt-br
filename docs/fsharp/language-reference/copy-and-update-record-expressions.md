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
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="5acba-103">Copiar e atualizar expressões de registro</span><span class="sxs-lookup"><span data-stu-id="5acba-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="5acba-104">Um *copiar e atualizar registro expressão* é uma expressão que copia um registro existente, atualiza os campos especificados e retorna o registro atualizado.</span><span class="sxs-lookup"><span data-stu-id="5acba-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="5acba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5acba-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="5acba-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="5acba-106">Remarks</span></span>

<span data-ttu-id="5acba-107">Registros e registros anônimos são imutáveis por padrão, para que nenhuma atualização para um registro existente seja possível.</span><span class="sxs-lookup"><span data-stu-id="5acba-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="5acba-108">Para criar um registro atualizado em todos os campos de um registro precisa ser especificado novamente.</span><span class="sxs-lookup"><span data-stu-id="5acba-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="5acba-109">Para simplificar essa tarefa uma *copiar e atualizar expressão* pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="5acba-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="5acba-110">Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificados pela expressão.</span><span class="sxs-lookup"><span data-stu-id="5acba-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="5acba-111">Isso pode ser útil quando você tem que copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.</span><span class="sxs-lookup"><span data-stu-id="5acba-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="5acba-112">Veja, por exemplo, um registro recém-criado.</span><span class="sxs-lookup"><span data-stu-id="5acba-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="5acba-113">Se você atualizar somente no campo desse registro, você pode usar o *copiar e atualizar registro expressão* semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="5acba-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="5acba-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5acba-114">See also</span></span>

- [<span data-ttu-id="5acba-115">Registros</span><span class="sxs-lookup"><span data-stu-id="5acba-115">Records</span></span>](records.md)
- [<span data-ttu-id="5acba-116">Registros anônimos</span><span class="sxs-lookup"><span data-stu-id="5acba-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="5acba-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="5acba-117">F# Language Reference</span></span>](index.md)
