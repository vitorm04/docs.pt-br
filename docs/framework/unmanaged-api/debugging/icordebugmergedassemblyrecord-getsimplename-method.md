---
title: "Método ICorDebugMergedAssemblyRecord::GetSimpleName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0bf7bb3f52e76c34c03b322d7d6e82fa65adf8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="3c5cd-102">Método ICorDebugMergedAssemblyRecord::GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="3c5cd-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="3c5cd-103">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="3c5cd-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c5cd-104">Syntax</span></span>  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c5cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c5cd-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3c5cd-106">[in] O número de caracteres a `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="3c5cd-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3c5cd-107">[out] Um ponteiro para o número de caracteres gravados o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="3c5cd-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="3c5cd-108">Um ponteiro para uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3c5cd-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c5cd-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c5cd-109">Remarks</span></span>  
 <span data-ttu-id="3c5cd-110">Esse método retorna o nome simples de um assembly (como "System. Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="3c5cd-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="3c5cd-111">Ele corresponde do <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> propriedade em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3c5cd-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c5cd-112">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3c5cd-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c5cd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c5cd-113">Requirements</span></span>  
 <span data-ttu-id="3c5cd-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c5cd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c5cd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c5cd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c5cd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c5cd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c5cd-117">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c5cd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5cd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c5cd-118">See Also</span></span>  
 [<span data-ttu-id="3c5cd-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="3c5cd-119">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="3c5cd-120">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="3c5cd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
