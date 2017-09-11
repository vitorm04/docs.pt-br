---
title: Realizando marshaling de cadeias de caracteres
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8d8455d4f1b4dbb463176c06d680b2bd0b1ff9d9
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="marshaling-strings"></a><span data-ttu-id="88602-102">Realizando marshaling de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="88602-102">Marshaling Strings</span></span>
<span data-ttu-id="88602-103">A invocação de plataforma copia parâmetros de cadeia de caracteres, convertendo-os do formato do .NET Framework (Unicode) para o formato não gerenciado (ANSI), se necessário.</span><span class="sxs-lookup"><span data-stu-id="88602-103">Platform invoke copies string parameters, converting them from the .NET Framework format (Unicode) to the unmanaged format (ANSI), if needed.</span></span> <span data-ttu-id="88602-104">Já que as cadeias de caracteres gerenciadas são imutáveis, a invocação de plataforma não as copia de volta da memória não gerenciada para a memória gerenciada quando a função retorna.</span><span class="sxs-lookup"><span data-stu-id="88602-104">Because managed strings are immutable, platform invoke does not copy them back from unmanaged memory to managed memory when the function returns.</span></span>  
  
 <span data-ttu-id="88602-105">A tabela a seguir lista as opções de marshaling para cadeias de caracteres, descreve o uso delas e fornece um link para a amostra de .NET Framework correspondente.</span><span class="sxs-lookup"><span data-stu-id="88602-105">The following table lists marshaling options for strings, describes their usage, and provides a link to the corresponding .NET Framework sample.</span></span>  
  
