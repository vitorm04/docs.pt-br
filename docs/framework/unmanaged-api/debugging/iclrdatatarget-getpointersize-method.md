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
ms.openlocfilehash: 749ec14af7bffee87afbe5c0705a6ddf68da5fd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406488"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="32a44-102">Método ICLRDataTarget::GetPointerSize</span><span class="sxs-lookup"><span data-stu-id="32a44-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="32a44-103">Obtém o tamanho, em bytes, do tipo de ponteiro que usa o processo de destino.</span><span class="sxs-lookup"><span data-stu-id="32a44-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="32a44-104">Este método é chamado pelos serviços de acesso de dados de tempo de execução linguagem comuns.</span><span class="sxs-lookup"><span data-stu-id="32a44-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32a44-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32a44-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32a44-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="32a44-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="32a44-107">[out] Um ponteiro para um valor inteiro que especifica o tamanho, em bytes, de um ponteiro no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="32a44-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32a44-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="32a44-108">Remarks</span></span>  
 <span data-ttu-id="32a44-109">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="32a44-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32a44-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32a44-110">Requirements</span></span>  
 <span data-ttu-id="32a44-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32a44-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32a44-112">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="32a44-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="32a44-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32a44-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32a44-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32a44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a44-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32a44-115">See Also</span></span>  
 [<span data-ttu-id="32a44-116">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="32a44-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
