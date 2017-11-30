---
title: "Operações básicas de cadeias de caracteres no .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f241b99f97cad081a65fd8654169e444a1b588cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="92983-102">Operações básicas de cadeia de caracteres no .NET</span><span class="sxs-lookup"><span data-stu-id="92983-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="92983-103">Muitas vezes, os aplicativos respondem aos usuários criando mensagens com base na entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="92983-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="92983-104">Por exemplo, não é incomum para sites responderem a um usuário recém-conectado com uma saudação especializada que inclui o nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="92983-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="92983-105">Vários métodos de <xref:System.String?displayProperty=nameWithType> e <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes permitem que você construa dinamicamente as cadeias de caracteres personalizadas para exibir na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="92983-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="92983-106">Esses métodos também ajudam a realizar várias operações de cadeias de caracteres básicas como criar novas cadeias de caracteres em matrizes de bytes, comparar os valores das cadeias de caracteres e modificar cadeias de caracteres existentes.</span><span class="sxs-lookup"><span data-stu-id="92983-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92983-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="92983-107">In This Section</span></span>  
 [<span data-ttu-id="92983-108">Criando novas cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="92983-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="92983-109">Descreve maneiras básicas para converter objetos em cadeias de caracteres e combinar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92983-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="92983-110">Cortando e removendo caracteres</span><span class="sxs-lookup"><span data-stu-id="92983-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="92983-111">Descreve como cortar ou remover caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92983-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="92983-112">Preenchendo cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="92983-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="92983-113">Descreve como inserir caracteres ou espaços vazios em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92983-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="92983-114">Comparação de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="92983-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="92983-115">Descreve como comparar o conteúdo de duas ou mais cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92983-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="92983-116">Alterando a definição de maiúsculas e minúsculas</span><span class="sxs-lookup"><span data-stu-id="92983-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="92983-117">Descreve como alterar o caso de caracteres em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92983-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="92983-118">Uso da classe StringBuilder</span><span class="sxs-lookup"><span data-stu-id="92983-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="92983-119">Descreve como criar e modificar objetos de cadeia de caracteres dinâmica com o <xref:System.Text.StringBuilder> classe.</span><span class="sxs-lookup"><span data-stu-id="92983-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="92983-120">Como executar manipulações de cadeias de caracteres básicas</span><span class="sxs-lookup"><span data-stu-id="92983-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="92983-121">Demonstra o uso das operações básicas de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="92983-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="92983-122">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="92983-122">Related Sections</span></span>  
 [<span data-ttu-id="92983-123">Conversão de tipo no .NET</span><span class="sxs-lookup"><span data-stu-id="92983-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="92983-124">Descreve como converter um tipo em outro tipo.</span><span class="sxs-lookup"><span data-stu-id="92983-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="92983-125">Formatando Tipos</span><span class="sxs-lookup"><span data-stu-id="92983-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="92983-126">Descreve como formatar cadeias de caracteres usando especificadores de formato.</span><span class="sxs-lookup"><span data-stu-id="92983-126">Describes how to format strings using format specifiers.</span></span>
