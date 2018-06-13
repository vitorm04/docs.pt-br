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
ms.openlocfilehash: 0b57d04a8a49371872c679a331b5ae9c45dce797
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433067"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="a907e-102">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="a907e-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="a907e-103">Obtém o número de versão do common language runtime (CLR) que está associado com o identificador de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="a907e-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="a907e-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a907e-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a907e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a907e-105">Syntax</span></span>  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a907e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a907e-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="a907e-107">[in] Um identificador para um processo.</span><span class="sxs-lookup"><span data-stu-id="a907e-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a907e-108">[out] Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida do método.</span><span class="sxs-lookup"><span data-stu-id="a907e-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a907e-109">[in] O comprimento do buffer de versão.</span><span class="sxs-lookup"><span data-stu-id="a907e-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="a907e-110">[out] Um ponteiro para o comprimento da cadeia de número de versão.</span><span class="sxs-lookup"><span data-stu-id="a907e-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a907e-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a907e-111">Return Value</span></span>  
 <span data-ttu-id="a907e-112">Esse método retorna códigos de erro do modelo de objeto de componente (COM) padrão, conforme definido no Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="a907e-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a907e-113">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="a907e-113">Return code</span></span>|<span data-ttu-id="a907e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a907e-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a907e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a907e-115">S_OK</span></span>|<span data-ttu-id="a907e-116">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a907e-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a907e-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a907e-117">E_INVALIDARG</span></span>|<span data-ttu-id="a907e-118">`pVersion` é nulo e `cchBuffer` não for null, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="a907e-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="a907e-119">-ou-</span><span class="sxs-lookup"><span data-stu-id="a907e-119">-or-</span></span><br /><br /> <span data-ttu-id="a907e-120">`hProcess` não é um identificador válido para um processo.</span><span class="sxs-lookup"><span data-stu-id="a907e-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="a907e-121">-ou-</span><span class="sxs-lookup"><span data-stu-id="a907e-121">-or-</span></span><br /><br /> <span data-ttu-id="a907e-122">O CLR não está carregado.</span><span class="sxs-lookup"><span data-stu-id="a907e-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="a907e-123">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a907e-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a907e-124">`cchBuffer` é nula ou menor que o comprimento da cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="a907e-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="a907e-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a907e-125">E_NOTIMPL</span></span>|<span data-ttu-id="a907e-126">Este método não está disponível no sistema operacional Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="a907e-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a907e-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a907e-127">Requirements</span></span>  
 <span data-ttu-id="a907e-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a907e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a907e-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a907e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a907e-130">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a907e-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a907e-131">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a907e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a907e-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a907e-132">See Also</span></span>  
 [<span data-ttu-id="a907e-133">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a907e-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="a907e-134">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="a907e-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="a907e-135">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="a907e-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
