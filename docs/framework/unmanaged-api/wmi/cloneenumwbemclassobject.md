---
title: Função CloneEnumWbemClassObject (referência de API não gerenciada)
description: A função CloneEnumWbemClassObject faz uma cópia lógica de um enumerador.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab660769a49cf12b129cb7f44b8378053a231f8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761619"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="ab56e-103">Função CloneEnumWbemClassObject</span><span class="sxs-lookup"><span data-stu-id="ab56e-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="ab56e-104">Faz uma cópia lógica de um enumerador, mantendo sua posição atual em uma enumeração.</span><span class="sxs-lookup"><span data-stu-id="ab56e-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ab56e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab56e-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```

## <a name="parameters"></a><span data-ttu-id="ab56e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab56e-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="ab56e-107">[out] Recebe um ponteiro para um novo [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="ab56e-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="ab56e-108">[in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="ab56e-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="ab56e-109">[in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="ab56e-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="ab56e-110">[out] Um ponteiro para o [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instância a ser clonado.</span><span class="sxs-lookup"><span data-stu-id="ab56e-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="ab56e-111">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="ab56e-111">[in] The user name.</span></span> <span data-ttu-id="ab56e-112">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ab56e-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="ab56e-113">[in] A senha.</span><span class="sxs-lookup"><span data-stu-id="ab56e-113">[in] The password.</span></span> <span data-ttu-id="ab56e-114">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ab56e-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="ab56e-115">`strAuthority`\ [in] o nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="ab56e-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="ab56e-116">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="ab56e-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="ab56e-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ab56e-117">Return value</span></span>

<span data-ttu-id="ab56e-118">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="ab56e-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ab56e-119">Constante</span><span class="sxs-lookup"><span data-stu-id="ab56e-119">Constant</span></span>  |<span data-ttu-id="ab56e-120">Valor</span><span class="sxs-lookup"><span data-stu-id="ab56e-120">Value</span></span>  |<span data-ttu-id="ab56e-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ab56e-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="ab56e-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ab56e-122">0x80041001</span></span> | <span data-ttu-id="ab56e-123">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="ab56e-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ab56e-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ab56e-124">0x80041008</span></span> | <span data-ttu-id="ab56e-125">Um parâmetro é inválido.</span><span class="sxs-lookup"><span data-stu-id="ab56e-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ab56e-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ab56e-126">0x80041006</span></span> | <span data-ttu-id="ab56e-127">Não há memória suficiente está disponível concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="ab56e-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="ab56e-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="ab56e-128">0x80041015</span></span> | <span data-ttu-id="ab56e-129">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="ab56e-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ab56e-130">0</span><span class="sxs-lookup"><span data-stu-id="ab56e-130">0</span></span> | <span data-ttu-id="ab56e-131">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ab56e-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ab56e-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab56e-132">Remarks</span></span>

<span data-ttu-id="ab56e-133">Essa função encapsula uma chamada para o [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) método.</span><span class="sxs-lookup"><span data-stu-id="ab56e-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="ab56e-134">Esse método faz apenas uma cópia de "melhor esforço".</span><span class="sxs-lookup"><span data-stu-id="ab56e-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="ab56e-135">Devido à natureza dinâmica de muitos objetos CIM, é possível que o novo enumerador não enumera o mesmo conjunto de objetos que o enumerador de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="ab56e-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="ab56e-136">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="ab56e-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="ab56e-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab56e-137">Example</span></span>

<span data-ttu-id="ab56e-138">Por exemplo, consulte o [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) método.</span><span class="sxs-lookup"><span data-stu-id="ab56e-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ab56e-139">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab56e-139">Requirements</span></span>
 <span data-ttu-id="ab56e-140">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab56e-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="ab56e-141">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ab56e-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="ab56e-142">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ab56e-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ab56e-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab56e-143">See also</span></span>

- [<span data-ttu-id="ab56e-144">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="ab56e-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
