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
ms.openlocfilehash: 50ea9caf08b2ffb689760da95af4e5c3fdd77301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793734"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="66e34-102">Método ICLRDataTarget::GetMachineType</span><span class="sxs-lookup"><span data-stu-id="66e34-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="66e34-103">Obtém o identificador da espécie de conjunto de instruções que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="66e34-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e34-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66e34-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66e34-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66e34-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="66e34-106">fora Um ponteiro para um valor que indica o conjunto de instruções que o processo de destino está usando.</span><span class="sxs-lookup"><span data-stu-id="66e34-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="66e34-107">O `machineType` retornado é uma das constantes IMAGE_FILE_MACHINE, que são definidas no arquivo de cabeçalho WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="66e34-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e34-108">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="66e34-108">Requirements</span></span>  
 <span data-ttu-id="66e34-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66e34-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e34-110">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="66e34-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="66e34-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66e34-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66e34-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e34-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e34-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="66e34-113">See also</span></span>

- [<span data-ttu-id="66e34-114">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="66e34-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
