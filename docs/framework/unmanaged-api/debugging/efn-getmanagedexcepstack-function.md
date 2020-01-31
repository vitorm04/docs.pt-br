---
title: Função _EFN_GetManagedExcepStack
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
ms.openlocfilehash: 824be4a401d265575b48f66045dd944d521e64a4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789149"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="ca2d8-102">Função \_EFN\_GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="ca2d8-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="ca2d8-103">Dado um endereço de objeto de exceção gerenciado, retorna uma versão de cadeia de caracteres do rastreamento de pilha contido dentro.</span><span class="sxs-lookup"><span data-stu-id="ca2d8-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca2d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca2d8-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca2d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca2d8-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="ca2d8-106">no O cliente que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="ca2d8-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="ca2d8-107">no Um ponteiro de objeto gerenciado, derivado de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="ca2d8-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="ca2d8-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="ca2d8-108">szStackString</span></span>  
 <span data-ttu-id="ca2d8-109">fora A cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="ca2d8-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="ca2d8-110">fora O número de caracteres disponíveis no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca2d8-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca2d8-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca2d8-111">Remarks</span></span>  
 <span data-ttu-id="ca2d8-112">Se não houver nenhum código gerenciado no thread atualmente no contexto, a função retornará HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0XA0 e um código de erro de 0x1000.</span><span class="sxs-lookup"><span data-stu-id="ca2d8-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca2d8-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ca2d8-113">Requirements</span></span>  
 <span data-ttu-id="ca2d8-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca2d8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca2d8-115">**Cabeçalho:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="ca2d8-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="ca2d8-116">**Versão do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca2d8-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca2d8-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="ca2d8-117">See also</span></span>

- [<span data-ttu-id="ca2d8-118">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="ca2d8-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
