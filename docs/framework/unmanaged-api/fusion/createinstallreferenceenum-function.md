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
ms.openlocfilehash: f089769f854bad5d3e572e0307734e06e72ca89c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108560"
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="86054-102">Função CreateInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="86054-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="86054-103">Obtém um ponteiro para uma instância de [IInstallReferenceEnum](iinstallreferenceenum-interface.md) que representa uma lista de referências de um aplicativo para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="86054-103">Gets a pointer to an [IInstallReferenceEnum](iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86054-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86054-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="86054-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86054-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="86054-106">fora O ponteiro de `IInstallReferenceEnum` retornado.</span><span class="sxs-lookup"><span data-stu-id="86054-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="86054-107">no O [IAssemblyName](iassemblyname-interface.md) que identifica o assembly para o qual enumerar referências.</span><span class="sxs-lookup"><span data-stu-id="86054-107">[in] The [IAssemblyName](iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="86054-108">no Sinalizadores que influenciam o comportamento do enumerador.</span><span class="sxs-lookup"><span data-stu-id="86054-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="86054-109">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="86054-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="86054-110">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="86054-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86054-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86054-111">Requirements</span></span>  
 <span data-ttu-id="86054-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86054-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86054-113">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="86054-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="86054-114">**Biblioteca:** Fusion. dll e mscorwks. dll.</span><span class="sxs-lookup"><span data-stu-id="86054-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="86054-115">Use Fusion. dll em vez de mscorwks. dll para garantir que você direcione a versão correta do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="86054-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="86054-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86054-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86054-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86054-117">See also</span></span>

- [<span data-ttu-id="86054-118">Interface IInstallReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="86054-118">IInstallReferenceEnum Interface</span></span>](iinstallreferenceenum-interface.md)
- [<span data-ttu-id="86054-119">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="86054-119">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="86054-120">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="86054-120">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
