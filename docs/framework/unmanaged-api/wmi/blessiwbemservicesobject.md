---
title: Função BlessIWbemServicesObject (referência de API não gerenciada)
description: A função BlessIWbemServicesObject indica se as credenciais do usuário permitem o acesso a um objeto IWbemServices
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94c6f47e67cf22f189719a8a9f56e830ee90227c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798718"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="a46d3-103">Função BlessIWbemServicesObject</span><span class="sxs-lookup"><span data-stu-id="a46d3-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="a46d3-104">Indica se as credenciais do usuário permitem o acesso a um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) especificado.</span><span class="sxs-lookup"><span data-stu-id="a46d3-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a46d3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a46d3-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="a46d3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a46d3-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="a46d3-107">no Um ponteiro para um objeto de serviço WMI.</span><span class="sxs-lookup"><span data-stu-id="a46d3-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="a46d3-108">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="a46d3-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="a46d3-109">no A senha associada `strUser`a.</span><span class="sxs-lookup"><span data-stu-id="a46d3-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="a46d3-110">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="a46d3-110">[in] The domain name of the user.</span></span> <span data-ttu-id="a46d3-111">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="a46d3-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="a46d3-112">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="a46d3-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="a46d3-113">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="a46d3-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="a46d3-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a46d3-114">Return value</span></span>

<span data-ttu-id="a46d3-115">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *Winerror. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="a46d3-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a46d3-116">Constante</span><span class="sxs-lookup"><span data-stu-id="a46d3-116">Constant</span></span>  |<span data-ttu-id="a46d3-117">Valor</span><span class="sxs-lookup"><span data-stu-id="a46d3-117">Value</span></span>  |<span data-ttu-id="a46d3-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="a46d3-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="a46d3-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="a46d3-119">0x80070057</span></span> | <span data-ttu-id="a46d3-120">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="a46d3-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="a46d3-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="a46d3-121">0x80004003</span></span> | <span data-ttu-id="a46d3-122">`pIWbemServices` é `null`.</span><span class="sxs-lookup"><span data-stu-id="a46d3-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="a46d3-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="a46d3-123">0x80000008</span></span> | <span data-ttu-id="a46d3-124">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="a46d3-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="a46d3-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="a46d3-125">0x80000002</span></span> | <span data-ttu-id="a46d3-126">Memória insuficiente disponível para executar a operação.</span><span class="sxs-lookup"><span data-stu-id="a46d3-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="a46d3-127">0</span><span class="sxs-lookup"><span data-stu-id="a46d3-127">0</span></span> | <span data-ttu-id="a46d3-128">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a46d3-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="a46d3-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a46d3-129">Requirements</span></span>

 <span data-ttu-id="a46d3-130">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a46d3-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="a46d3-131">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a46d3-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="a46d3-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a46d3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a46d3-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a46d3-133">See also</span></span>

- [<span data-ttu-id="a46d3-134">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="a46d3-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
