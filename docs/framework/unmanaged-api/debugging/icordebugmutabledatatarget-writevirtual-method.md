---
title: 'Método ICorDebugMutableDataTarget:: WriteVirtual'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 2b4bd1dc97f37f5a514ab54f9e4d778fe3b91736
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792828"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a><span data-ttu-id="962c5-102">Método ICorDebugMutableDataTarget:: WriteVirtual</span><span class="sxs-lookup"><span data-stu-id="962c5-102">ICorDebugMutableDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="962c5-103">Grava a memória no espaço de endereço do processo de destino.</span><span class="sxs-lookup"><span data-stu-id="962c5-103">Writes memory into the target process address space.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="962c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="962c5-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a><span data-ttu-id="962c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="962c5-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="962c5-106">no O endereço no qual gravar o conteúdo de `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="962c5-106">[in] The address at which to write the contents of `pBuffer`.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="962c5-107">no Um ponteiro para uma matriz de bytes que contém os bytes a serem gravados.</span><span class="sxs-lookup"><span data-stu-id="962c5-107">[in] A pointer to a byte array that contains the bytes to be written.</span></span>  
  
 `address`  
 <span data-ttu-id="962c5-108">no O número de bytes em `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="962c5-108">[in] The number of bytes in `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="962c5-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="962c5-109">Return Value</span></span>  
 <span data-ttu-id="962c5-110">`S_OK` em caso de êxito ou qualquer outro `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="962c5-110">`S_OK` on success, or any other `HRESULT` on failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="962c5-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="962c5-111">Remarks</span></span>  
 <span data-ttu-id="962c5-112">Se algum byte não puder ser gravado, a chamada do método falhará sem alterar nenhum byte no espaço de endereço de destino.</span><span class="sxs-lookup"><span data-stu-id="962c5-112">If any bytes cannot be written, the method call fails without changing any bytes in the target address space.</span></span> <span data-ttu-id="962c5-113">(Caso contrário, o destino estaria em um estado inconsistente que torna a depuração mais não confiável.)</span><span class="sxs-lookup"><span data-stu-id="962c5-113">(Otherwise, the target would be in an inconsistent state that makes further debugging unreliable.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="962c5-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="962c5-114">Requirements</span></span>  
 <span data-ttu-id="962c5-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="962c5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="962c5-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="962c5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="962c5-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="962c5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="962c5-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="962c5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962c5-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="962c5-119">See also</span></span>

- [<span data-ttu-id="962c5-120">Interface ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="962c5-120">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="962c5-121">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="962c5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
