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
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="1823f-103">Copiar e atualizar expressões de registro</span><span class="sxs-lookup"><span data-stu-id="1823f-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="1823f-104">Uma *expressão de registro de cópia e atualização* é uma expressão que copia um registro existente, atualiza campos especificados e retorna o registro atualizado.</span><span class="sxs-lookup"><span data-stu-id="1823f-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="1823f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1823f-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="1823f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1823f-106">Remarks</span></span>

<span data-ttu-id="1823f-107">Registros e registros anônimos são imutáveis por padrão, portanto não é possível atualizar um registro existente.</span><span class="sxs-lookup"><span data-stu-id="1823f-107">Records and anonymous records are immutable by default, so it is not possible to update an existing record.</span></span> <span data-ttu-id="1823f-108">Para criar um registro atualizado, todos os campos de um registro teriam que ser especificados novamente.</span><span class="sxs-lookup"><span data-stu-id="1823f-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="1823f-109">Para simplificar essa tarefa, uma *expressão de cópia e atualização* pode ser usada.</span><span class="sxs-lookup"><span data-stu-id="1823f-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="1823f-110">Essa expressão pega um registro existente, cria um novo do mesmo tipo usando campos especificados da expressão e do campo ausente especificado pela expressão.</span><span class="sxs-lookup"><span data-stu-id="1823f-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="1823f-111">Isso pode ser útil quando você tem que copiar um registro existente e, possivelmente, alterar alguns dos valores de campo.</span><span class="sxs-lookup"><span data-stu-id="1823f-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="1823f-112">Por exemplo, um registro recém-criado.</span><span class="sxs-lookup"><span data-stu-id="1823f-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="1823f-113">Para atualizar apenas dois campos nesse registro, você pode usar a *expressão de registro de cópia e atualização:*</span><span class="sxs-lookup"><span data-stu-id="1823f-113">To update only two fields in that record you can use the *copy and update record expression*:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="1823f-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="1823f-114">See also</span></span>

- [<span data-ttu-id="1823f-115">Registros</span><span class="sxs-lookup"><span data-stu-id="1823f-115">Records</span></span>](records.md)
- [<span data-ttu-id="1823f-116">Registros Anônimos</span><span class="sxs-lookup"><span data-stu-id="1823f-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="1823f-117">Referência de idioma F#</span><span class="sxs-lookup"><span data-stu-id="1823f-117">F# Language Reference</span></span>](index.md)
