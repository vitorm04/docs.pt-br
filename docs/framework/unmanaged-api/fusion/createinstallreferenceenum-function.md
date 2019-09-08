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
ms.openlocfilehash: d696326ff8861ed8496474f76e9eaf89b4ead3e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795398"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="e95db-102">Função CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="e95db-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="e95db-103">Obtém um ponteiro para uma instância de [IInstallReferenceEnum](iinstallreferenceenum-interface.md) que representa uma lista de referências de um aplicativo para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="e95db-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e95db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e95db-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e95db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e95db-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="e95db-106">fora O ponteiro `IInstallReferenceEnum` retornado.</span><span class="sxs-lookup"><span data-stu-id="e95db-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="e95db-107">no O [IAssemblyName](iassemblyname-interface.md) que identifica o assembly para o qual enumerar referências.</span><span class="sxs-lookup"><span data-stu-id="e95db-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e95db-108">no Sinalizadores que influenciam o comportamento do enumerador.</span><span class="sxs-lookup"><span data-stu-id="e95db-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="e95db-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="e95db-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e95db-110">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="e95db-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e95db-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e95db-111">Requirements</span></span>  
 <span data-ttu-id="e95db-112">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e95db-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e95db-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e95db-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e95db-114">**Biblioteca** Fusion. dll e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="e95db-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="e95db-115">Use Fusion. dll em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e95db-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e95db-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e95db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95db-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e95db-117">See also</span></span>

- [<span data-ttu-id="e95db-118">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="e95db-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="e95db-119">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="e95db-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="e95db-120">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="e95db-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
