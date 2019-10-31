---
title: Método IValidator::Validate
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 8ae47eac713fbee30ea543538957b12460b8e1fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123281"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="cf5ae-102">Método IValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="cf5ae-102">IValidator::Validate Method</span></span>
<span data-ttu-id="cf5ae-103">Valida o executável portátil (PE) ou o arquivo. MSIL (Microsoft Intermediate Language) especificado.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf5ae-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf5ae-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="cf5ae-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf5ae-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="cf5ae-106">no Um ponteiro para uma instância de `IVEHandler` que lida com erros de validação.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="cf5ae-107">no Um ponteiro para o domínio do aplicativo no qual o arquivo é carregado.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="cf5ae-108">no Uma combinação de bits de valor [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) , que indica as validações que devem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="cf5ae-109">no O número máximo de erros a serem permitidos antes de sair da validação.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="cf5ae-110">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="cf5ae-111">no Uma cadeia de caracteres que especifica o nome do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="cf5ae-112">no Um ponteiro para o buffer de memória no qual o arquivo está armazenado.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="cf5ae-113">no O tamanho, em bytes, do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="cf5ae-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf5ae-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf5ae-114">Requirements</span></span>  
 <span data-ttu-id="cf5ae-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf5ae-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf5ae-116">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="cf5ae-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="cf5ae-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf5ae-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf5ae-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf5ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
