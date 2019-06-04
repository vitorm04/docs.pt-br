---
title: Função GetRealProcAddress
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40cd5b6298012ef4dc21987a2a2dbe95c02a0ff2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490357"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="85651-102">Função GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="85651-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="85651-103">Obtém o endereço da função especificada exportada da versão instalada mais recente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="85651-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="85651-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="85651-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85651-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="85651-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85651-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="85651-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="85651-107">[in] O nome da função.</span><span class="sxs-lookup"><span data-stu-id="85651-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="85651-108">[out] O local que recebe um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="85651-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85651-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="85651-109">Return Value</span></span>  
 <span data-ttu-id="85651-110">Esse método retorna códigos de erro padrão (COM Component Object Model), conforme definido em Winerror. H, além dos seguintes valores definidos no corerror.</span><span class="sxs-lookup"><span data-stu-id="85651-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="85651-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="85651-111">Return code</span></span>|<span data-ttu-id="85651-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="85651-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="85651-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="85651-113">S_OK</span></span>|<span data-ttu-id="85651-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="85651-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="85651-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="85651-115">E_POINTER</span></span>|<span data-ttu-id="85651-116">`ppv` não é válido.</span><span class="sxs-lookup"><span data-stu-id="85651-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="85651-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="85651-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="85651-118">A função não é exportada do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85651-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85651-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="85651-119">Requirements</span></span>  
 <span data-ttu-id="85651-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85651-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85651-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="85651-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="85651-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85651-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85651-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85651-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85651-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85651-124">See also</span></span>

- [<span data-ttu-id="85651-125">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="85651-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
