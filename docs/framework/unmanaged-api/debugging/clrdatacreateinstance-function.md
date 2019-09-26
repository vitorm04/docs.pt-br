---
title: Função CLRDataCreateInstance
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d44f9b5dc42147959d3f1d127a64d39258f515
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274272"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="7fdf3-102">Função CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="7fdf3-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="7fdf3-103">Cria um objeto de interface para o item de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="7fdf3-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fdf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fdf3-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fdf3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fdf3-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="7fdf3-106">no O identificador da interface a ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="7fdf3-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="7fdf3-107">no Um ponteiro para um objeto [ICLRDataTarget](iclrdatatarget-interface.md) implementado pelo usuário que representa o item de destino para o qual criar o objeto de interface.</span><span class="sxs-lookup"><span data-stu-id="7fdf3-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="7fdf3-108">fora Um ponteiro para o endereço do objeto de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="7fdf3-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fdf3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fdf3-109">Remarks</span></span>  
 <span data-ttu-id="7fdf3-110">O `ICLRDataTarget` objeto é implementado pelo gravador do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="7fdf3-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="7fdf3-111">A implementação depende do tipo de item de destino que está sendo representado.</span><span class="sxs-lookup"><span data-stu-id="7fdf3-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="7fdf3-112">O item de destino pode ser um processo, despejo de memória, computador remoto e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="7fdf3-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fdf3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fdf3-113">Requirements</span></span>  
 <span data-ttu-id="7fdf3-114">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fdf3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fdf3-115">**Cabeçalho:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="7fdf3-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="7fdf3-116">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fdf3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fdf3-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fdf3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fdf3-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fdf3-118">See also</span></span>

- [<span data-ttu-id="7fdf3-119">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="7fdf3-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
