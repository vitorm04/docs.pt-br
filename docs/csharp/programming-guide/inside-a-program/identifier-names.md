---
title: Nomes de identificadores
description: Conheça as regras para nomes de identificador válidos na linguagem de programação C#.
ms.date: 08/21/2018
ms.openlocfilehash: f8a27ddae0437ed037b59f76d60dc7e420ddc2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589346"
---
# <a name="identifier-names"></a><span data-ttu-id="29b7e-103">Nomes de identificadores</span><span class="sxs-lookup"><span data-stu-id="29b7e-103">Identifier names</span></span>

<span data-ttu-id="29b7e-104">Um **identificador** é o nome que você atribui a um tipo (classe, interface, struct, delegado ou enumerado), membro, variável ou namespace.</span><span class="sxs-lookup"><span data-stu-id="29b7e-104">An **identifier** is the name you assign to a type (class, interface, struct, delegate, or enum), member, variable, or namespace.</span></span> <span data-ttu-id="29b7e-105">Os identificadores válidos devem seguir estas regras:</span><span class="sxs-lookup"><span data-stu-id="29b7e-105">Valid identifiers must follow these rules:</span></span>

- <span data-ttu-id="29b7e-106">Os identificadores devem começar com uma letra ou `_`.</span><span class="sxs-lookup"><span data-stu-id="29b7e-106">Identifiers must start with a letter, or `_`.</span></span>
- <span data-ttu-id="29b7e-107">Os identificadores podem conter caracteres de letra Unicode, caracteres de dígito decimal, caracteres de conexão Unicode, caracteres de combinação Unicode ou caracteres de formatação Unicode.</span><span class="sxs-lookup"><span data-stu-id="29b7e-107">Identifiers may contain Unicode letter characters, decimal digit characters, Unicode connecting characters, Unicode combining characters, or Unicode formatting characters.</span></span> <span data-ttu-id="29b7e-108">Para obter mais informações sobre as categorias Unicode, consulte o [Banco de dados da categoria Unicode](https://www.unicode.org/reports/tr44/).</span><span class="sxs-lookup"><span data-stu-id="29b7e-108">For more information on Unicode categories, see the [Unicode Category Database](https://www.unicode.org/reports/tr44/).</span></span>
<span data-ttu-id="29b7e-109">É possível declarar identificadores que correspondem às palavras-chave em C# usando o prefixo `@` no identificador.</span><span class="sxs-lookup"><span data-stu-id="29b7e-109">You can declare identifiers that match C# keywords by using the `@` prefix on the identifier.</span></span> <span data-ttu-id="29b7e-110">O `@` não faz parte do nome do identificador.</span><span class="sxs-lookup"><span data-stu-id="29b7e-110">The `@` is not part of the identifier name.</span></span> <span data-ttu-id="29b7e-111">Por exemplo, `@if` declara um identificador chamado `if`.</span><span class="sxs-lookup"><span data-stu-id="29b7e-111">For example, `@if` declares an identifier named `if`.</span></span> <span data-ttu-id="29b7e-112">Esses [identificadores textuais](../../language-reference/tokens/verbatim.md) são destinados principalmente para interoperabilidade com os identificadores declarados em outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="29b7e-112">These [verbatim identifiers](../../language-reference/tokens/verbatim.md) are primarily for interoperability with identifiers declared in other languages.</span></span>

<span data-ttu-id="29b7e-113">Para obter uma definição completa de identificadores válidos, consulte o [tópico de identificadores na especificação da linguagem C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span><span class="sxs-lookup"><span data-stu-id="29b7e-113">For a complete definition of valid identifiers, see the [Identifiers topic in the C# Language Specification](../../../../_csharplang/spec/lexical-structure.md#identifiers).</span></span>

## <a name="naming-conventions"></a><span data-ttu-id="29b7e-114">Convenções de nomenclatura</span><span class="sxs-lookup"><span data-stu-id="29b7e-114">Naming conventions</span></span>

<span data-ttu-id="29b7e-115">Além das regras, há inúmeras [convenções de nomenclatura](../../../standard/design-guidelines/naming-guidelines.md) de identificador usadas em toda as APIs do .NET.</span><span class="sxs-lookup"><span data-stu-id="29b7e-115">In addition to the rules, there are a number of identifier [naming conventions](../../../standard/design-guidelines/naming-guidelines.md) used throughout the .NET APIs.</span></span> <span data-ttu-id="29b7e-116">Por convenção, os programas C# usam `PascalCase` para nomes de tipo, namespaces e todos os membros públicos.</span><span class="sxs-lookup"><span data-stu-id="29b7e-116">By convention, C# programs use `PascalCase` for type names, namespaces, and all public members.</span></span> <span data-ttu-id="29b7e-117">Além disso, as seguintes convenções são comuns:</span><span class="sxs-lookup"><span data-stu-id="29b7e-117">In addition, the following conventions are common:</span></span>

- <span data-ttu-id="29b7e-118">Os nomes de interface começam com `I` maiúsculo.</span><span class="sxs-lookup"><span data-stu-id="29b7e-118">Interface names start with a capital `I`.</span></span>
- <span data-ttu-id="29b7e-119">Os tipos de atributo terminam com a palavra `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="29b7e-119">Attribute types end with the word `Attribute`.</span></span>
- <span data-ttu-id="29b7e-120">Os tipos enumerados usam um substantivo singular para não sinalizadores e um substantivo plural para sinalizadores.</span><span class="sxs-lookup"><span data-stu-id="29b7e-120">Enum types use a singular noun for non-flags, and a plural noun for flags.</span></span>
- <span data-ttu-id="29b7e-121">Os identificadores não devem conter dois caracteres `_` consecutivos.</span><span class="sxs-lookup"><span data-stu-id="29b7e-121">Identifiers should not contain two consecutive `_` characters.</span></span> <span data-ttu-id="29b7e-122">Esses nomes estão reservados para identificadores gerados por compilador.</span><span class="sxs-lookup"><span data-stu-id="29b7e-122">Those names are reserved for compiler generated identifiers.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="29b7e-123">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="29b7e-123">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29b7e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29b7e-124">See also</span></span>

- [<span data-ttu-id="29b7e-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="29b7e-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="29b7e-126">Por dentro de um programa em C#</span><span class="sxs-lookup"><span data-stu-id="29b7e-126">Inside a C# Program</span></span>](./index.md)
- [<span data-ttu-id="29b7e-127">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="29b7e-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="29b7e-128">Classes</span><span class="sxs-lookup"><span data-stu-id="29b7e-128">Classes</span></span>](../classes-and-structs/classes.md)
- [<span data-ttu-id="29b7e-129">Estruturas</span><span class="sxs-lookup"><span data-stu-id="29b7e-129">Structs</span></span>](../classes-and-structs/structs.md)
- [<span data-ttu-id="29b7e-130">Namespaces</span><span class="sxs-lookup"><span data-stu-id="29b7e-130">Namespaces</span></span>](../namespaces/index.md)
- [<span data-ttu-id="29b7e-131">Interfaces</span><span class="sxs-lookup"><span data-stu-id="29b7e-131">Interfaces</span></span>](../interfaces/index.md)
- [<span data-ttu-id="29b7e-132">Delegados</span><span class="sxs-lookup"><span data-stu-id="29b7e-132">Delegates</span></span>](../delegates/index.md)
