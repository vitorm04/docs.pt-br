---
title: Função BlessIWbemServices (referência de API não gerenciada)
description: A função BlessIWbemServices indica se as credenciais de usuário permitirem o acesso a uma classe IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a65c3c14507b2520c69875a1bc101ce826ace7ba
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532159"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="c7350-103">Função BlessIWbemServices</span><span class="sxs-lookup"><span data-stu-id="c7350-103">BlessIWbemServices function</span></span>
<span data-ttu-id="c7350-104">Indica se as credenciais de usuário permitirem o acesso especificado [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) classe.</span><span class="sxs-lookup"><span data-stu-id="c7350-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c7350-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7350-105">Syntax</span></span>  
  
```  
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser, 
   [in] BSTR strPassword, 
   [in] BSTR strAuthority, 
   [in] DWORD impLevel, 
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="c7350-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7350-106">Parameters</span></span>

`pIWbemServices`  
<span data-ttu-id="c7350-107">[in] Um ponteiro para o [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto para o qual as permissões são necessárias.</span><span class="sxs-lookup"><span data-stu-id="c7350-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`  
<span data-ttu-id="c7350-108">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="c7350-108">[in] The user name.</span></span>

`strPassword`  
<span data-ttu-id="c7350-109">[in] A senha associada `strUser`.</span><span class="sxs-lookup"><span data-stu-id="c7350-109">[in] The password associated with `strUser`.</span></span>

<span data-ttu-id="c7350-110">`strAuthority` [in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="c7350-110">`strAuthority` [in] The domain name of the user.</span></span> <span data-ttu-id="c7350-111">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c7350-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="c7350-112">`impLevel` [in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="c7350-112">`impLevel` [in] The impersonation level.</span></span>

<span data-ttu-id="c7350-113">`authnLevel` [in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="c7350-113">`authnLevel` [in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="c7350-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c7350-114">Return value</span></span>

<span data-ttu-id="c7350-115">Os seguintes valores retornados por essa função são definidos na *Winerror. H* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="c7350-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c7350-116">Constante</span><span class="sxs-lookup"><span data-stu-id="c7350-116">Constant</span></span>  |<span data-ttu-id="c7350-117">Valor</span><span class="sxs-lookup"><span data-stu-id="c7350-117">Value</span></span>  |<span data-ttu-id="c7350-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c7350-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="c7350-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="c7350-119">0x80070057</span></span> | <span data-ttu-id="c7350-120">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="c7350-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="c7350-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="c7350-121">0x80004003</span></span> | <span data-ttu-id="c7350-122">`pIWbemServices` é `null`.</span><span class="sxs-lookup"><span data-stu-id="c7350-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="c7350-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="c7350-123">0x80000008</span></span> | <span data-ttu-id="c7350-124">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="c7350-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="c7350-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="c7350-125">0x80000002</span></span> | <span data-ttu-id="c7350-126">Memória disponível é insuficiente para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="c7350-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="c7350-127">0</span><span class="sxs-lookup"><span data-stu-id="c7350-127">0</span></span> | <span data-ttu-id="c7350-128">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="c7350-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="c7350-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7350-129">Requirements</span></span>  
 <span data-ttu-id="c7350-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7350-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7350-131">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c7350-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c7350-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c7350-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7350-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7350-133">See also</span></span>  
[<span data-ttu-id="c7350-134">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="c7350-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
