---
title: Método ICLRDataTarget::GetPointerSize
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54abcd357c6f26f54432b39bfcb4a0d63afabfe4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738718"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="8de3b-102">Método ICLRDataTarget::GetPointerSize</span><span class="sxs-lookup"><span data-stu-id="8de3b-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="8de3b-103">Obtém o tamanho, em bytes, do tipo de ponteiro que usa o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="8de3b-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="8de3b-104">Esse método é chamado pelo serviço de acesso de dados do common language runtime.</span><span class="sxs-lookup"><span data-stu-id="8de3b-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8de3b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8de3b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8de3b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8de3b-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="8de3b-107">[out] Um ponteiro para um valor inteiro que especifica o tamanho, em bytes, de um ponteiro no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="8de3b-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8de3b-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="8de3b-108">Remarks</span></span>  
 <span data-ttu-id="8de3b-109">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="8de3b-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8de3b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8de3b-110">Requirements</span></span>  
 <span data-ttu-id="8de3b-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8de3b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8de3b-112">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8de3b-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8de3b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8de3b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8de3b-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8de3b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de3b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8de3b-115">See also</span></span>

- [<span data-ttu-id="8de3b-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="8de3b-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
