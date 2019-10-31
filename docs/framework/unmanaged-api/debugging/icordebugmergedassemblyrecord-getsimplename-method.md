---
title: 'Método ICorDebugMergedAssemblyRecord:: getsimplesname'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 565e27b47f2454dec1e4c2b89ee46ac5279b08b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130544"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="ae4ce-102">Método ICorDebugMergedAssemblyRecord:: getsimplesname</span><span class="sxs-lookup"><span data-stu-id="ae4ce-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="ae4ce-103">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="ae4ce-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4ce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ae4ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae4ce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ae4ce-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ae4ce-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="ae4ce-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ae4ce-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="ae4ce-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ae4ce-108">Um ponteiro para uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ae4ce-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae4ce-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ae4ce-109">Remarks</span></span>  
 <span data-ttu-id="ae4ce-110">Esse método recupera o nome simples de um assembly (como "System. Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="ae4ce-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="ae4ce-111">Ele corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ae4ce-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae4ce-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ae4ce-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae4ce-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ae4ce-113">Requirements</span></span>  
 <span data-ttu-id="ae4ce-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae4ce-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae4ce-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae4ce-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae4ce-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae4ce-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae4ce-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae4ce-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4ce-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ae4ce-118">See also</span></span>

- [<span data-ttu-id="ae4ce-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="ae4ce-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="ae4ce-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ae4ce-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
