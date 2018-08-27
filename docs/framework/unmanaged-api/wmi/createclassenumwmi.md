---
title: Função CreateClassEnumWmi (referência de API não gerenciada)
description: A função CreateClassEnumWmi retorna um enumerador para todas as classes que atendem aos critérios especificados.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b38e4753105932d2464bf78797a6979aeb0a0aee
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2018
ms.locfileid: "42908177"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="5a2e5-103">Função CreateClassEnumWmi</span><span class="sxs-lookup"><span data-stu-id="5a2e5-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="5a2e5-104">Retorna um enumerador para todas as classes que satisfaçam os critérios de seleção especificados.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="5a2e5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a2e5-105">Syntax</span></span>  
  
```  
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

## <a name="parameters"></a><span data-ttu-id="5a2e5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5a2e5-106">Parameters</span></span>

`strSuperclass`    
<span data-ttu-id="5a2e5-107">[in] Se não for `null` ou em branco, especifica o nome de uma classe pai; o enumerador os retorna apenas as subclasses dessa classe.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="5a2e5-108">Se ele estiver `null` ou deixe em branco e `lFlags` é WBEM_FLAG_SHALLOW, retorna apenas classes de nível superior (classes sem classe pai).</span><span class="sxs-lookup"><span data-stu-id="5a2e5-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="5a2e5-109">Se ele estiver `null` ou deixe em branco e `lFlags` é `WBEM_FLAG_DEEP`, retorna todas as classes no namespace.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`   
<span data-ttu-id="5a2e5-110">[in] Uma combinação de sinalizadores que afetam o comportamento dessa função.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="5a2e5-111">Os seguintes valores são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="5a2e5-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span> 

