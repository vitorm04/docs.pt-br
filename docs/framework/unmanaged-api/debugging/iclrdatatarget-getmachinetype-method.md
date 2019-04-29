---
title: Método ICLRDataTarget::GetMachineType
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ff9c88d534e0bfe51075a76581af37aba791a3da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698246"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="f6098-102">Método ICLRDataTarget::GetMachineType</span><span class="sxs-lookup"><span data-stu-id="f6098-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="f6098-103">Obtém o identificador para o tipo de conjunto de instruções que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="f6098-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6098-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6098-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6098-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f6098-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="f6098-106">[out] Um ponteiro para um valor que indica que do conjunto de instruções que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="f6098-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="f6098-107">Retornado `machineType` é uma das constantes IMAGE_FILE_MACHINE, que são definidas no arquivo de cabeçalho de Winnt. H.</span><span class="sxs-lookup"><span data-stu-id="f6098-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6098-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6098-108">Requirements</span></span>  
 <span data-ttu-id="f6098-109">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6098-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6098-110">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f6098-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f6098-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6098-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6098-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6098-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6098-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6098-113">See also</span></span>

- [<span data-ttu-id="f6098-114">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="f6098-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
