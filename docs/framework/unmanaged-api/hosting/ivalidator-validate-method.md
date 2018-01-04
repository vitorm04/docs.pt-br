---
title: "Método IValidator::Validate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a74249cb806f332b3ae575223f237438da616972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="37cf3-102">Método IValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="37cf3-102">IValidator::Validate Method</span></span>
<span data-ttu-id="37cf3-103">Valida o especificado PE (executável portátil) ou arquivo do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="37cf3-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37cf3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37cf3-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37cf3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37cf3-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="37cf3-106">[in] Um ponteiro para um `IVEHandler` instância que manipula erros de validação.</span><span class="sxs-lookup"><span data-stu-id="37cf3-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="37cf3-107">[in] Um ponteiro para o domínio de aplicativo no qual o arquivo é carregado.</span><span class="sxs-lookup"><span data-stu-id="37cf3-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="37cf3-108">[in] Uma combinação bit a bit de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valores, indicando as validações que devem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="37cf3-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="37cf3-109">[in] O número máximo de erros permitido antes de sair da validação.</span><span class="sxs-lookup"><span data-stu-id="37cf3-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="37cf3-110">[in] Não usado.</span><span class="sxs-lookup"><span data-stu-id="37cf3-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="37cf3-111">[in] Uma cadeia de caracteres que especifica o nome do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="37cf3-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="37cf3-112">[in] Um ponteiro para o buffer de memória no qual o arquivo está armazenado.</span><span class="sxs-lookup"><span data-stu-id="37cf3-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="37cf3-113">[in] O tamanho, em bytes, do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="37cf3-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37cf3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37cf3-114">Requirements</span></span>  
 <span data-ttu-id="37cf3-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37cf3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37cf3-116">**Cabeçalho:** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="37cf3-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="37cf3-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="37cf3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37cf3-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37cf3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37cf3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37cf3-119">See Also</span></span>  
 
