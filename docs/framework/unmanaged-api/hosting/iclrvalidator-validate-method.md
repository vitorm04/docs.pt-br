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
ms.openlocfilehash: 18492f3e95947a3a11da9d5d303651c04d764a8f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762624"
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="15589-102">Método ICLRValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="15589-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="15589-103">Valida o executável portátil (PE) ou o Microsoft Intermediate Language (MSIL) no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="15589-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15589-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15589-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="15589-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="15589-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="15589-106">no Um ponteiro para uma `IVEHandler` instância que manipula erros de validação.</span><span class="sxs-lookup"><span data-stu-id="15589-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="15589-107">no O identificador para o atual <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="15589-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="15589-108">no Uma combinação de valores [ValidatorFlags](validatorflags-enumeration.md) , que indica o tipo de validação que deve ser executada.</span><span class="sxs-lookup"><span data-stu-id="15589-108">[in] A combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="15589-109">no O número máximo de erros a serem permitidos antes de sair da validação.</span><span class="sxs-lookup"><span data-stu-id="15589-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="15589-110">no Não utilizado.</span><span class="sxs-lookup"><span data-stu-id="15589-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="15589-111">no O nome do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="15589-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="15589-112">no Um ponteiro para o buffer de arquivo.</span><span class="sxs-lookup"><span data-stu-id="15589-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="15589-113">no O tamanho, em bytes, do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="15589-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15589-114">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="15589-114">Return Value</span></span>  
  
|<span data-ttu-id="15589-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15589-115">HRESULT</span></span>|<span data-ttu-id="15589-116">Description</span><span class="sxs-lookup"><span data-stu-id="15589-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15589-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="15589-117">S_OK</span></span>|<span data-ttu-id="15589-118">`Validate`retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="15589-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="15589-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15589-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15589-120">O Common Language Runtime (CLR) não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="15589-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15589-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15589-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15589-122">A chamada atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="15589-122">The call timed out.</span></span>|  
|<span data-ttu-id="15589-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15589-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15589-124">O chamador não possui o bloqueio.</span><span class="sxs-lookup"><span data-stu-id="15589-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15589-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15589-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15589-126">Um evento foi cancelado enquanto um thread ou uma fibra bloqueada estava esperando.</span><span class="sxs-lookup"><span data-stu-id="15589-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15589-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15589-127">E_FAIL</span></span>|<span data-ttu-id="15589-128">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="15589-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15589-129">Quando um método retorna E_FAIL, o CLR não é mais utilizável no processo.</span><span class="sxs-lookup"><span data-stu-id="15589-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15589-130">As chamadas subsequentes para métodos de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="15589-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15589-131">Requisitos</span><span class="sxs-lookup"><span data-stu-id="15589-131">Requirements</span></span>  
 <span data-ttu-id="15589-132">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15589-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15589-133">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="15589-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="15589-134">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15589-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15589-135">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15589-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15589-136">Veja também</span><span class="sxs-lookup"><span data-stu-id="15589-136">See also</span></span>

- [<span data-ttu-id="15589-137">Interface ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="15589-137">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