|<span data-ttu-id="5a2e5-112">Constante</span><span class="sxs-lookup"><span data-stu-id="5a2e5-112">Constant</span></span>  |<span data-ttu-id="5a2e5-113">Valor</span><span class="sxs-lookup"><span data-stu-id="5a2e5-113">Value</span></span>  |<span data-ttu-id="5a2e5-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a2e5-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="5a2e5-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="5a2e5-115">0x20000</span></span> | <span data-ttu-id="5a2e5-116">Se definido, a função recupera os qualificadores corrigidos armazenados no namespace localizado da localidade da conexão atual.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="5a2e5-117">Se não for definido, a função recupera somente os qualificadores armazenados no namespace de imediato.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="5a2e5-118">0</span><span class="sxs-lookup"><span data-stu-id="5a2e5-118">0</span></span> | <span data-ttu-id="5a2e5-119">A enumeração inclui todas as subclasses na hierarquia, mas não essa classe.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="5a2e5-120">1</span><span class="sxs-lookup"><span data-stu-id="5a2e5-120">1</span></span> | <span data-ttu-id="5a2e5-121">A enumeração inclui apenas puras instâncias dessa classe e exclui todas as instâncias de subclasses que fornecem propriedades não encontradas nessa classe.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="5a2e5-122">0x10</span><span class="sxs-lookup"><span data-stu-id="5a2e5-122">0x10</span></span> | <span data-ttu-id="5a2e5-123">O sinalizador faz com que uma chamada semissíncrona.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="5a2e5-124">0x20</span><span class="sxs-lookup"><span data-stu-id="5a2e5-124">0x20</span></span> | <span data-ttu-id="5a2e5-125">A função retorna um enumerador de somente avanço.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="5a2e5-126">Normalmente, os enumeradores de somente avanço são mais rápidos e usam menos memória do que os enumeradores convencionais, mas eles não permitem chamadas para [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="5a2e5-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="5a2e5-127">0</span><span class="sxs-lookup"><span data-stu-id="5a2e5-127">0</span></span> | <span data-ttu-id="5a2e5-128">WMI mantém ponteiros para objetos no enumration até que eles sejam liberados.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-128">WMI retains pointers to objects in the enumration until they are released.</span></span> | 

<span data-ttu-id="5a2e5-129">Os sinalizadores recomendados são `WBEM_FLAG_RETURN_IMMEDIATELY` e `WBEM_FLAG_FORWARD_ONLY` para melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`  
<span data-ttu-id="5a2e5-130">[in] Normalmente, esse valor é `null`.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="5a2e5-131">Caso contrário, ele é um ponteiro para um [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instância que pode ser usada pelo provedor que está fornecendo as classes solicitadas.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span> 

`ppEnum`  
<span data-ttu-id="5a2e5-132">[out] Recebe o ponteiro para o enumerador.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`  
<span data-ttu-id="5a2e5-133">[in] O nível de autorização.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-133">[in] The authorization level.</span></span>

<span data-ttu-id="5a2e5-134">`impLevel` [in] O nível de representação.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-134">`impLevel` [in] The impersonation level.</span></span>

`pCurrentNamespace`   
<span data-ttu-id="5a2e5-135">[in] Um ponteiro para um [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objeto que representa o namespace atual.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`   
<span data-ttu-id="5a2e5-136">[in] O nome de usuário.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-136">[in] The user name.</span></span> <span data-ttu-id="5a2e5-137">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`   
<span data-ttu-id="5a2e5-138">[in] A senha.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-138">[in] The password.</span></span> <span data-ttu-id="5a2e5-139">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`   
<span data-ttu-id="5a2e5-140">[in] O nome de domínio do usuário.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-140">[in] The domain name of the user.</span></span> <span data-ttu-id="5a2e5-141">Consulte a [ConnectServerWmi](connectserverwmi.md) função para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="5a2e5-142">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="5a2e5-142">Return value</span></span>

<span data-ttu-id="5a2e5-143">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="5a2e5-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="5a2e5-144">Constante</span><span class="sxs-lookup"><span data-stu-id="5a2e5-144">Constant</span></span>  |<span data-ttu-id="5a2e5-145">Valor</span><span class="sxs-lookup"><span data-stu-id="5a2e5-145">Value</span></span>  |<span data-ttu-id="5a2e5-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a2e5-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="5a2e5-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="5a2e5-147">0x80041003</span></span> | <span data-ttu-id="5a2e5-148">O usuário não tem permissão para exibir um ou mais das classes que a função pode retornar.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="5a2e5-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="5a2e5-149">0x80041001</span></span> | <span data-ttu-id="5a2e5-150">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="5a2e5-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="5a2e5-151">0x80041010</span></span> | <span data-ttu-id="5a2e5-152">`strSuperClass` não existe.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="5a2e5-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="5a2e5-153">0x80041008</span></span> | <span data-ttu-id="5a2e5-154">Um parâmetro não é válido.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="5a2e5-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="5a2e5-155">0x80041006</span></span> | <span data-ttu-id="5a2e5-156">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="5a2e5-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="5a2e5-157">0x80041033</span></span> | <span data-ttu-id="5a2e5-158">WMI foi provavelmente interrompido e reiniciar.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="5a2e5-159">Chame [ConnectServerWmi](connectserverwmi.md) novamente.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="5a2e5-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="5a2e5-160">0x80041015</span></span> | <span data-ttu-id="5a2e5-161">O link RPC (chamada) de procedimento remoto entre o processo atual e a WMI falhou.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="5a2e5-162">0</span><span class="sxs-lookup"><span data-stu-id="5a2e5-162">0</span></span> | <span data-ttu-id="5a2e5-163">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-163">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="5a2e5-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="5a2e5-164">Remarks</span></span>

<span data-ttu-id="5a2e5-165">Essa função encapsula uma chamada para o [IWbemServices:: Createclassenum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) método.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="5a2e5-166">Se a chamada de função falhar, você pode obter informações adicionais sobre erros chamando o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="5a2e5-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a2e5-167">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a2e5-167">Requirements</span></span>  
 <span data-ttu-id="5a2e5-168">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a2e5-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a2e5-169">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="5a2e5-169">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="5a2e5-170">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5a2e5-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2e5-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a2e5-171">See also</span></span>  
[<span data-ttu-id="5a2e5-172">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="5a2e5-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
