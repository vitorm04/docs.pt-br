---
title: "Depurando funções estáticas globais"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7fde0941959619f4832019806401be0ffddb81e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="6aef9-102">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="6aef9-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="6aef9-103">Esta seção descreve as funções estáticas globais não gerenciadas que usa a API de depuração.</span><span class="sxs-lookup"><span data-stu-id="6aef9-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6aef9-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="6aef9-104">In This Section</span></span>  
 [<span data-ttu-id="6aef9-105">Função _EFN_GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="6aef9-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="6aef9-106">Fornecido um endereço de objeto de exceção gerenciado, retorna uma versão de cadeia de caracteres de rastreamento de pilha contido.</span><span class="sxs-lookup"><span data-stu-id="6aef9-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="6aef9-107">Função _EFN_GetManagedObjectFieldInfo</span><span class="sxs-lookup"><span data-stu-id="6aef9-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="6aef9-108">Obtém o deslocamento do início de um objeto para um campo e o valor do campo, usando o ponteiro de objeto fornecido e o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="6aef9-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="6aef9-109">Função _EFN_GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="6aef9-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="6aef9-110">Obtém o nome de um tipo usando o ponteiro de objeto gerenciado fornecido.</span><span class="sxs-lookup"><span data-stu-id="6aef9-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="6aef9-111">Função _EFN_StackTrace</span><span class="sxs-lookup"><span data-stu-id="6aef9-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="6aef9-112">Fornece uma representação de texto de um rastreamento de pilha gerenciada e uma matriz de `CONTEXT` registra, uma para cada transição entre não gerenciados e código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6aef9-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="6aef9-113">Função CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="6aef9-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="6aef9-114">Chamado pelos common language runtime (CLR) dados serviços de acesso para criar o objeto de interface especificada para o processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="6aef9-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="6aef9-115">Ponteiro de função PFN_CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="6aef9-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="6aef9-116">Aponta para uma função que é chamado pelos dados do CLR acessar os serviços para criar o objeto de interface especificada para o processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="6aef9-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6aef9-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="6aef9-117">Related Sections</span></span>  
 [<span data-ttu-id="6aef9-118">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="6aef9-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="6aef9-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6aef9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="6aef9-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6aef9-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="6aef9-121">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="6aef9-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
