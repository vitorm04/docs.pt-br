---
title: Método ICorRuntimeHost::GetConfiguration
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: 88abdbc62c8b27f48c5629afb99ab6e30ee67e00
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762260"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="cf464-102">Método ICorRuntimeHost::GetConfiguration</span><span class="sxs-lookup"><span data-stu-id="cf464-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="cf464-103">Obtém um objeto que permite ao host especificar a configuração de retorno de chamada do Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="cf464-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf464-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf464-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf464-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf464-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="cf464-106">fora Um ponteiro para o endereço de um objeto [ICorConfiguration](icorconfiguration-interface.md) que pode ser usado para configurar o CLR.</span><span class="sxs-lookup"><span data-stu-id="cf464-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf464-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf464-107">Remarks</span></span>  
 <span data-ttu-id="cf464-108">O CLR deve ser configurado antes de sua inicialização; caso contrário, o `GetConfiguration` método retornará um HRESULT indicando um erro.</span><span class="sxs-lookup"><span data-stu-id="cf464-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf464-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf464-109">Requirements</span></span>  
 <span data-ttu-id="cf464-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf464-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf464-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cf464-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf464-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf464-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf464-113">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="cf464-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf464-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf464-114">See also</span></span>

- [<span data-ttu-id="cf464-115">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="cf464-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
