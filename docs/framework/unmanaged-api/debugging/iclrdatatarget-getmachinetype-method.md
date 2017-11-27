---
title: "Método ICLRDataTarget::GetMachineType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetMachineType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8cd3a71d150011a1a5b9ad84c4687aac6346eb6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="d7173-102">Método ICLRDataTarget::GetMachineType</span><span class="sxs-lookup"><span data-stu-id="d7173-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="d7173-103">Obtém o identificador para o tipo de conjunto de instruções que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="d7173-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7173-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7173-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7173-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7173-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="d7173-106">[out] Um ponteiro para um valor que indica a instrução que definir o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="d7173-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="d7173-107">Retornado `machineType` é uma das constantes IMAGE_FILE_MACHINE, que são definidas no arquivo de cabeçalho Winnt. H.</span><span class="sxs-lookup"><span data-stu-id="d7173-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7173-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7173-108">Requirements</span></span>  
 <span data-ttu-id="d7173-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7173-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7173-110">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="d7173-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d7173-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7173-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7173-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7173-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7173-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7173-113">See Also</span></span>  
 [<span data-ttu-id="d7173-114">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="d7173-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
