---
title: ICorDebugMergeDRecord::GetSimpleName Method
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 99ba27171e129e8725c3e0555a6991ef08b893da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178713"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="f429f-102">ICorDebugMergeDRecord::GetSimpleName Method</span><span class="sxs-lookup"><span data-stu-id="f429f-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="f429f-103">Fica com o nome simples da assembléia.</span><span class="sxs-lookup"><span data-stu-id="f429f-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f429f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f429f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f429f-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f429f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f429f-106">[em] O número de `szName` caracteres no buffer.</span><span class="sxs-lookup"><span data-stu-id="f429f-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f429f-107">[fora] Um ponteiro para o número de `szName` caracteres realmente escrito no buffer.</span><span class="sxs-lookup"><span data-stu-id="f429f-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="f429f-108">Um ponteiro para uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f429f-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f429f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f429f-109">Remarks</span></span>  
 <span data-ttu-id="f429f-110">Este método recupera o nome simples de um conjunto (como "System.Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="f429f-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="f429f-111">Corresponde à <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> propriedade em código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f429f-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f429f-112">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f429f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f429f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f429f-113">Requirements</span></span>  
 <span data-ttu-id="f429f-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f429f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f429f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f429f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f429f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f429f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f429f-117">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f429f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f429f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="f429f-118">See also</span></span>

- [<span data-ttu-id="f429f-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="f429f-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="f429f-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f429f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