|<span data-ttu-id="88602-106">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="88602-106">String</span></span>|<span data-ttu-id="88602-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="88602-107">Description</span></span>|<span data-ttu-id="88602-108">Amostra</span><span class="sxs-lookup"><span data-stu-id="88602-108">Sample</span></span>|  
|------------|-----------------|------------|  
|<span data-ttu-id="88602-109">Por valor.</span><span class="sxs-lookup"><span data-stu-id="88602-109">By value.</span></span>|<span data-ttu-id="88602-110">Passa cadeias de caracteres como parâmetros In.</span><span class="sxs-lookup"><span data-stu-id="88602-110">Passes strings as In parameters.</span></span>|[<span data-ttu-id="88602-111">MsgBox</span><span class="sxs-lookup"><span data-stu-id="88602-111">MsgBox</span></span>](../../../docs/framework/interop/msgbox-sample.md)|  
|<span data-ttu-id="88602-112">Como resultado.</span><span class="sxs-lookup"><span data-stu-id="88602-112">As result.</span></span>|<span data-ttu-id="88602-113">Retorna cadeias de caracteres de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="88602-113">Returns strings from unmanaged code.</span></span>|[<span data-ttu-id="88602-114">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="88602-114">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="88602-115">Por referência.</span><span class="sxs-lookup"><span data-stu-id="88602-115">By reference.</span></span>|<span data-ttu-id="88602-116">Passa cadeias de caracteres como parâmetros In/Out usando <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="88602-116">Passes strings as In/Out parameters using <xref:System.Text.StringBuilder>.</span></span>|[<span data-ttu-id="88602-117">Buffers</span><span class="sxs-lookup"><span data-stu-id="88602-117">Buffers</span></span>](http://msdn.microsoft.com/en-us/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5)|  
|<span data-ttu-id="88602-118">Em uma estrutura por valor.</span><span class="sxs-lookup"><span data-stu-id="88602-118">In a structure by value.</span></span>|<span data-ttu-id="88602-119">Passa cadeias de caracteres em uma estrutura que é um parâmetro In.</span><span class="sxs-lookup"><span data-stu-id="88602-119">Passes strings in a structure that is an In parameter.</span></span>|[<span data-ttu-id="88602-120">Estruturas</span><span class="sxs-lookup"><span data-stu-id="88602-120">Structs</span></span>](http://msdn.microsoft.com/en-us/96a62265-dcf9-4608-bc0a-1f762ab9f48e)|  
|<span data-ttu-id="88602-121">Em uma estrutura por referência **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="88602-121">In a structure by reference **(char\*)**.</span></span>|<span data-ttu-id="88602-122">Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out.</span><span class="sxs-lookup"><span data-stu-id="88602-122">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="88602-123">A função não gerenciada espera um ponteiro para um buffer de caracteres e o tamanho do buffer é um membro da estrutura.</span><span class="sxs-lookup"><span data-stu-id="88602-123">The unmanaged function expects a pointer to a character buffer and the buffer size is a member of the structure.</span></span>|[<span data-ttu-id="88602-124">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="88602-124">Strings</span></span>](http://msdn.microsoft.com/en-us/be9e82a3-dc95-4aaa-9396-61b66e467e02)|  
|<span data-ttu-id="88602-125">Em uma estrutura por referência **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="88602-125">In a structure by reference **(char[])**.</span></span>|<span data-ttu-id="88602-126">Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out.</span><span class="sxs-lookup"><span data-stu-id="88602-126">Passes strings in a structure that is an In/Out parameter.</span></span> <span data-ttu-id="88602-127">A função não gerenciada espera um buffer de caracteres inserido.</span><span class="sxs-lookup"><span data-stu-id="88602-127">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="88602-128">OSInfo</span><span class="sxs-lookup"><span data-stu-id="88602-128">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="88602-129">Em uma classe por valor **(char\*)**.</span><span class="sxs-lookup"><span data-stu-id="88602-129">In a class by value **(char\*)**.</span></span>|<span data-ttu-id="88602-130">Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out).</span><span class="sxs-lookup"><span data-stu-id="88602-130">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="88602-131">A função não gerenciada espera um ponteiro para um buffer de caracteres.</span><span class="sxs-lookup"><span data-stu-id="88602-131">The unmanaged function expects a pointer to a character buffer.</span></span>|[<span data-ttu-id="88602-132">OpenFileDlg</span><span class="sxs-lookup"><span data-stu-id="88602-132">OpenFileDlg</span></span>](http://msdn.microsoft.com/en-us/b7dea792-cb92-4baf-ac7b-6a24803e6c75)|  
|<span data-ttu-id="88602-133">Em uma classe por valor **(char[])**.</span><span class="sxs-lookup"><span data-stu-id="88602-133">In a class by value **(char[])**.</span></span>|<span data-ttu-id="88602-134">Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out).</span><span class="sxs-lookup"><span data-stu-id="88602-134">Passes strings in a class (a class is an In/Out parameter).</span></span> <span data-ttu-id="88602-135">A função não gerenciada espera um buffer de caracteres inserido.</span><span class="sxs-lookup"><span data-stu-id="88602-135">The unmanaged function expects an embedded character buffer.</span></span>|[<span data-ttu-id="88602-136">OSInfo</span><span class="sxs-lookup"><span data-stu-id="88602-136">OSInfo</span></span>](http://msdn.microsoft.com/en-us/69d89067-507b-41fe-859d-30bf3ff29455)|  
|<span data-ttu-id="88602-137">Como uma matriz de cadeias de caracteres por valor.</span><span class="sxs-lookup"><span data-stu-id="88602-137">As an array of strings by value.</span></span>|<span data-ttu-id="88602-138">Cria uma matriz de cadeias de caracteres que é passada por valor.</span><span class="sxs-lookup"><span data-stu-id="88602-138">Creates an array of strings that is passed by value.</span></span>|[<span data-ttu-id="88602-139">Matrizes</span><span class="sxs-lookup"><span data-stu-id="88602-139">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
|<span data-ttu-id="88602-140">Como uma matriz de estruturas que contêm cadeias de caracteres por valor.</span><span class="sxs-lookup"><span data-stu-id="88602-140">As an array of structures that contain strings by value.</span></span>|<span data-ttu-id="88602-141">Cria uma matriz de estruturas que contêm cadeias de caracteres e a matriz é transmitida por valor.</span><span class="sxs-lookup"><span data-stu-id="88602-141">Creates an array of structures that contain strings and the array is passed by value.</span></span>|[<span data-ttu-id="88602-142">Matrizes</span><span class="sxs-lookup"><span data-stu-id="88602-142">Arrays</span></span>](../../../docs/framework/interop/marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a><span data-ttu-id="88602-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88602-143">See Also</span></span>  
 <span data-ttu-id="88602-144">[Marshaling de dados com a invocação de plataforma](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md) </span><span class="sxs-lookup"><span data-stu-id="88602-144">[Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md) </span></span>  
 <span data-ttu-id="88602-145">[Tipos de Dados de Invocação de Plataforma](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f) </span><span class="sxs-lookup"><span data-stu-id="88602-145">[Platform Invoke Data Types](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f) </span></span>  
 <span data-ttu-id="88602-146">[Marshaling de classes, estruturas e uniões](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md) </span><span class="sxs-lookup"><span data-stu-id="88602-146">[Marshaling Classes, Structures, and Unions](../../../docs/framework/interop/marshaling-classes-structures-and-unions.md) </span></span>  
 <span data-ttu-id="88602-147">[Marshaling de matrizes de tipos](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8) </span><span class="sxs-lookup"><span data-stu-id="88602-147">[Marshaling Arrays of Types](http://msdn.microsoft.com/en-us/049b1c1b-228f-4445-88ec-91bc7fd4b1e8) </span></span>  
 [<span data-ttu-id="88602-148">Exemplos diversos de marshaling</span><span class="sxs-lookup"><span data-stu-id="88602-148">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)

