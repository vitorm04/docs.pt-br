---
title: Operações básicas de cadeias de caracteres no .NET
description: Saiba mais sobre as operações básicas que você pode executar em cadeias de caracteres.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 2ce1b148a2b1605b5b1283bdc3398409661f3f83
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523982"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="7c19f-103">Operações básicas de string em .NET</span><span class="sxs-lookup"><span data-stu-id="7c19f-103">Basic string operations in .NET</span></span>

<span data-ttu-id="7c19f-104">Muitas vezes, os aplicativos respondem aos usuários criando mensagens com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="7c19f-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="7c19f-105">Por exemplo, não é incomum que sites respondam a um usuário recém-conectado com uma saudação especializada que inclua o nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="7c19f-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="7c19f-106">Vários métodos nas classes <xref:System.String?displayProperty=nameWithType> e <xref:System.Text.StringBuilder?displayProperty=nameWithType> permitem que você construa dinamicamente cadeias de caracteres personalizadas para exibir na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7c19f-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="7c19f-107">Esses métodos também ajudam a realizar várias operações de cadeias de caracteres básicas como criar novas cadeias de caracteres em matrizes de bytes, comparar os valores das cadeias de caracteres e modificar cadeias de caracteres existentes.</span><span class="sxs-lookup"><span data-stu-id="7c19f-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7c19f-108">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7c19f-108">Related sections</span></span>

<span data-ttu-id="7c19f-109">[Conversão de tipo em .NET](../../../docs/standard/base-types/type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="7c19f-109">[Type Conversion in .NET](../../../docs/standard/base-types/type-conversion.md)</span></span>\
<span data-ttu-id="7c19f-110">Descreve como converter de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="7c19f-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="7c19f-111">[Tipos de formatação](../../../docs/standard/base-types/formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="7c19f-111">[Formatting Types](../../../docs/standard/base-types/formatting-types.md)</span></span>\
<span data-ttu-id="7c19f-112">Descreve como formatar cadeias de caracteres usando especificadores de formato.</span><span class="sxs-lookup"><span data-stu-id="7c19f-112">Describes how to format strings using format specifiers.</span></span>
