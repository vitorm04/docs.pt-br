---
title: ICorDebugMergedAssemblyRecord::GetSimpleName Method
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df142ea8f02d5cefc5c63a2d376afb331b4379ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197978"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="ea353-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span><span class="sxs-lookup"><span data-stu-id="ea353-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="ea353-103">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="ea353-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea353-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea353-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea353-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ea353-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ea353-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="ea353-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ea353-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="ea353-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ea353-108">Um ponteiro para uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ea353-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea353-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea353-109">Remarks</span></span>  
 <span data-ttu-id="ea353-110">Esse método recupera o nome simples de um assembly (por exemplo, "System. Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="ea353-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="ea353-111">Ele corresponde a <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> propriedade no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea353-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea353-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ea353-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea353-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea353-113">Requirements</span></span>  
 <span data-ttu-id="ea353-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea353-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea353-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea353-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea353-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea353-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea353-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea353-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea353-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea353-118">See also</span></span>

- [<span data-ttu-id="ea353-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="ea353-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="ea353-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ea353-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
