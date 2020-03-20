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
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178126"
---
# <a name="getversionfromprocess-function"></a><span data-ttu-id="093f7-102">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="093f7-102">GetVersionFromProcess Function</span></span>
<span data-ttu-id="093f7-103">Obtém o número da versão do tempo de execução do idioma comum (CLR) que está associado à alça de processo especificada.</span><span class="sxs-lookup"><span data-stu-id="093f7-103">Gets the version number of the common language runtime (CLR) that is associated with the specified process handle.</span></span>  
  
 <span data-ttu-id="093f7-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="093f7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="093f7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="093f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="093f7-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="093f7-106">Parameters</span></span>  
 `hProcess`  
 <span data-ttu-id="093f7-107">[em] Uma alça para um processo.</span><span class="sxs-lookup"><span data-stu-id="093f7-107">[in] A handle to a process.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="093f7-108">[fora] Um buffer que contém a seqüência de números da versão após a conclusão bem sucedida do método.</span><span class="sxs-lookup"><span data-stu-id="093f7-108">[out] A buffer that contains the version number string upon successful completion of the method.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="093f7-109">[em] O comprimento do buffer da versão.</span><span class="sxs-lookup"><span data-stu-id="093f7-109">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="093f7-110">[fora] Um ponteiro para o comprimento da seqüência numérica da versão.</span><span class="sxs-lookup"><span data-stu-id="093f7-110">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="093f7-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="093f7-111">Return Value</span></span>  
 <span data-ttu-id="093f7-112">Este método retorna códigos de erro com (Component Object Model, modelo de objeto componente padrão), conforme definido em WinError.h, além dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="093f7-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="093f7-113">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="093f7-113">Return code</span></span>|<span data-ttu-id="093f7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="093f7-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="093f7-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="093f7-115">S_OK</span></span>|<span data-ttu-id="093f7-116">O método foi concluído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="093f7-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="093f7-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="093f7-117">E_INVALIDARG</span></span>|<span data-ttu-id="093f7-118">`pVersion`é nulo e `cchBuffer` não é nulo, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="093f7-118">`pVersion` is null and `cchBuffer` is not null, or vice versa.</span></span><br /><br /> <span data-ttu-id="093f7-119">-ou-</span><span class="sxs-lookup"><span data-stu-id="093f7-119">-or-</span></span><br /><br /> <span data-ttu-id="093f7-120">`hProcess`não é uma alça válida para um processo.</span><span class="sxs-lookup"><span data-stu-id="093f7-120">`hProcess` is not a valid handle to a process.</span></span><br /><br /> <span data-ttu-id="093f7-121">-ou-</span><span class="sxs-lookup"><span data-stu-id="093f7-121">-or-</span></span><br /><br /> <span data-ttu-id="093f7-122">A CLR não está carregada.</span><span class="sxs-lookup"><span data-stu-id="093f7-122">The CLR is not loaded.</span></span>|  
|<span data-ttu-id="093f7-123">Error_insufficient_buffer</span><span class="sxs-lookup"><span data-stu-id="093f7-123">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="093f7-124">`cchBuffer`é nulo ou menor do que o comprimento da seqüência de versão.</span><span class="sxs-lookup"><span data-stu-id="093f7-124">`cchBuffer` is null or less than the length of the version string.</span></span>|  
|<span data-ttu-id="093f7-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="093f7-125">E_NOTIMPL</span></span>|<span data-ttu-id="093f7-126">Este método não está disponível no sistema operacional Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.</span><span class="sxs-lookup"><span data-stu-id="093f7-126">This method is not available on the Microsoft Windows 95, Microsoft Windows 98, or Microsoft Windows Millennium Edition operating system.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="093f7-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="093f7-127">Requirements</span></span>  
 <span data-ttu-id="093f7-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="093f7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="093f7-129">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="093f7-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="093f7-130">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="093f7-130">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="093f7-131">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="093f7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="093f7-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="093f7-132">See also</span></span>

- [<span data-ttu-id="093f7-133">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="093f7-133">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="093f7-134">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="093f7-134">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="093f7-135">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="093f7-135">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
