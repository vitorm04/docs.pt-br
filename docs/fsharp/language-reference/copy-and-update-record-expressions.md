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
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="d1385-103">Copiar e atualizar expressões de registro</span><span class="sxs-lookup"><span data-stu-id="d1385-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="d1385-104">Uma *expressão para copiar e atualizar registro* é uma expressão que copia um registro existente, atualiza campos especificados e retorna o registro atualizado.</span><span class="sxs-lookup"><span data-stu-id="d1385-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1385-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d1385-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="d1385-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d1385-106">Remarks</span></span>

<span data-ttu-id="d1385-107">Registros e registros anônimos são imutáveis por padrão, para que não haja nenhuma atualização para um registro existente possível.</span><span class="sxs-lookup"><span data-stu-id="d1385-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="d1385-108">Para criar um registro atualizado, todos os campos de um registro teriam que ser especificados novamente.</span><span class="sxs-lookup"><span data-stu-id="d1385-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="d1385-109">Para simplificar essa tarefa, é possível usar uma *expressão de cópia e atualização* .</span><span class="sxs-lookup"><span data-stu-id="d1385-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="d1385-110">Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificado pela expressão.</span><span class="sxs-lookup"><span data-stu-id="d1385-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="d1385-111">Isso pode ser útil quando você precisa copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.</span><span class="sxs-lookup"><span data-stu-id="d1385-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="d1385-112">Considere uma instância de um registro recém-criado.</span><span class="sxs-lookup"><span data-stu-id="d1385-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="d1385-113">Se você atualizar apenas no campo do registro, poderá usar a *expressão copiar e atualizar registro* como a seguinte:</span><span class="sxs-lookup"><span data-stu-id="d1385-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="d1385-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d1385-114">See also</span></span>

- [<span data-ttu-id="d1385-115">Registros</span><span class="sxs-lookup"><span data-stu-id="d1385-115">Records</span></span>](records.md)
- [<span data-ttu-id="d1385-116">Registros anônimos</span><span class="sxs-lookup"><span data-stu-id="d1385-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="d1385-117">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="d1385-117">F# Language Reference</span></span>](index.md)
