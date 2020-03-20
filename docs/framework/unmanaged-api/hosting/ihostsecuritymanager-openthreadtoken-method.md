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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176260"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="555cf-102">Método IHostSecurityManager::OpenThreadToken</span><span class="sxs-lookup"><span data-stu-id="555cf-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="555cf-103">Abre o token de acesso discricionário associado ao segmento de execução atualmente.</span><span class="sxs-lookup"><span data-stu-id="555cf-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="555cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="555cf-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="555cf-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="555cf-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="555cf-106">[em] Uma máscara de valores de acesso que especificam os tipos de acesso solicitados ao token de segmento.</span><span class="sxs-lookup"><span data-stu-id="555cf-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="555cf-107">Esses valores são definidos `OpenThreadToken` na função Win32.</span><span class="sxs-lookup"><span data-stu-id="555cf-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="555cf-108">Os tipos de acesso solicitados são conciliados com a lista de controle de acesso discricionário (DACL) do token para determinar quais tipos de acesso conceder ou negar.</span><span class="sxs-lookup"><span data-stu-id="555cf-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="555cf-109">[em] `true` especificar que a verificação de acesso deve ser feita usando o contexto de segurança do processo para o segmento de chamada; `false` para especificar que a verificação de acesso deve ser realizada usando o contexto de segurança do próprio segmento de chamada.</span><span class="sxs-lookup"><span data-stu-id="555cf-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="555cf-110">Se o segmento está se passando por um cliente, o contexto de segurança pode ser o de um processo de cliente.</span><span class="sxs-lookup"><span data-stu-id="555cf-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="555cf-111">[fora] Um ponteiro para o token de acesso recém-aberto.</span><span class="sxs-lookup"><span data-stu-id="555cf-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="555cf-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="555cf-112">Return Value</span></span>  
  
|<span data-ttu-id="555cf-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="555cf-113">HRESULT</span></span>|<span data-ttu-id="555cf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="555cf-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="555cf-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="555cf-115">S_OK</span></span>|<span data-ttu-id="555cf-116">`OpenThreadToken`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="555cf-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="555cf-117">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="555cf-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="555cf-118">O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="555cf-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="555cf-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="555cf-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="555cf-120">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="555cf-120">The call timed out.</span></span>|  
|<span data-ttu-id="555cf-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="555cf-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="555cf-122">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="555cf-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="555cf-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="555cf-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="555cf-124">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="555cf-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="555cf-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="555cf-125">E_FAIL</span></span>|<span data-ttu-id="555cf-126">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="555cf-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="555cf-127">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="555cf-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="555cf-128">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="555cf-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="555cf-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="555cf-129">Remarks</span></span>  
 <span data-ttu-id="555cf-130">`IHostSecurityManager::OpenThreadToken`comporta-se de forma semelhante à função Win32 correspondente de mesmo nome, exceto que a função Win32 `IHostSecurityManager::OpenThreadToken` permite que o chamador passe em uma alça para um segmento arbitrário, enquanto abre apenas o token associado ao segmento de chamada.</span><span class="sxs-lookup"><span data-stu-id="555cf-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="555cf-131">O `HANDLE` tipo não é compatível com COM, ou seja, seu tamanho é específico para o sistema operacional, e requer empacotamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="555cf-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="555cf-132">Assim, este token é para uso apenas dentro do processo, entre o CLR e o host.</span><span class="sxs-lookup"><span data-stu-id="555cf-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="555cf-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="555cf-133">Requirements</span></span>  
 <span data-ttu-id="555cf-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="555cf-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="555cf-135">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="555cf-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="555cf-136">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="555cf-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="555cf-137">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="555cf-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="555cf-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="555cf-138">See also</span></span>

- [<span data-ttu-id="555cf-139">Interface IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="555cf-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="555cf-140">Interface IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="555cf-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
