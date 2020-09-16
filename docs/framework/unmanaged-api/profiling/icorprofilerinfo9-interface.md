---
title: Interface ICorProfilerInfo9
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f38195b1a7983e23c7f5c20055ea8c2a8bfcb7d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556844"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="a8742-102">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="a8742-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="a8742-103">Uma subclasse de [ICorProfilerInfo8](icorprofilerinfo8-interface.md) que fornece métodos para consultar informações sobre funções com várias versões de código nativo.</span><span class="sxs-lookup"><span data-stu-id="a8742-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="a8742-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a8742-104">Methods</span></span>  

| <span data-ttu-id="a8742-105">Método</span><span class="sxs-lookup"><span data-stu-id="a8742-105">Method</span></span>|<span data-ttu-id="a8742-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a8742-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="a8742-107">Método GetNativeCodeStartAddresses</span><span class="sxs-lookup"><span data-stu-id="a8742-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="a8742-108">Dada uma FunctionID e rejitId, enumera o endereço inicial do código de início de todas as versões com compilação JIT desse código que existem atualmente.</span><span class="sxs-lookup"><span data-stu-id="a8742-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="a8742-109">Método GetILToNativeMapping3</span><span class="sxs-lookup"><span data-stu-id="a8742-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="a8742-110">Dado o endereço de início do código nativo, retorna as informações de mapeamento nativo para IL para essa versão JIT do código.</span><span class="sxs-lookup"><span data-stu-id="a8742-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="a8742-111">Método GetCodeInfo4</span><span class="sxs-lookup"><span data-stu-id="a8742-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="a8742-112">Dado o endereço de início do código nativo, retorna os blocos de memória virtual que armazenam esse código.</span><span class="sxs-lookup"><span data-stu-id="a8742-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="a8742-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8742-113">Requirements</span></span>  
<span data-ttu-id="a8742-114">**Plataformas:** Consulte [sistemas operacionais com suporte do .NET Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="a8742-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="a8742-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a8742-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="a8742-116">**Versões do .net:**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8742-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a8742-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8742-117">See also</span></span>

- [<span data-ttu-id="a8742-118">Criação de perfil de interfaces</span><span class="sxs-lookup"><span data-stu-id="a8742-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
