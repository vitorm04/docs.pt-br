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
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178134"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="7fecd-102">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="7fecd-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="7fecd-103">Obtém o número da versão do tempo de execução do idioma comum (CLR) solicitado pelo aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="7fecd-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="7fecd-104">Se essa versão não estiver instalada, terá a versão mais recente que está instalada antes da versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="7fecd-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="7fecd-105">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="7fecd-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fecd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fecd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fecd-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="7fecd-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="7fecd-108">[em] O nome da aplicação.</span><span class="sxs-lookup"><span data-stu-id="7fecd-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="7fecd-109">[fora] Um buffer que contém a seqüência de números da versão após a conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="7fecd-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7fecd-110">[em] O comprimento do buffer da versão.</span><span class="sxs-lookup"><span data-stu-id="7fecd-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="7fecd-111">[fora] Um ponteiro para o comprimento da seqüência numérica da versão.</span><span class="sxs-lookup"><span data-stu-id="7fecd-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fecd-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7fecd-112">Return Value</span></span>  
 <span data-ttu-id="7fecd-113">Este método retorna códigos de erro com (Component Object Model, modelo de objeto componente padrão), conforme definido em WinError.h, além dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="7fecd-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7fecd-114">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="7fecd-114">Return code</span></span>|<span data-ttu-id="7fecd-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="7fecd-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7fecd-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fecd-116">S_OK</span></span>|<span data-ttu-id="7fecd-117">O método foi concluído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="7fecd-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="7fecd-118">Error_insufficient_buffer</span><span class="sxs-lookup"><span data-stu-id="7fecd-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7fecd-119">O buffer de versão não é grande o suficiente para armazenar a seqüência de versões.</span><span class="sxs-lookup"><span data-stu-id="7fecd-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="7fecd-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7fecd-120">E_POINTER</span></span>|<span data-ttu-id="7fecd-121">`pdwLength` é nulo.</span><span class="sxs-lookup"><span data-stu-id="7fecd-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fecd-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7fecd-122">Requirements</span></span>  
 <span data-ttu-id="7fecd-123">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fecd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fecd-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7fecd-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fecd-125">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7fecd-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fecd-126">**.NET Framework Versions:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fecd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fecd-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="7fecd-127">See also</span></span>

- [<span data-ttu-id="7fecd-128">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="7fecd-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="7fecd-129">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="7fecd-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="7fecd-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="7fecd-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
