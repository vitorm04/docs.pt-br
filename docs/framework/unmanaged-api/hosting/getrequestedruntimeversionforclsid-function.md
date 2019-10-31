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
ms.openlocfilehash: ce0c6307defd93dcf63ac4e9051fc798041475f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127047"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="34fd2-102">Função GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="34fd2-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="34fd2-103">Obtém as informações de versão do Common Language Runtime (CLR) apropriadas para a classe com a `CLSID`especificada.</span><span class="sxs-lookup"><span data-stu-id="34fd2-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="34fd2-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="34fd2-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fd2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34fd2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34fd2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34fd2-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="34fd2-107">no  O `CLSID` do componente.</span><span class="sxs-lookup"><span data-stu-id="34fd2-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="34fd2-108">fora  Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="34fd2-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="34fd2-109">no  O tamanho, em caracteres largos, do buffer de `pVersion`.</span><span class="sxs-lookup"><span data-stu-id="34fd2-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="34fd2-110">fora O comprimento, em bytes, do buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="34fd2-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="34fd2-111">no  Um dos valores de CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="34fd2-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="34fd2-112">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="34fd2-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="34fd2-113">CLSID_RESOLUTION_DEFAULT: (0x0) especifica que o comportamento de interoperabilidade padrão deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="34fd2-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="34fd2-114">CLSID_RESOLUTION_REGISTERED: (0x1) especifica que o registro deve ser pesquisado e que a política de Shim deve ser aplicada.</span><span class="sxs-lookup"><span data-stu-id="34fd2-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34fd2-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="34fd2-115">Return Value</span></span>  
  
|<span data-ttu-id="34fd2-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34fd2-116">HRESULT</span></span>|<span data-ttu-id="34fd2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="34fd2-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34fd2-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="34fd2-118">S_OK</span></span>|<span data-ttu-id="34fd2-119">A função retornou com êxito.</span><span class="sxs-lookup"><span data-stu-id="34fd2-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="34fd2-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34fd2-120">E_INVALIDARG</span></span>|<span data-ttu-id="34fd2-121">Um dos parâmetros tem um tipo ou formato inválido.</span><span class="sxs-lookup"><span data-stu-id="34fd2-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="34fd2-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="34fd2-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="34fd2-123">O buffer de `pVersion` não é grande o suficiente para manter a cadeia de caracteres de versão inteira.</span><span class="sxs-lookup"><span data-stu-id="34fd2-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="34fd2-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="34fd2-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="34fd2-125">Não há nenhuma classe registrada com o `CLSID`especificado.</span><span class="sxs-lookup"><span data-stu-id="34fd2-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="34fd2-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="34fd2-126">E_POINTER</span></span>|<span data-ttu-id="34fd2-127">`dwLength` é nulo ou `cchBuffer` é grande o suficiente para manter a cadeia de caracteres da versão, mas `pVersion` é nulo.</span><span class="sxs-lookup"><span data-stu-id="34fd2-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34fd2-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34fd2-128">Requirements</span></span>  
 <span data-ttu-id="34fd2-129">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34fd2-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34fd2-130">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="34fd2-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="34fd2-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34fd2-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34fd2-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34fd2-132">See also</span></span>

- [<span data-ttu-id="34fd2-133">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="34fd2-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
