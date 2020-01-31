---
title: Método ICorDebugMDA::GetXML
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: cd1882bdfca1258889514a041726a59435e126b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793212"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="775de-102">Método ICorDebugMDA::GetXML</span><span class="sxs-lookup"><span data-stu-id="775de-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="775de-103">Obtém o fluxo XML completo associado ao MDA (Assistente de depuração gerenciada) representado por [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="775de-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="775de-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="775de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="775de-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="775de-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="775de-106">no O tamanho da matriz de `szName`.</span><span class="sxs-lookup"><span data-stu-id="775de-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="775de-107">fora Um ponteiro para o comprimento do fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="775de-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="775de-108">fora Uma matriz na qual armazenar o fluxo XML.</span><span class="sxs-lookup"><span data-stu-id="775de-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="775de-109">A matriz pode estar vazia.</span><span class="sxs-lookup"><span data-stu-id="775de-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="775de-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="775de-110">Remarks</span></span>  
 <span data-ttu-id="775de-111">O método `GetXML` pode potencialmente afetar o desempenho, dependendo do tamanho do fluxo XML associado.</span><span class="sxs-lookup"><span data-stu-id="775de-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="775de-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="775de-112">Requirements</span></span>  
 <span data-ttu-id="775de-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="775de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="775de-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="775de-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="775de-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="775de-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="775de-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="775de-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775de-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="775de-117">See also</span></span>

- [<span data-ttu-id="775de-118">Interface ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="775de-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="775de-119">Diagnosticando erros com Assistentes de Depuração Gerenciados</span><span class="sxs-lookup"><span data-stu-id="775de-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
