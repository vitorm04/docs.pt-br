---
title: Método IHostSecurityManager::OpenThreadToken
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1beeb0ff6b2e3493f0814fc3371f189bd4d485d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778014"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="53e86-102">Método IHostSecurityManager::OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="53e86-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="53e86-103">Abre o token de acesso discricionário associado ao thread em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="53e86-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e86-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53e86-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53e86-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53e86-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="53e86-106">[in] Uma máscara de valores de acesso que especificam os tipos solicitados de acesso para o token de thread.</span><span class="sxs-lookup"><span data-stu-id="53e86-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="53e86-107">Esses valores são definidos no Win32 `OpenThreadToken` função.</span><span class="sxs-lookup"><span data-stu-id="53e86-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="53e86-108">Os tipos de acesso solicitado são reconciliados em relação a lista de controle de acesso discricionário (DACL) para determinar quais tipos de acesso para conceder ou negar do token.</span><span class="sxs-lookup"><span data-stu-id="53e86-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="53e86-109">[in] `true` para especificar que a verificação de acesso deve ser feita usando o contexto de segurança do processo para o thread de chamada; `false` para especificar que a verificação de acesso deve ser realizada usando o contexto de segurança para o thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="53e86-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="53e86-110">Se o thread estiver representando um cliente, o contexto de segurança pode ser de um processo do cliente.</span><span class="sxs-lookup"><span data-stu-id="53e86-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="53e86-111">[out] Um ponteiro para o token de acesso recém-aberta.</span><span class="sxs-lookup"><span data-stu-id="53e86-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53e86-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="53e86-112">Return Value</span></span>  
  
|<span data-ttu-id="53e86-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53e86-113">HRESULT</span></span>|<span data-ttu-id="53e86-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="53e86-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53e86-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="53e86-115">S_OK</span></span>|<span data-ttu-id="53e86-116">`OpenThreadToken` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="53e86-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="53e86-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53e86-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53e86-118">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="53e86-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53e86-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53e86-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53e86-120">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="53e86-120">The call timed out.</span></span>|  
|<span data-ttu-id="53e86-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53e86-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53e86-122">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="53e86-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53e86-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53e86-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53e86-124">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="53e86-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53e86-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53e86-125">E_FAIL</span></span>|<span data-ttu-id="53e86-126">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="53e86-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53e86-127">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="53e86-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53e86-128">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="53e86-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e86-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="53e86-129">Remarks</span></span>  
 <span data-ttu-id="53e86-130">`IHostSecurityManager::OpenThreadToken` se comporta da mesma forma para a função Win32 correspondente de mesmo nome, exceto que a função Win32 permite que o chamador passe um identificador para um thread arbitrário, enquanto `IHostSecurityManager::OpenThreadToken` abre apenas o token associado com o thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="53e86-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="53e86-131">O `HANDLE` tipo não é compatível com, ou seja, seu tamanho é específico para o sistema operacional e ela requer o marshaling personalizado.</span><span class="sxs-lookup"><span data-stu-id="53e86-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="53e86-132">Portanto, esse token é para uso somente dentro do processo, entre o CLR e o host.</span><span class="sxs-lookup"><span data-stu-id="53e86-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53e86-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53e86-133">Requirements</span></span>  
 <span data-ttu-id="53e86-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e86-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e86-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="53e86-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53e86-136">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="53e86-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53e86-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53e86-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e86-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53e86-138">See also</span></span>

- [<span data-ttu-id="53e86-139">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="53e86-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="53e86-140">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="53e86-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
