---
title: Função GetRequestedRuntimeVersion
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ee737f4c6d34e77996f5ba08ce4d84132a99238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207325"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="d955e-102">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="d955e-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="d955e-103">Obtém o número de versão do common language runtime (CLR) solicitado pelo aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="d955e-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="d955e-104">Se essa versão não estiver instalado, obtém a versão mais recente instalado antes da versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="d955e-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="d955e-105">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d955e-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d955e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d955e-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d955e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d955e-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="d955e-108">[in] O nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d955e-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="d955e-109">[out] Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d955e-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="d955e-110">[in] O comprimento do buffer de versão.</span><span class="sxs-lookup"><span data-stu-id="d955e-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="d955e-111">[out] Um ponteiro para o comprimento da sequência de números de versão.</span><span class="sxs-lookup"><span data-stu-id="d955e-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d955e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d955e-112">Return Value</span></span>  
 <span data-ttu-id="d955e-113">Esse método retorna códigos de erro padrão (COM Component Object Model), conforme definido em Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="d955e-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="d955e-114">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="d955e-114">Return code</span></span>|<span data-ttu-id="d955e-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="d955e-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d955e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="d955e-116">S_OK</span></span>|<span data-ttu-id="d955e-117">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="d955e-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="d955e-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d955e-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d955e-119">O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="d955e-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="d955e-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d955e-120">E_POINTER</span></span>|`pdwLength` <span data-ttu-id="d955e-121">é nulo.</span><span class="sxs-lookup"><span data-stu-id="d955e-121">is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d955e-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d955e-122">Requirements</span></span>  
 <span data-ttu-id="d955e-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d955e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d955e-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d955e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d955e-125">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d955e-125">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d955e-126">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d955e-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d955e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d955e-127">See also</span></span>

- [<span data-ttu-id="d955e-128">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="d955e-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="d955e-129">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="d955e-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="d955e-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="d955e-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
