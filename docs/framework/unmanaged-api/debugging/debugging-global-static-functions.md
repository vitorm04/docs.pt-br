---
title: Depurando funções estáticas globais
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: c20d8719b63cb40074dc740506ae4a3c0fc3a251
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793776"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="12c0f-102">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="12c0f-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="12c0f-103">Esta seção descreve as funções estáticas globais não gerenciadas que a API de depuração usa.</span><span class="sxs-lookup"><span data-stu-id="12c0f-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12c0f-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="12c0f-104">In This Section</span></span>  
 [<span data-ttu-id="12c0f-105">Função _EFN_GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="12c0f-105">_EFN_GetManagedExcepStack Function</span></span>](efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="12c0f-106">Dado um endereço de objeto de exceção gerenciado, retorna uma versão de cadeia de caracteres do rastreamento de pilha contido dentro.</span><span class="sxs-lookup"><span data-stu-id="12c0f-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="12c0f-107">Função _EFN_GetManagedObjectFieldInfo</span><span class="sxs-lookup"><span data-stu-id="12c0f-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="12c0f-108">Obtém o deslocamento do início de um objeto para um campo e o valor do campo, usando o ponteiro do objeto fornecido e o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="12c0f-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="12c0f-109">Função _EFN_GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="12c0f-109">_EFN_GetManagedObjectName Function</span></span>](efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="12c0f-110">Obtém o nome de um tipo usando o ponteiro de objeto gerenciado fornecido.</span><span class="sxs-lookup"><span data-stu-id="12c0f-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="12c0f-111">Função _EFN_StackTrace</span><span class="sxs-lookup"><span data-stu-id="12c0f-111">_EFN_StackTrace Function</span></span>](efn-stacktrace-function.md)  
 <span data-ttu-id="12c0f-112">Fornece uma representação de texto de um rastreamento de pilha gerenciado e uma matriz de registros de `CONTEXT`, um para cada transição entre código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="12c0f-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="12c0f-113">Função CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="12c0f-113">CLRDataCreateInstance Function</span></span>](clrdatacreateinstance-function.md)  
 <span data-ttu-id="12c0f-114">Chamado pelos serviços de acesso a dados do Common Language Runtime (CLR) para criar o objeto de interface especificado para o processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="12c0f-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="12c0f-115">Ponteiro de função PFN_CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="12c0f-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="12c0f-116">Aponta para uma função que é chamada pelos serviços de acesso a dados do CLR para criar o objeto de interface especificado para o processo de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="12c0f-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="12c0f-117">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="12c0f-117">Related Sections</span></span>  
 [<span data-ttu-id="12c0f-118">Depurando coclasses</span><span class="sxs-lookup"><span data-stu-id="12c0f-118">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="12c0f-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="12c0f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="12c0f-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="12c0f-120">Debugging Enumerations</span></span>](debugging-enumerations.md)  
  
 [<span data-ttu-id="12c0f-121">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="12c0f-121">Debugging Structures</span></span>](debugging-structures.md)
