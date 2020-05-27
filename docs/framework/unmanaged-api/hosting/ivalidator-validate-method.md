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
ms.openlocfilehash: 688abd210cca193bf03c40f000b74ecb66eb8ede
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008541"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="53403-102">Método IValidator::Validate</span><span class="sxs-lookup"><span data-stu-id="53403-102">IValidator::Validate Method</span></span>
<span data-ttu-id="53403-103">Valida o executável portátil (PE) ou o arquivo. MSIL (Microsoft Intermediate Language) especificado.</span><span class="sxs-lookup"><span data-stu-id="53403-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53403-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53403-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="53403-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53403-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="53403-106">no Um ponteiro para uma `IVEHandler` instância que manipula erros de validação.</span><span class="sxs-lookup"><span data-stu-id="53403-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="53403-107">no Um ponteiro para o domínio do aplicativo no qual o arquivo é carregado.</span><span class="sxs-lookup"><span data-stu-id="53403-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="53403-108">no Uma combinação de bits de valor [ValidatorFlags](validatorflags-enumeration.md) , que indica as validações que devem ser executadas.</span><span class="sxs-lookup"><span data-stu-id="53403-108">[in] A bitwise combination of [ValidatorFlags](validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="53403-109">no O número máximo de erros a serem permitidos antes de sair da validação.</span><span class="sxs-lookup"><span data-stu-id="53403-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="53403-110">no Não usado.</span><span class="sxs-lookup"><span data-stu-id="53403-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="53403-111">no Uma cadeia de caracteres que especifica o nome do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="53403-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="53403-112">no Um ponteiro para o buffer de memória no qual o arquivo está armazenado.</span><span class="sxs-lookup"><span data-stu-id="53403-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="53403-113">no O tamanho, em bytes, do arquivo a ser validado.</span><span class="sxs-lookup"><span data-stu-id="53403-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53403-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53403-114">Requirements</span></span>  
 <span data-ttu-id="53403-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53403-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53403-116">**Cabeçalho:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="53403-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="53403-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53403-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53403-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53403-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
