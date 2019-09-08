---
title: Função CreateInstanceEnumWmi (referência de API não gerenciada)
description: A função CreateInstanceEnumWmi retorna um enumerador que contém instâncias de uma classe especificada que atendem aos critérios de seleção.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7709d9c50a494013ece2f91b3acc213278f0e57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798912"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="2c6a6-103">Função CreateInstanceEnumWmi</span><span class="sxs-lookup"><span data-stu-id="2c6a6-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="2c6a6-104">Retorna um enumerador que retorna as instâncias de uma classe especificada que atendem aos critérios de seleção selecionados.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2c6a6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c6a6-105">Syntax</span></span>

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="2c6a6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c6a6-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="2c6a6-107">no O nome da classe para a qual as instâncias são desejadas.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="2c6a6-108">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="2c6a6-109">no Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="2c6a6-110">Os valores a seguir são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="2c6a6-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2c6a6-111">Constante</span><span class="sxs-lookup"><span data-stu-id="2c6a6-111">Constant</span></span>  |<span data-ttu-id="2c6a6-112">Valor</span><span class="sxs-lookup"><span data-stu-id="2c6a6-112">Value</span></span>  |<span data-ttu-id="2c6a6-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c6a6-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="2c6a6-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="2c6a6-114">0x20000</span></span> | <span data-ttu-id="2c6a6-115">Se definido, a função recupera os qualificadores corrigidos armazenados no namespace localizado da localidade da conexão atual.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="2c6a6-116">Se não for definido, a função recuperará somente os qualificadores armazenados no namespace imediato.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="2c6a6-117">0</span><span class="sxs-lookup"><span data-stu-id="2c6a6-117">0</span></span> | <span data-ttu-id="2c6a6-118">A enumeração inclui isso e todas as subclasses na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="2c6a6-119">1</span><span class="sxs-lookup"><span data-stu-id="2c6a6-119">1</span></span> | <span data-ttu-id="2c6a6-120">A enumeração inclui apenas instâncias puras dessa classe e exclui todas as instâncias de subclasses que fornecem propriedades não encontradas nesta classe.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="2c6a6-121">0x10</span><span class="sxs-lookup"><span data-stu-id="2c6a6-121">0x10</span></span> | <span data-ttu-id="2c6a6-122">O sinalizador causa uma chamada de semisynchronous.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="2c6a6-123">0x20</span><span class="sxs-lookup"><span data-stu-id="2c6a6-123">0x20</span></span> | <span data-ttu-id="2c6a6-124">A função retorna um enumerador somente encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="2c6a6-125">Normalmente, enumeradores somente de encaminhamento são mais rápidos e usam menos memória do que enumeradores convencionais, mas não permitem que as chamadas [clonem](clone.md).</span><span class="sxs-lookup"><span data-stu-id="2c6a6-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="2c6a6-126">0</span><span class="sxs-lookup"><span data-stu-id="2c6a6-126">0</span></span> | <span data-ttu-id="2c6a6-127">O WMI retém ponteiros para objetos na enumeração até que sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="2c6a6-128">Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para obter o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="2c6a6-129">no Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="2c6a6-130">Caso contrário, é um ponteiro para uma instância de [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) que pode ser usada pelo provedor que está fornecendo as instâncias solicitadas.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="2c6a6-131">fora Recebe o ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="2c6a6-132">no O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="2c6a6-133">no O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="2c6a6-134">no Um ponteiro para um objeto [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="2c6a6-135">no O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-135">[in] The user name.</span></span> <span data-ttu-id="2c6a6-136">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="2c6a6-137">no A senha.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-137">[in] The password.</span></span> <span data-ttu-id="2c6a6-138">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="2c6a6-139">no O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-139">[in] The domain name of the user.</span></span> <span data-ttu-id="2c6a6-140">Consulte a função [ConnectServerWmi](connectserverwmi.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="2c6a6-141">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2c6a6-141">Return value</span></span>

<span data-ttu-id="2c6a6-142">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="2c6a6-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2c6a6-143">Constante</span><span class="sxs-lookup"><span data-stu-id="2c6a6-143">Constant</span></span>  |<span data-ttu-id="2c6a6-144">Valor</span><span class="sxs-lookup"><span data-stu-id="2c6a6-144">Value</span></span>  |<span data-ttu-id="2c6a6-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c6a6-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="2c6a6-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="2c6a6-146">0x80041003</span></span> | <span data-ttu-id="2c6a6-147">O usuário não tem permissão para exibir instâncias da classe especificada.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="2c6a6-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2c6a6-148">0x80041001</span></span> | <span data-ttu-id="2c6a6-149">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="2c6a6-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="2c6a6-150">0x80041010</span></span> | <span data-ttu-id="2c6a6-151">`strFilter` não existe.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2c6a6-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2c6a6-152">0x80041008</span></span> | <span data-ttu-id="2c6a6-153">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2c6a6-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2c6a6-154">0x80041006</span></span> | <span data-ttu-id="2c6a6-155">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="2c6a6-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="2c6a6-156">0x80041033</span></span> | <span data-ttu-id="2c6a6-157">O WMI provavelmente foi interrompido e reiniciado.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="2c6a6-158">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="2c6a6-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="2c6a6-159">0x80041015</span></span> | <span data-ttu-id="2c6a6-160">O link RPC (chamada de procedimento remoto) entre o processo atual e o WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2c6a6-161">0</span><span class="sxs-lookup"><span data-stu-id="2c6a6-161">0</span></span> | <span data-ttu-id="2c6a6-162">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="2c6a6-163">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c6a6-163">Remarks</span></span>

<span data-ttu-id="2c6a6-164">Essa função encapsula uma chamada para o método [IWbemServices:: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) .</span><span class="sxs-lookup"><span data-stu-id="2c6a6-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="2c6a6-165">Observe que o enumerador retornado pode ter zero elementos.</span><span class="sxs-lookup"><span data-stu-id="2c6a6-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="2c6a6-166">Se a chamada de função falhar, você poderá obter informações adicionais sobre o erro chamando a função [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="2c6a6-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c6a6-167">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c6a6-167">Requirements</span></span>

<span data-ttu-id="2c6a6-168">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c6a6-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="2c6a6-169">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2c6a6-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="2c6a6-170">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2c6a6-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2c6a6-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c6a6-171">See also</span></span>

- [<span data-ttu-id="2c6a6-172">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="2c6a6-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
