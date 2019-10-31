---
title: Método ICLRValidator::Validate
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 497a115b980bb58a3906fda68d7ff564efe78089
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127835"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="6b517-102">Método ICLRValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="6b517-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="6b517-103">Valida o executável portátil (PE) ou o Microsoft Intermediate Language (MSIL) no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="6b517-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b517-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b517-104">Syntax</span></span>  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
## <a name="parameters"></a><span data-ttu-id="6b517-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b517-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="6b517-106">no Um ponteiro para uma instância de `IVEHandler` que lida com erros de validação.</span><span class="sxs-lookup"><span data-stu-id="6b517-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="6b517-107">no O identificador para o <xref:System.AppDomain>atual.</span><span class="sxs-lookup"><span data-stu-id="6b517-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="6b517-108">no Uma combinação de valores [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) , que indica o tipo de validação que deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="6b517-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="6b517-109">no O número máximo de erros a serem permitidos antes de sair da validação.</span><span class="sxs-lookup"><span data-stu-id="6b517-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="6b517-110">no Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="6b517-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="6b517-111">no O nome do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="6b517-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="6b517-112">no Um ponteiro para o buffer de arquivo.</span><span class="sxs-lookup"><span data-stu-id="6b517-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="6b517-113">no O tamanho, em bytes, do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="6b517-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b517-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6b517-114">Return Value</span></span>  
  
|<span data-ttu-id="6b517-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b517-115">HRESULT</span></span>|<span data-ttu-id="6b517-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b517-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b517-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b517-117">S_OK</span></span>|<span data-ttu-id="6b517-118">`Validate` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="6b517-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="6b517-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b517-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b517-120">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="6b517-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b517-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b517-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b517-122">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="6b517-122">The call timed out.</span></span>|  
|<span data-ttu-id="6b517-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b517-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b517-124">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="6b517-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b517-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b517-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b517-126">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="6b517-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b517-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b517-127">E_FAIL</span></span>|<span data-ttu-id="6b517-128">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="6b517-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b517-129">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="6b517-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b517-130">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b517-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b517-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b517-131">Requirements</span></span>  
 <span data-ttu-id="6b517-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b517-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b517-133">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="6b517-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="6b517-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b517-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b517-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b517-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b517-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b517-136">See also</span></span>

- [<span data-ttu-id="6b517-137">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="6b517-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
