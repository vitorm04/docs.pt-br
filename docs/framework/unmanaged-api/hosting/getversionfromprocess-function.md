---
title: Função GetVersionFromProcess
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3055ac73f15329015f532f42c1f922eab38828cb
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490300"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="f32ee-102">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="f32ee-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="f32ee-103">Obtém o número de versão do common language runtime (CLR) que está associado com o identificador de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="f32ee-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="f32ee-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f32ee-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32ee-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f32ee-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f32ee-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f32ee-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="f32ee-107">[in] Um identificador para um processo.</span><span class="sxs-lookup"><span data-stu-id="f32ee-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="f32ee-108">[out] Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida do método.</span><span class="sxs-lookup"><span data-stu-id="f32ee-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f32ee-109">[in] O comprimento do buffer de versão.</span><span class="sxs-lookup"><span data-stu-id="f32ee-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="f32ee-110">[out] Um ponteiro para o comprimento da sequência de números de versão.</span><span class="sxs-lookup"><span data-stu-id="f32ee-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f32ee-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f32ee-111">Return Value</span></span>  
 <span data-ttu-id="f32ee-112">Esse método retorna códigos de erro padrão (COM Component Object Model), conforme definido em Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="f32ee-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="f32ee-113">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="f32ee-113">Return code</span></span>|<span data-ttu-id="f32ee-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f32ee-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="f32ee-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f32ee-115">S_OK</span></span>|<span data-ttu-id="f32ee-116">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f32ee-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="f32ee-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f32ee-117">E_INVALIDARG</span></span>|<span data-ttu-id="f32ee-118">`pVersion` é nulo e `cchBuffer` não for nulo, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="f32ee-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="f32ee-119">- ou -</span><span class="sxs-lookup"><span data-stu-id="f32ee-119">-or-</span></span><br /><br /> <span data-ttu-id="f32ee-120">`hProcess` não é um identificador válido para um processo.</span><span class="sxs-lookup"><span data-stu-id="f32ee-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="f32ee-121">- ou -</span><span class="sxs-lookup"><span data-stu-id="f32ee-121">-or-</span></span><br /><br /> <span data-ttu-id="f32ee-122">O CLR não está carregado.</span><span class="sxs-lookup"><span data-stu-id="f32ee-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="f32ee-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f32ee-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f32ee-124">`cchBuffer` é nulo ou menor que o comprimento da cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="f32ee-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="f32ee-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f32ee-125">E_NOTIMPL</span></span>|<span data-ttu-id="f32ee-126">Esse método não está disponível no sistema operacional Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="f32ee-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f32ee-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f32ee-127">Requirements</span></span>  
 <span data-ttu-id="f32ee-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f32ee-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f32ee-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f32ee-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f32ee-130">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f32ee-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f32ee-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f32ee-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f32ee-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f32ee-132">See also</span></span>

- [<span data-ttu-id="f32ee-133">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="f32ee-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="f32ee-134">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="f32ee-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="f32ee-135">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="f32ee-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
