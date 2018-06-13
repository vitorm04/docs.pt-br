---
title: Método ICorDebugMergedAssemblyRecord::GetSimpleName
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c5499b63e5201fbf42ece07f4f3eff52129e09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417486"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="25a43-102">Método ICorDebugMergedAssemblyRecord::GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="25a43-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="25a43-103">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="25a43-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25a43-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25a43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25a43-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="25a43-106">[in] O número de caracteres a `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="25a43-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="25a43-107">[out] Um ponteiro para o número de caracteres gravados o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="25a43-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="25a43-108">Um ponteiro para uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="25a43-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25a43-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="25a43-109">Remarks</span></span>  
 <span data-ttu-id="25a43-110">Esse método retorna o nome simples de um assembly (como "System. Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="25a43-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="25a43-111">Ele corresponde do <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> propriedade em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="25a43-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25a43-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="25a43-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25a43-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25a43-113">Requirements</span></span>  
 <span data-ttu-id="25a43-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25a43-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25a43-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25a43-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25a43-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25a43-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25a43-117">**Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25a43-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a43-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25a43-118">See Also</span></span>  
 [<span data-ttu-id="25a43-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="25a43-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="25a43-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="25a43-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
