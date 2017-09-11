---
title: "Operações básicas de cadeias de caracteres"
description: "Operações básicas de cadeias de caracteres"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 9658098d-de60-4868-ba5b-0c278748a90f
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b8bdbeccd226c412e725200fcaf81ec568afc5bc
ms.contentlocale: pt-br
ms.lasthandoff: 03/02/2017

---

# <a name="basic-string-operations"></a><span data-ttu-id="28fa7-104">Operações básicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="28fa7-104">Basic string operations</span></span>

<span data-ttu-id="28fa7-105">Muitas vezes, os aplicativos respondem aos usuários criando mensagens com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="28fa7-105">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="28fa7-106">Por exemplo, não é incomum para sites responderem a um usuário recém-conectado com uma saudação especializada que inclui o nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="28fa7-106">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="28fa7-107">Vários métodos nas classes [System.String](xref:System.String) e [System.Text.StringBuilder](xref:System.Text.StringBuilder) permitem que você construa dinamicamente cadeias de caracteres personalizadas para exibir na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="28fa7-107">Several methods in the [System.String](xref:System.String) and [System.Text.StringBuilder](xref:System.Text.StringBuilder) classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="28fa7-108">Esses métodos também ajudam a realizar várias operações de cadeias de caracteres básicas como criar novas cadeias de caracteres em matrizes de bytes, comparar os valores das cadeias de caracteres e modificar cadeias de caracteres existentes.</span><span class="sxs-lookup"><span data-stu-id="28fa7-108">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="28fa7-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="28fa7-109">In This Section</span></span>

<span data-ttu-id="28fa7-110">[Creating new strings](creating-new.md) (Criando novas cadeias de caracteres) – descreve maneiras básicas de converter objetos em cadeias de caracteres e de combinar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28fa7-110">[Creating new strings](creating-new.md) - Describes basic ways to convert objects into strings and to combine strings.</span></span>

<span data-ttu-id="28fa7-111">[Trimming and removing characters](trimming.md) (Cortando e removendo caracteres) – descreve como cortar ou remover caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28fa7-111">[Trimming and removing characters](trimming.md) - Describes how to trim or remove characters in a string.</span></span> 

<span data-ttu-id="28fa7-112">[Padding strings](padding.md) (Preenchimento de cadeias de caracteres) – descreve como inserir caracteres ou espaços vazios em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28fa7-112">[Padding strings](padding.md) - Describes how to insert characters or empty spaces into a string.</span></span>

<span data-ttu-id="28fa7-113">[Comparing strings](comparing.md) (Comparando cadeias de caracteres) – descreve como comparar o conteúdo de duas ou mais cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28fa7-113">[Comparing strings](comparing.md) - Describes how to compare the contents of two or more strings.</span></span>

<span data-ttu-id="28fa7-114">[Changing case](changing-case.md) (Alterando a definição de maiúsculas e minúsculas) – descreve como alterar a definição de maiúsculas e minúsculas dentro de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28fa7-114">[Changing case](changing-case.md) - Describes how to change the case of characters within a string.</span></span>

<span data-ttu-id="28fa7-115">[Using the StringBuilder class](stringbuilder.md) (Usando a classe StringBuilder) – descreve como criar e modificar objetos de cadeia de caracteres dinâmicos com a classe [StringBuilder](xref:System.Text.StringBuilder).</span><span class="sxs-lookup"><span data-stu-id="28fa7-115">[Using the StringBuilder class](stringbuilder.md) - Describes how to create and modify dynamic string objects with the [StringBuilder](xref:System.Text.StringBuilder) class.</span></span>

<span data-ttu-id="28fa7-116">[How to: Perform basic string manipulations](basic-manipulations.md) (Como executar manipulações de cadeias de caracteres básicas) – demonstra o uso das operações de cadeias de caracteres básicas.</span><span class="sxs-lookup"><span data-stu-id="28fa7-116">[How to: Perform basic string manipulations](basic-manipulations.md) - Demonstrates the use of basic string operations.</span></span>

## <a name="related-sections"></a><span data-ttu-id="28fa7-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="28fa7-117">Related Sections</span></span>

<span data-ttu-id="28fa7-118">[Conversão de tipo](type-conversion.md) – Descreve como converter de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="28fa7-118">[Type conversion](type-conversion.md) - Describes how to convert from one type to another.</span></span>

<span data-ttu-id="28fa7-119">[Tipos de formatação](formatting-types.md) – descreve como formatar cadeias de caracteres usando especificadores de formato de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="28fa7-119">[Formatting types](formatting-types.md) - Describes how to format strings using the string format specifiers.</span></span>



