---
title: Operações básicas de cadeias de caracteres no .NET
description: Saiba mais sobre as operações básicas que você pode executar em cadeias de caracteres.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 6ec244ab6935f4a92b0f59fa6c1cb8bc45638ce4
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889108"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="30bb3-103">Operações básicas de cadeia de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="30bb3-103">Basic string operations in .NET</span></span>

<span data-ttu-id="30bb3-104">Muitas vezes, os aplicativos respondem aos usuários criando mensagens com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="30bb3-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="30bb3-105">Por exemplo, não é incomum que sites respondam a um usuário conectado recentemente com uma saudação especializada que inclui o nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="30bb3-105">For example, it is not uncommon for websites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span>

<span data-ttu-id="30bb3-106">Vários métodos nas classes <xref:System.String?displayProperty=nameWithType> e <xref:System.Text.StringBuilder?displayProperty=nameWithType> permitem que você construa dinamicamente cadeias de caracteres personalizadas para exibir na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="30bb3-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="30bb3-107">Esses métodos também ajudam a realizar várias operações de cadeias de caracteres básicas como criar novas cadeias de caracteres em matrizes de bytes, comparar os valores das cadeias de caracteres e modificar cadeias de caracteres existentes.</span><span class="sxs-lookup"><span data-stu-id="30bb3-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="related-sections"></a><span data-ttu-id="30bb3-108">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="30bb3-108">Related sections</span></span>

<span data-ttu-id="30bb3-109">[Conversão de tipo no .NET](type-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="30bb3-109">[Type Conversion in .NET](type-conversion.md)</span></span>\
<span data-ttu-id="30bb3-110">Descreve como converter de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="30bb3-110">Describes how to convert one type into another type.</span></span>  

<span data-ttu-id="30bb3-111">[Tipos de formatação](formatting-types.md)</span><span class="sxs-lookup"><span data-stu-id="30bb3-111">[Formatting Types](formatting-types.md)</span></span>\
<span data-ttu-id="30bb3-112">Descreve como formatar cadeias de caracteres usando especificadores de formato.</span><span class="sxs-lookup"><span data-stu-id="30bb3-112">Describes how to format strings using format specifiers.</span></span>
