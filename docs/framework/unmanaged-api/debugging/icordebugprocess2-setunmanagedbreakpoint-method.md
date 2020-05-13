---
title: Método ICorDebugProcess2::SetUnmanagedBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 6b9396d03892f29e3698af90856d0c0023dc628a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213459"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="fea3f-102">Método ICorDebugProcess2::SetUnmanagedBreakpoint</span><span class="sxs-lookup"><span data-stu-id="fea3f-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="fea3f-103">Define um ponto de interrupção não gerenciado no deslocamento da imagem nativa especificada.</span><span class="sxs-lookup"><span data-stu-id="fea3f-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fea3f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fea3f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fea3f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fea3f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="fea3f-106">no Um `CORDB_ADDRESS` objeto que especifica o deslocamento da imagem nativa.</span><span class="sxs-lookup"><span data-stu-id="fea3f-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="fea3f-107">no O tamanho, em bytes, da `buffer` matriz.</span><span class="sxs-lookup"><span data-stu-id="fea3f-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="fea3f-108">fora Uma matriz que contém o opcode que é substituído pelo ponto de interrupção.</span><span class="sxs-lookup"><span data-stu-id="fea3f-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="fea3f-109">fora Um ponteiro para o número de bytes retornados na `buffer` matriz.</span><span class="sxs-lookup"><span data-stu-id="fea3f-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fea3f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="fea3f-110">Remarks</span></span>  
 <span data-ttu-id="fea3f-111">Se o deslocamento da imagem nativa estiver dentro do Common Language Runtime (CLR), o ponto de interrupção será ignorado.</span><span class="sxs-lookup"><span data-stu-id="fea3f-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="fea3f-112">Isso permite que o CLR Evite distribuir um ponto de interrupção fora de banda, quando o ponto de interrupção é definido pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="fea3f-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea3f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fea3f-113">Requirements</span></span>  
 <span data-ttu-id="fea3f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fea3f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fea3f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fea3f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fea3f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fea3f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fea3f-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fea3f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
