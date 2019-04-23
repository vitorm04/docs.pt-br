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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 559c265c70c199e64782ba185d4925d293d6a778
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158685"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="49452-102">Método ICLRValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="49452-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="49452-103">Valida o executável portátil (PE) ou Microsoft intermediate language (MSIL) no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="49452-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49452-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49452-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="49452-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49452-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="49452-106">[in] Um ponteiro para um `IVEHandler` instância que manipula erros de validação.</span><span class="sxs-lookup"><span data-stu-id="49452-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="49452-107">[in] O identificador atual <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="49452-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="49452-108">[in] Uma combinação de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valores, que indica o tipo de validação deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="49452-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="49452-109">[in] O número máximo de erros para permitir que antes de sair da validação.</span><span class="sxs-lookup"><span data-stu-id="49452-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="49452-110">[in] Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="49452-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="49452-111">[in] O nome do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="49452-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="49452-112">[in] Um ponteiro para o buffer de arquivo.</span><span class="sxs-lookup"><span data-stu-id="49452-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="49452-113">[in] O tamanho, em bytes, do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="49452-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49452-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="49452-114">Return Value</span></span>  
  
|<span data-ttu-id="49452-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49452-115">HRESULT</span></span>|<span data-ttu-id="49452-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="49452-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49452-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="49452-117">S_OK</span></span>|<span data-ttu-id="49452-118">`Validate` retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="49452-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="49452-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49452-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49452-120">O common language runtime (CLR) não foi carregado em um processo ou o CLR está em um estado em que ele não pode executar o código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="49452-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49452-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49452-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49452-122">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="49452-122">The call timed out.</span></span>|  
|<span data-ttu-id="49452-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49452-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49452-124">O chamador não é proprietário do bloqueio.</span><span class="sxs-lookup"><span data-stu-id="49452-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49452-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49452-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49452-126">Um evento foi cancelado enquanto um thread bloqueado ou fibra estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="49452-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49452-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49452-127">E_FAIL</span></span>|<span data-ttu-id="49452-128">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="49452-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49452-129">Quando um método retornar E_FAIL, o CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="49452-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49452-130">As chamadas subsequentes à hospedagem de métodos de retorno HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="49452-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49452-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="49452-131">Requirements</span></span>  
 <span data-ttu-id="49452-132">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49452-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49452-133">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="49452-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="49452-134">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="49452-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49452-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49452-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49452-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49452-136">See also</span></span>

- [<span data-ttu-id="49452-137">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="49452-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
