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
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178055"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="ce296-102">Método ICLRValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="ce296-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="ce296-103">Valida o executável portátil (PE) ou o idioma intermediário Microsoft (MSIL) no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ce296-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce296-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce296-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ce296-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce296-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="ce296-106">[em] Um ponteiro `IVEHandler` para uma instância que lida com erros de validação.</span><span class="sxs-lookup"><span data-stu-id="ce296-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="ce296-107">[em] O identificador da <xref:System.AppDomain>corrente.</span><span class="sxs-lookup"><span data-stu-id="ce296-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="ce296-108">[em] Uma combinação de valores [ValidatorFlags,](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) indicando o tipo de validação que deve ser realizada.</span><span class="sxs-lookup"><span data-stu-id="ce296-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="ce296-109">[em] O número máximo de erros a serem permitidos antes de sair da validação.</span><span class="sxs-lookup"><span data-stu-id="ce296-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="ce296-110">[em] Utilizadas.</span><span class="sxs-lookup"><span data-stu-id="ce296-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="ce296-111">[em] O nome do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="ce296-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="ce296-112">[em] Um ponteiro para o buffer de arquivos.</span><span class="sxs-lookup"><span data-stu-id="ce296-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="ce296-113">[em] O tamanho, em bytes, do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="ce296-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce296-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ce296-114">Return Value</span></span>  
  
|<span data-ttu-id="ce296-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce296-115">HRESULT</span></span>|<span data-ttu-id="ce296-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce296-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce296-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce296-117">S_OK</span></span>|<span data-ttu-id="ce296-118">`Validate`retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="ce296-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="ce296-119">Host_e_clrnotavailable</span><span class="sxs-lookup"><span data-stu-id="ce296-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ce296-120">O tempo de execução do idioma comum (CLR) não foi carregado em um processo, ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="ce296-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ce296-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ce296-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ce296-122">A chamada acabou.</span><span class="sxs-lookup"><span data-stu-id="ce296-122">The call timed out.</span></span>|  
|<span data-ttu-id="ce296-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ce296-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ce296-124">O interlocutor não é dono da fechadura.</span><span class="sxs-lookup"><span data-stu-id="ce296-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ce296-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ce296-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ce296-126">Um evento foi cancelado enquanto um fio ou fibra bloqueado estava esperando por ele.</span><span class="sxs-lookup"><span data-stu-id="ce296-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ce296-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ce296-127">E_FAIL</span></span>|<span data-ttu-id="ce296-128">Uma falha catastrófica desconhecida ocorreu.</span><span class="sxs-lookup"><span data-stu-id="ce296-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ce296-129">Quando um método retorna E_FAIL, a CLR não é mais utilizável dentro do processo.</span><span class="sxs-lookup"><span data-stu-id="ce296-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ce296-130">Chamadas subseqüentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ce296-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce296-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce296-131">Requirements</span></span>  
 <span data-ttu-id="ce296-132">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce296-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce296-133">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="ce296-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="ce296-134">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ce296-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce296-135">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce296-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce296-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce296-136">See also</span></span>

- [<span data-ttu-id="ce296-137">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="ce296-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
