---
title: 'Método ICorDebugMergedAssemblyRecord:: getsimplesname'
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: 21e8ebeabd3b082361ca3307240cfca58835b066
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793088"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="adae4-102">Método ICorDebugMergedAssemblyRecord:: getsimplesname</span><span class="sxs-lookup"><span data-stu-id="adae4-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="adae4-103">Obtém o nome simples do assembly.</span><span class="sxs-lookup"><span data-stu-id="adae4-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adae4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adae4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adae4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="adae4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="adae4-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="adae4-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="adae4-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="adae4-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="adae4-108">Um ponteiro para uma matriz de caracteres.</span><span class="sxs-lookup"><span data-stu-id="adae4-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adae4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="adae4-109">Remarks</span></span>  
 <span data-ttu-id="adae4-110">Esse método recupera o nome simples de um assembly (como "System. Collections"), sem uma extensão de arquivo, versão, cultura ou token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="adae4-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="adae4-111">Ele corresponde à propriedade <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="adae4-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adae4-112">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="adae4-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adae4-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="adae4-113">Requirements</span></span>  
 <span data-ttu-id="adae4-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adae4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adae4-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="adae4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="adae4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adae4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adae4-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adae4-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adae4-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="adae4-118">See also</span></span>

- [<span data-ttu-id="adae4-119">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="adae4-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="adae4-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="adae4-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
