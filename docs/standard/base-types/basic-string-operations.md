---
title: Operações básicas de cadeias de caracteres no .NET
description: Saiba mais sobre as operações básicas que você pode executar em cadeias de caracteres.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
author: rpetrusha
ms.author: ronpet
ms.custom: seadec18
ms.openlocfilehash: 8621e79ad6e305f3859dc269965ecd216081f695
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150674"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="a62e4-103">Operações básicas de cadeias de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="a62e4-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="a62e4-104">Muitas vezes, os aplicativos respondem aos usuários criando mensagens com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="a62e4-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="a62e4-105">Por exemplo, não é incomum para sites responderem a um usuário recém-conectado com uma saudação especializada que inclui o nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="a62e4-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="a62e4-106">Vários métodos nas classes <xref:System.String?displayProperty=nameWithType> e <xref:System.Text.StringBuilder?displayProperty=nameWithType> permitem que você construa dinamicamente cadeias de caracteres personalizadas para exibir na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="a62e4-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="a62e4-107">Esses métodos também ajudam a realizar várias operações de cadeias de caracteres básicas como criar novas cadeias de caracteres em matrizes de bytes, comparar os valores das cadeias de caracteres e modificar cadeias de caracteres existentes.</span><span class="sxs-lookup"><span data-stu-id="a62e4-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a62e4-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a62e4-108">In This Section</span></span>  
 [<span data-ttu-id="a62e4-109">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="a62e4-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="a62e4-110">Descreve maneiras básicas de converter objetos em cadeias de caracteres e de combinar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a62e4-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="a62e4-111">Cortando e removendo caracteres</span><span class="sxs-lookup"><span data-stu-id="a62e4-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="a62e4-112">Descreve como cortar ou remover caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a62e4-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="a62e4-113">Preenchendo cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="a62e4-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="a62e4-114">Descreve como inserir caracteres ou espaços vazios em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a62e4-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="a62e4-115">Comparação de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="a62e4-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="a62e4-116">Descreve como comparar o conteúdo de duas ou mais cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a62e4-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="a62e4-117">Alterando a definição de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="a62e4-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="a62e4-118">Descreve como alterar a definição de maiúsculas e minúsculas dentro de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a62e4-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="a62e4-119">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="a62e4-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="a62e4-120">Descreve como criar e modificar objetos de cadeia de caracteres dinâmica usando a classe <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="a62e4-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="a62e4-121">Como executar manipulações de cadeias de caracteres básicas</span><span class="sxs-lookup"><span data-stu-id="a62e4-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="a62e4-122">Demonstra o uso das operações de cadeias de caracteres básicas.</span><span class="sxs-lookup"><span data-stu-id="a62e4-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a62e4-123">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="a62e4-123">Related Sections</span></span>  
 [<span data-ttu-id="a62e4-124">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="a62e4-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="a62e4-125">Descreve como converter de um tipo para outro.</span><span class="sxs-lookup"><span data-stu-id="a62e4-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="a62e4-126">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="a62e4-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="a62e4-127">Descreve como formatar cadeias de caracteres usando especificadores de formato.</span><span class="sxs-lookup"><span data-stu-id="a62e4-127">Describes how to format strings using format specifiers.</span></span>
