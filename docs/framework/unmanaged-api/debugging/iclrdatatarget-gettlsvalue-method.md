---
title: Método ICLRDataTarget::GetTLSValue
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
ms.openlocfilehash: d4e7c055480ea611357d5d3e18ac4306acf4d0b0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785413"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="cda91-102">Método ICLRDataTarget::GetTLSValue</span><span class="sxs-lookup"><span data-stu-id="cda91-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="cda91-103">Obtém um valor do armazenamento local do thread (TLS) do thread especificado no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="cda91-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="cda91-104">Esse método é chamado pelos serviços de acesso a dados do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="cda91-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda91-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cda91-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cda91-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cda91-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cda91-107">no O identificador do sistema operacional de um thread no processo de destino.</span><span class="sxs-lookup"><span data-stu-id="cda91-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="cda91-108">no O índice do local.</span><span class="sxs-lookup"><span data-stu-id="cda91-108">[in] The index of the location.</span></span> <span data-ttu-id="cda91-109">Esse valor deve ser um índice válido no repositório local do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="cda91-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="cda91-110">fora Um ponteiro para um valor `CLRDATA_ADDRESS` que especifica o valor retornado do local TLS fornecido.</span><span class="sxs-lookup"><span data-stu-id="cda91-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cda91-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cda91-111">Remarks</span></span>  
 <span data-ttu-id="cda91-112">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="cda91-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda91-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cda91-113">Requirements</span></span>  
 <span data-ttu-id="cda91-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda91-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda91-115">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="cda91-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cda91-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cda91-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cda91-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda91-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda91-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="cda91-118">See also</span></span>

- [<span data-ttu-id="cda91-119">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="cda91-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
