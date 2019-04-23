---
title: Função GetRequestedRuntimeVersionForCLSID
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b4ac1a37c2b3506216499ed0c9f8194949b768
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59081886"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="8b715-102">Função GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="8b715-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="8b715-103">Obtém o common language runtime (CLR) versão informações apropriadas para a classe com especificado `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="8b715-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="8b715-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b715-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b715-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b715-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b715-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b715-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="8b715-107">[in]  O `CLSID` do componente.</span><span class="sxs-lookup"><span data-stu-id="8b715-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="8b715-108">[out]  Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="8b715-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="8b715-109">[in]  O tamanho, em caracteres largos, da `pVersion` buffer.</span><span class="sxs-lookup"><span data-stu-id="8b715-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="8b715-110">[out] O comprimento, em bytes, do buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="8b715-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="8b715-111">[in]  Um dos valores CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="8b715-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="8b715-112">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="8b715-112">The following values are supported:</span></span>  
  
-   <span data-ttu-id="8b715-113">CLSID_RESOLUTION_DEFAULT: (0x0) Especifica que o comportamento de interoperabilidade padrão deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="8b715-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
-   <span data-ttu-id="8b715-114">CLSID_RESOLUTION_REGISTERED: (0x1) Especifica que o registro deve ser pesquisado e política de correção deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="8b715-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b715-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8b715-115">Return Value</span></span>  
  
|<span data-ttu-id="8b715-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b715-116">HRESULT</span></span>|<span data-ttu-id="8b715-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b715-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8b715-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="8b715-118">S_OK</span></span>|<span data-ttu-id="8b715-119">A função retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="8b715-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="8b715-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8b715-120">E_INVALIDARG</span></span>|<span data-ttu-id="8b715-121">Um dos parâmetros tem um tipo ou formato inválido.</span><span class="sxs-lookup"><span data-stu-id="8b715-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="8b715-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8b715-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8b715-123">O `pVersion` buffer não é grande o suficiente para manter a cadeia de caracteres de versão inteira.</span><span class="sxs-lookup"><span data-stu-id="8b715-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="8b715-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="8b715-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="8b715-125">Não há nenhuma classe registrada com o especificado `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="8b715-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="8b715-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8b715-126">E_POINTER</span></span>|<span data-ttu-id="8b715-127">`dwLength` é nulo, ou `cchBuffer` é grande o suficiente para manter a cadeia de caracteres de versão, mas `pVersion` é nulo.</span><span class="sxs-lookup"><span data-stu-id="8b715-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b715-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b715-128">Requirements</span></span>  
 <span data-ttu-id="8b715-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b715-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b715-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8b715-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b715-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b715-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b715-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b715-132">See also</span></span>

- [<span data-ttu-id="8b715-133">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="8b715-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
