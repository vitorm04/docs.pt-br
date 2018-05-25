---
title: Chamando uma função de DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98d363b6c0838ff1211d969391f04ce8ccddd003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="770c3-102">Chamando uma função de DLL</span><span class="sxs-lookup"><span data-stu-id="770c3-102">Calling a DLL Function</span></span>
<span data-ttu-id="770c3-103">Embora a chamada a funções de DLL não gerenciadas seja quase idêntica à chamada de outro código gerenciado, há diferenças que podem fazer com que as funções de DLL pareçam confusas a princípio.</span><span class="sxs-lookup"><span data-stu-id="770c3-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="770c3-104">Esta seção apresenta tópicos que descrevem alguns dos problemas incomuns relacionados a chamadas.</span><span class="sxs-lookup"><span data-stu-id="770c3-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="770c3-105">Estruturas retornadas de chamadas de invocação de plataforma devem ser tipos de dados que têm a mesma representação em um código gerenciado e não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="770c3-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="770c3-106">Esses tipos são chamados de *tipos blittable* porque não exigem conversão (consulte [Tipos blittable e não blittable](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="770c3-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="770c3-107">Para chamar uma função que tem uma estrutura não blittable como seu tipo de retorno, é possível definir um tipo de auxiliar blittable do mesmo tamanho do tipo não blittable e converter os dados depois que a função é retornada.</span><span class="sxs-lookup"><span data-stu-id="770c3-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="770c3-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="770c3-108">In This Section</span></span>  
 [<span data-ttu-id="770c3-109">Passando estruturas</span><span class="sxs-lookup"><span data-stu-id="770c3-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="770c3-110">Identifica os problemas de passar estruturas de dados com um layout predefinido.</span><span class="sxs-lookup"><span data-stu-id="770c3-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="770c3-111">Funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="770c3-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="770c3-112">Fornece informações básicas sobre as funções de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="770c3-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="770c3-113">Como implementar funções de retorno de chamada</span><span class="sxs-lookup"><span data-stu-id="770c3-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="770c3-114">Descreve como implementar funções de retorno de chamada em um código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="770c3-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="770c3-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="770c3-115">Related Sections</span></span>  
 [<span data-ttu-id="770c3-116">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="770c3-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="770c3-117">Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="770c3-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="770c3-118">Marshaling de dados com a invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="770c3-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="770c3-119">Descreve como declarar parâmetros de método e passar argumentos para funções exportadas por bibliotecas não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="770c3-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
