---
title: 'Copiar e atualizar as expressões de registros (F #)'
description: Saiba como escrever um 'Copiar e atualizar registro expression' que copia um existente atualizações de registro, campos de especificado e retorna o registro atualizado.
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: 000746b6e76349ae6d8f338519a58034f4e29020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="8d109-103">Copiar e atualizar expressões de registro</span><span class="sxs-lookup"><span data-stu-id="8d109-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="8d109-104">Um *copiar e atualizar registro expressão* é uma expressão que copia um registro existente, atualiza campos especificados e retorna o registro atualizado.</span><span class="sxs-lookup"><span data-stu-id="8d109-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="8d109-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d109-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="8d109-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d109-106">Remarks</span></span>
<span data-ttu-id="8d109-107">Os registros são imutáveis, por padrão, para que nenhuma atualização para um registro existente é possível.</span><span class="sxs-lookup"><span data-stu-id="8d109-107">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="8d109-108">Para criar um registro atualizado em todos os campos de um registro precisa ser especificado novamente.</span><span class="sxs-lookup"><span data-stu-id="8d109-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="8d109-109">Para simplificar essa tarefa uma *copiar e atualizar a expressão de registro* pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="8d109-109">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="8d109-110">Essa expressão usa um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e o campo ausente especificados pela expressão.</span><span class="sxs-lookup"><span data-stu-id="8d109-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="8d109-111">Isso pode ser útil quando você precisa copiar um registro existente e possivelmente alterar alguns dos valores de campo.</span><span class="sxs-lookup"><span data-stu-id="8d109-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="8d109-112">Veja, por exemplo, um registro recém-criada.</span><span class="sxs-lookup"><span data-stu-id="8d109-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="8d109-113">Se você atualizar somente no campo de registro de que você pode usar o *copiar e atualizar registro expressão* como a seguir:</span><span class="sxs-lookup"><span data-stu-id="8d109-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="8d109-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d109-114">See Also</span></span>
[<span data-ttu-id="8d109-115">Registros</span><span class="sxs-lookup"><span data-stu-id="8d109-115">Records</span></span>](records.md)

[<span data-ttu-id="8d109-116">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="8d109-116">F# Language Reference</span></span>](index.md)
