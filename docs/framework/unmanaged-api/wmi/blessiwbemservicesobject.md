---
title: Função BlessIWbemServicesObject (referência de API não gerenciada)
description: A função BlessIWbemServicesObject indica se as credenciais do usuário permitem acesso a um objeto IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175025"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="2278c-103">Função BlessIWbemServicesObject</span><span class="sxs-lookup"><span data-stu-id="2278c-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="2278c-104">Indica se as credenciais do usuário permitem acesso a um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) especificado.</span><span class="sxs-lookup"><span data-stu-id="2278c-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2278c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2278c-105">Syntax</span></span>

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a><span data-ttu-id="2278c-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2278c-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="2278c-107">[em] Um ponteiro para um objeto de serviço WMI.</span><span class="sxs-lookup"><span data-stu-id="2278c-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="2278c-108">[em] O nome do usuário.</span><span class="sxs-lookup"><span data-stu-id="2278c-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="2278c-109">[em] A senha `strUser`associada a .</span><span class="sxs-lookup"><span data-stu-id="2278c-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="2278c-110">[em] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="2278c-110">[in] The domain name of the user.</span></span> <span data-ttu-id="2278c-111">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2278c-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="2278c-112">[em] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="2278c-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="2278c-113">[em] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="2278c-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="2278c-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2278c-114">Return value</span></span>

<span data-ttu-id="2278c-115">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WinError.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="2278c-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2278c-116">Constante</span><span class="sxs-lookup"><span data-stu-id="2278c-116">Constant</span></span>  |<span data-ttu-id="2278c-117">Valor</span><span class="sxs-lookup"><span data-stu-id="2278c-117">Value</span></span>  |<span data-ttu-id="2278c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="2278c-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="2278c-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="2278c-119">0x80070057</span></span> | <span data-ttu-id="2278c-120">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="2278c-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="2278c-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="2278c-121">0x80004003</span></span> | <span data-ttu-id="2278c-122">`pIWbemServices` é `null`.</span><span class="sxs-lookup"><span data-stu-id="2278c-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="2278c-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="2278c-123">0x80000008</span></span> | <span data-ttu-id="2278c-124">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="2278c-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="2278c-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="2278c-125">0x80000002</span></span> | <span data-ttu-id="2278c-126">A memória insuficiente está disponível para realizar a operação.</span><span class="sxs-lookup"><span data-stu-id="2278c-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="2278c-127">0</span><span class="sxs-lookup"><span data-stu-id="2278c-127">0</span></span> | <span data-ttu-id="2278c-128">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="2278c-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="2278c-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2278c-129">Requirements</span></span>

 <span data-ttu-id="2278c-130">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2278c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="2278c-131">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2278c-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="2278c-132">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2278c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2278c-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="2278c-133">See also</span></span>

- [<span data-ttu-id="2278c-134">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="2278c-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
