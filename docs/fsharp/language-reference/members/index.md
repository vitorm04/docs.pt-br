---
title: Membros (F#)
description: "Saiba mais sobre os membros de objeto em F # linguagem de programação."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="members"></a><span data-ttu-id="d7685-104">Membros</span><span class="sxs-lookup"><span data-stu-id="d7685-104">Members</span></span>

<span data-ttu-id="d7685-105">Esta seção descreve os membros dos tipos de objeto do F#.</span><span class="sxs-lookup"><span data-stu-id="d7685-105">This section describes members of F# object types.</span></span>


## <a name="remarks"></a><span data-ttu-id="d7685-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7685-106">Remarks</span></span>
<span data-ttu-id="d7685-107">*Membros* são recursos que fazem parte de uma definição de tipo e são declarados com a palavra-chave `member`.</span><span class="sxs-lookup"><span data-stu-id="d7685-107">*Members* are features that are part of a type definition and are declared with the `member` keyword.</span></span> <span data-ttu-id="d7685-108">Tipos de objeto F# como registros, classes, uniões discriminadas, interfaces e membros de suporte às estruturas.</span><span class="sxs-lookup"><span data-stu-id="d7685-108">F# object types such as records, classes, discriminated unions, interfaces, and structures support members.</span></span> <span data-ttu-id="d7685-109">Para saber mais, veja [Registros](../records.md), [Classes](../classes.md), [Uniões discriminada](../discriminated-Unions.md), [Interfaces](../interfaces.md) e [estruturas](../structures.md).</span><span class="sxs-lookup"><span data-stu-id="d7685-109">For more information, see [Records](../records.md), [Classes](../classes.md), [Discriminated Unions](../discriminated-Unions.md), [Interfaces](../interfaces.md), and [Structures](../structures.md).</span></span>

<span data-ttu-id="d7685-110">Os membros normalmente compõem a interface pública de um tipo e, por isso, são públicos, a menos que o contrário seja especificado.</span><span class="sxs-lookup"><span data-stu-id="d7685-110">Members typically make up the public interface for a type, which is why they are public unless otherwise specified.</span></span> <span data-ttu-id="d7685-111">Os membros também podem ser declarados particular ou internamente.</span><span class="sxs-lookup"><span data-stu-id="d7685-111">Members can also be declared private or internal.</span></span> <span data-ttu-id="d7685-112">Para saber mais, veja [Controle de acesso](../access-Control.md).</span><span class="sxs-lookup"><span data-stu-id="d7685-112">For more information, see [Access Control](../access-Control.md).</span></span> <span data-ttu-id="d7685-113">As assinaturas para tipos também podem ser usadas para expor ou não certos membros de um tipo.</span><span class="sxs-lookup"><span data-stu-id="d7685-113">Signatures for types can also be used to expose or not expose certain members of a type.</span></span> <span data-ttu-id="d7685-114">Para saber mais, confira [Assinaturas](../signatures.md).</span><span class="sxs-lookup"><span data-stu-id="d7685-114">For more information, see [Signatures](../signatures.md).</span></span>

<span data-ttu-id="d7685-115">Campos particulares e associações `do`, usados apenas com classes, não são membros reais, pois não fazem parte da interface pública de um tipo e não são declarados com a palavra-chave `member`, mas estão descritos nesta seção também.</span><span class="sxs-lookup"><span data-stu-id="d7685-115">Private fields and `do` bindings, which are used only with classes, are not true members, because they are never part of the public interface of a type and are not declared with the `member` keyword, but they are described in this section also.</span></span>


## <a name="related-topics"></a><span data-ttu-id="d7685-116">Tópicos relacionados</span><span class="sxs-lookup"><span data-stu-id="d7685-116">Related Topics</span></span>


|<span data-ttu-id="d7685-117">Tópico</span><span class="sxs-lookup"><span data-stu-id="d7685-117">Topic</span></span>|<span data-ttu-id="d7685-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7685-118">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="d7685-119">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="d7685-119">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)|<span data-ttu-id="d7685-120">Descreve a definição de campos particulares e funções em classes.</span><span class="sxs-lookup"><span data-stu-id="d7685-120">Describes the definition of private fields and functions in classes.</span></span>|
|[<span data-ttu-id="d7685-121">`do`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="d7685-121">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)|<span data-ttu-id="d7685-122">Descreve a especificação do código de inicialização de objeto.</span><span class="sxs-lookup"><span data-stu-id="d7685-122">Describes the specification of object initialization code.</span></span>|
|[<span data-ttu-id="d7685-123">Propriedades</span><span class="sxs-lookup"><span data-stu-id="d7685-123">Properties</span></span>](properties.md)|<span data-ttu-id="d7685-124">Descreve os membros da propriedade em classes e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="d7685-124">Describes property members in classes and other types.</span></span>|
|[<span data-ttu-id="d7685-125">Propriedades Indexadas</span><span class="sxs-lookup"><span data-stu-id="d7685-125">Indexed Properties</span></span>](indexed-properties.md)|<span data-ttu-id="d7685-126">Descreve propriedade do tipo matriz em classes e outros tipos.</span><span class="sxs-lookup"><span data-stu-id="d7685-126">Describes array-like properties in classes and other types.</span></span>|
|[<span data-ttu-id="d7685-127">Métodos</span><span class="sxs-lookup"><span data-stu-id="d7685-127">Methods</span></span>](methods.md)|<span data-ttu-id="d7685-128">Descreve as funções que são membros de um tipo.</span><span class="sxs-lookup"><span data-stu-id="d7685-128">Describes functions that are members of a type.</span></span>|
|[<span data-ttu-id="d7685-129">Construtores</span><span class="sxs-lookup"><span data-stu-id="d7685-129">Constructors</span></span>](constructors.md)|<span data-ttu-id="d7685-130">Descreve funções especiais que inicializam objetos de um tipo.</span><span class="sxs-lookup"><span data-stu-id="d7685-130">Describes special functions that initialize objects of a type.</span></span>|
|[<span data-ttu-id="d7685-131">Sobrecarga de Operador</span><span class="sxs-lookup"><span data-stu-id="d7685-131">Operator Overloading</span></span>](../operator-overloading.md)|<span data-ttu-id="d7685-132">Descreve a definição dos operadores personalizados para os tipos.</span><span class="sxs-lookup"><span data-stu-id="d7685-132">Describes the definition of customized operators for types.</span></span>|
|[<span data-ttu-id="d7685-133">Eventos</span><span class="sxs-lookup"><span data-stu-id="d7685-133">Events</span></span>](events.md)|<span data-ttu-id="d7685-134">Descreve a definição de eventos e suporte de manipulação de eventos em F#.</span><span class="sxs-lookup"><span data-stu-id="d7685-134">Describes the definition of events and event handling support in F#.</span></span>|
|[<span data-ttu-id="d7685-135">Campos Explícitos: a `val` Palavra-Chave</span><span class="sxs-lookup"><span data-stu-id="d7685-135">Explicit Fields: The `val` Keyword</span></span>](explicit-fields-the-val-keyword.md)|<span data-ttu-id="d7685-136">Descreve a definição dos campos não inicializados em um tipo.</span><span class="sxs-lookup"><span data-stu-id="d7685-136">Describes the definition of uninitialized fields in a type.</span></span>|
