---
title: 'Método ICorDebugMutableDataTarget:: WriteVirtual'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 5947caa8dfb97574bb4b3c5634d962df153211c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132688"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="53a84-102">Método ICorDebugMutableDataTarget:: WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="53a84-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="53a84-103">Grava a memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="53a84-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53a84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53a84-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53a84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53a84-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="53a84-106">no O endereço no qual gravar o conteúdo de `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="53a84-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="53a84-107">no Um ponteiro para uma matriz de bytes que contém os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="53a84-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="53a84-108">no O número de bytes em `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="53a84-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53a84-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="53a84-109">Return Value</span></span>  
 <span data-ttu-id="53a84-110">`S_OK` em caso de êxito ou qualquer outro `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="53a84-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53a84-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="53a84-111">Remarks</span></span>  
 <span data-ttu-id="53a84-112">Se algum byte não puder ser gravado, a chamada do método falhará sem alterar nenhum byte no espaço de endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="53a84-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="53a84-113">(Caso contrário, o destino estaria em um estado inconsistente que torna a depuração mais não confiável.)</span><span class="sxs-lookup"><span data-stu-id="53a84-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53a84-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53a84-114">Requirements</span></span>  
 <span data-ttu-id="53a84-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53a84-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53a84-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53a84-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53a84-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53a84-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53a84-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53a84-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53a84-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53a84-119">See also</span></span>

- [<span data-ttu-id="53a84-120">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="53a84-120">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="53a84-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="53a84-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
