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
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178110"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="24d76-102">Função GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="24d76-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="24d76-103">Obtém as informações apropriadas da versão de tempo de `CLSID`execução do idioma comum (CLR) para a classe com a especificada .</span><span class="sxs-lookup"><span data-stu-id="24d76-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="24d76-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="24d76-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d76-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="24d76-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24d76-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="24d76-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="24d76-107">[em]  O `CLSID` do componente.</span><span class="sxs-lookup"><span data-stu-id="24d76-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="24d76-108">[fora]  Um buffer que contém a seqüência de números da versão após a conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="24d76-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="24d76-109">[em]  O tamanho, em caracteres `pVersion` largos, do buffer.</span><span class="sxs-lookup"><span data-stu-id="24d76-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="24d76-110">[fora] O comprimento, em bytes, do tampão devolvido.</span><span class="sxs-lookup"><span data-stu-id="24d76-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="24d76-111">[em]  Um dos valores CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="24d76-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="24d76-112">Os valores a seguir têm suporte:</span><span class="sxs-lookup"><span data-stu-id="24d76-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="24d76-113">CLSID_RESOLUTION_DEFAULT: (0x0) Especifica que o comportamento de interop padrão deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="24d76-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="24d76-114">CLSID_RESOLUTION_REGISTERED: (0x1) Especifica que o registro deve ser pesquisado e a política de shim deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="24d76-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24d76-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="24d76-115">Return Value</span></span>  
  
|<span data-ttu-id="24d76-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24d76-116">HRESULT</span></span>|<span data-ttu-id="24d76-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="24d76-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24d76-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="24d76-118">S_OK</span></span>|<span data-ttu-id="24d76-119">A função retornou com sucesso.</span><span class="sxs-lookup"><span data-stu-id="24d76-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="24d76-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="24d76-120">E_INVALIDARG</span></span>|<span data-ttu-id="24d76-121">Um dos parâmetros tem um tipo ou formato inválido.</span><span class="sxs-lookup"><span data-stu-id="24d76-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="24d76-122">Error_insufficient_buffer</span><span class="sxs-lookup"><span data-stu-id="24d76-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="24d76-123">O `pVersion` buffer não é grande o suficiente para segurar toda a seqüência de versão.</span><span class="sxs-lookup"><span data-stu-id="24d76-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="24d76-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="24d76-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="24d76-125">Não há classe registrada com `CLSID`o especificado .</span><span class="sxs-lookup"><span data-stu-id="24d76-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="24d76-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="24d76-126">E_POINTER</span></span>|<span data-ttu-id="24d76-127">`dwLength`é nulo, ou `cchBuffer` é grande o `pVersion` suficiente para segurar a seqüência de versão, mas é nulo.</span><span class="sxs-lookup"><span data-stu-id="24d76-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24d76-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24d76-128">Requirements</span></span>  
 <span data-ttu-id="24d76-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24d76-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24d76-130">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24d76-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24d76-131">**.NET Framework Versions:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24d76-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d76-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="24d76-132">See also</span></span>

- [<span data-ttu-id="24d76-133">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="24d76-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
