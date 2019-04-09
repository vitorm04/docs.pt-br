---
title: Função LoadStringRCEx
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 697557463aa949036acb21e63b9a82b1fb84b415
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105489"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="99bf6-102">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="99bf6-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="99bf6-103">Converte um valor HRESULT a uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="99bf6-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="99bf6-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99bf6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99bf6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99bf6-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99bf6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="99bf6-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="99bf6-107">[in] Um identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="99bf6-107">[in] A culture identifier.</span></span> <span data-ttu-id="99bf6-108">Passe -1 `lcid` para usar a cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="99bf6-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="99bf6-109">[in] Um HRESULT.</span><span class="sxs-lookup"><span data-stu-id="99bf6-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="99bf6-110">[out] Um buffer que contém a mensagem de erro após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="99bf6-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="99bf6-111">[in] O tamanho do buffer de mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="99bf6-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="99bf6-112">[in] Ignorado.</span><span class="sxs-lookup"><span data-stu-id="99bf6-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="99bf6-113">[out] Um ponteiro para o comprimento da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="99bf6-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99bf6-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="99bf6-114">Return Value</span></span>  
 <span data-ttu-id="99bf6-115">Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="99bf6-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="99bf6-116">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="99bf6-116">Return code</span></span>|<span data-ttu-id="99bf6-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="99bf6-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="99bf6-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="99bf6-118">S_OK</span></span>|<span data-ttu-id="99bf6-119">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="99bf6-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="99bf6-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="99bf6-120">E_INVALIDARG</span></span>|`szBuffer` <span data-ttu-id="99bf6-121">é nulo, ou `iMax` é zero (0).</span><span class="sxs-lookup"><span data-stu-id="99bf6-121">is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99bf6-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="99bf6-122">Remarks</span></span>  
 <span data-ttu-id="99bf6-123">Se o método não for concluída com êxito, `szBuffer` contém uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="99bf6-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99bf6-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="99bf6-124">Requirements</span></span>  
 <span data-ttu-id="99bf6-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99bf6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99bf6-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99bf6-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99bf6-127">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99bf6-127">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="99bf6-128">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="99bf6-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99bf6-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99bf6-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="99bf6-130">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="99bf6-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="99bf6-131">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="99bf6-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
