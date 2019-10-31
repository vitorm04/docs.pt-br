---
title: Método IAssemblyName::GetDisplayName
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
ms.openlocfilehash: 5dbb5dc483bc5a08c59606654d55b5a62266e509
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134375"
---
# <a name="iassemblynamegetdisplayname-method"></a><span data-ttu-id="c00c8-102">Método IAssemblyName::GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="c00c8-102">IAssemblyName::GetDisplayName Method</span></span>
<span data-ttu-id="c00c8-103">Obtém o nome legível do assembly referenciado por este objeto [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c00c8-103">Gets the human-readable name of the assembly referenced by this [IAssemblyName](iassemblyname-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c00c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c00c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c00c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c00c8-105">Parameters</span></span>  
 `szDisplayName`  
 <span data-ttu-id="c00c8-106">fora O buffer de cadeia de caracteres que contém o nome do assembly referenciado.</span><span class="sxs-lookup"><span data-stu-id="c00c8-106">[out] The string buffer that contains the name of the referenced assembly.</span></span>  
  
 `pccDisplayName`  
 <span data-ttu-id="c00c8-107">[entrada, saída] O tamanho de `szDisplayName` em caracteres largos, incluindo um caractere de terminador nulo.</span><span class="sxs-lookup"><span data-stu-id="c00c8-107">[in, out] The size of `szDisplayName` in wide characters, including a null terminator character.</span></span>  
  
 `dwDisplayFlags`  
 <span data-ttu-id="c00c8-108">no Uma combinação de bits de valores [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) que influencia os recursos de `szDisplayName`.</span><span class="sxs-lookup"><span data-stu-id="c00c8-108">[in] A bitwise combination of [ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md) values that influence the features of `szDisplayName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c00c8-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c00c8-109">Requirements</span></span>  
 <span data-ttu-id="c00c8-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c00c8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c00c8-111">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c00c8-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c00c8-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c00c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c00c8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c00c8-113">See also</span></span>

- [<span data-ttu-id="c00c8-114">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c00c8-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="c00c8-115">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="c00c8-115">Fusion Enumerations</span></span>](fusion-enumerations.md)
