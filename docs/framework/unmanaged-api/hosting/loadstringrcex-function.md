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
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177978"
---
# <a name="loadstringrcex-function"></a><span data-ttu-id="1de24-102">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="1de24-102">LoadStringRCEx Function</span></span>
<span data-ttu-id="1de24-103">Traduz um valor HRESULT para uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="1de24-103">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="1de24-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="1de24-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1de24-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1de24-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,
    [in]  UINT    iResouceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet,
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1de24-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="1de24-106">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="1de24-107">[em] Um identificador de cultura.</span><span class="sxs-lookup"><span data-stu-id="1de24-107">[in] A culture identifier.</span></span> <span data-ttu-id="1de24-108">Passe -1 `lcid` para usar a cultura padrão.</span><span class="sxs-lookup"><span data-stu-id="1de24-108">Pass -1 for `lcid` to use the default culture.</span></span>  
  
 `iResourceID`  
 <span data-ttu-id="1de24-109">[em] Um HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1de24-109">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="1de24-110">[fora] Um buffer que contém a mensagem de erro após a conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="1de24-110">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="1de24-111">[em] O tamanho do buffer de mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="1de24-111">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="1de24-112">[em] Ignorado.</span><span class="sxs-lookup"><span data-stu-id="1de24-112">[in] Ignored.</span></span>  
  
 `pcwchUsed`  
 <span data-ttu-id="1de24-113">[fora] Um ponteiro para o comprimento da mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="1de24-113">[out] A pointer to the length of the error message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1de24-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1de24-114">Return Value</span></span>  
 <span data-ttu-id="1de24-115">Este método retorna códigos de erro COM padrão, conforme definido em WinError.h, além dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="1de24-115">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="1de24-116">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="1de24-116">Return code</span></span>|<span data-ttu-id="1de24-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="1de24-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="1de24-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="1de24-118">S_OK</span></span>|<span data-ttu-id="1de24-119">O método foi concluído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="1de24-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="1de24-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1de24-120">E_INVALIDARG</span></span>|<span data-ttu-id="1de24-121">`szBuffer`é nulo, ou `iMax` é zero (0).</span><span class="sxs-lookup"><span data-stu-id="1de24-121">`szBuffer` is null, or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1de24-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="1de24-122">Remarks</span></span>  
 <span data-ttu-id="1de24-123">Se o método não `szBuffer` for concluído com sucesso, contém uma seqüência vazia.</span><span class="sxs-lookup"><span data-stu-id="1de24-123">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1de24-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1de24-124">Requirements</span></span>  
 <span data-ttu-id="1de24-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1de24-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1de24-126">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1de24-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1de24-127">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1de24-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1de24-128">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1de24-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de24-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="1de24-129">See also</span></span>

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1de24-130">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="1de24-130">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [<span data-ttu-id="1de24-131">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="1de24-131">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
