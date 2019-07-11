---
title: Função CreateInstallReferenceEnum
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da77d2eb848419c35e57ffacc8bf3d4580106fa5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764331"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="86613-102">Função CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="86613-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="86613-103">Obtém um ponteiro para um [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instância que representa uma lista de referências de um aplicativo para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="86613-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86613-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86613-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="86613-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86613-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="86613-106">[out] Retornado `IInstallReferenceEnum` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="86613-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="86613-107">[in] O [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) que identifica o assembly para o qual enumerar referências.</span><span class="sxs-lookup"><span data-stu-id="86613-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="86613-108">[in] Sinalizadores que influenciam o comportamento do enumerador.</span><span class="sxs-lookup"><span data-stu-id="86613-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="86613-109">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="86613-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="86613-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="86613-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86613-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86613-111">Requirements</span></span>  
 <span data-ttu-id="86613-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86613-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86613-113">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="86613-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="86613-114">**Biblioteca:** Fusion e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="86613-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="86613-115">Use Fusion em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86613-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="86613-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86613-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86613-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86613-117">See also</span></span>

- [<span data-ttu-id="86613-118">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="86613-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
- [<span data-ttu-id="86613-119">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="86613-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="86613-120">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="86613-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
