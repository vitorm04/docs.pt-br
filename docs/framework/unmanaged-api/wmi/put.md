---
title: Função put (referência de API não gerenciada)
description: A função Put atribui um novo valor a uma propriedade nomeada.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798403"
---
# <a name="put-function"></a><span data-ttu-id="16715-103">Função put</span><span class="sxs-lookup"><span data-stu-id="16715-103">Put function</span></span>

<span data-ttu-id="16715-104">Define uma propriedade nomeada para um novo valor.</span><span class="sxs-lookup"><span data-stu-id="16715-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="16715-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16715-105">Syntax</span></span>

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a><span data-ttu-id="16715-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16715-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="16715-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="16715-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="16715-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="16715-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="16715-109">no O nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="16715-109">[in] The name of the property.</span></span> <span data-ttu-id="16715-110">O parâmetro não pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="16715-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="16715-111">[in] Reservado.</span><span class="sxs-lookup"><span data-stu-id="16715-111">[in] Reserved.</span></span> <span data-ttu-id="16715-112">Esse parâmetro deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="16715-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="16715-113">no Um ponteiro para um válido `VARIANT` que se torna o novo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="16715-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="16715-114">Se `pVal` `VARIANT` for `null` ou apontar para um de tipo `VT_NULL`, a propriedade será definida como `null`.</span><span class="sxs-lookup"><span data-stu-id="16715-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="16715-115">no O tipo de `VARIANT` apontado por `pVal`.</span><span class="sxs-lookup"><span data-stu-id="16715-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="16715-116">Consulte a seção [comentários](#remarks) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="16715-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="16715-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="16715-117">Return value</span></span>

<span data-ttu-id="16715-118">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="16715-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="16715-119">Constante</span><span class="sxs-lookup"><span data-stu-id="16715-119">Constant</span></span>  |<span data-ttu-id="16715-120">Valor</span><span class="sxs-lookup"><span data-stu-id="16715-120">Value</span></span>  |<span data-ttu-id="16715-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="16715-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="16715-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="16715-122">0x80041001</span></span> | <span data-ttu-id="16715-123">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="16715-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="16715-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="16715-124">0x80041008</span></span> | <span data-ttu-id="16715-125">Um ou mais parâmetros não são válidos.</span><span class="sxs-lookup"><span data-stu-id="16715-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="16715-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="16715-126">0x8004102a</span></span> | <span data-ttu-id="16715-127">O tipo de propriedade não é reconhecido.</span><span class="sxs-lookup"><span data-stu-id="16715-127">The property type is not recognized.</span></span> <span data-ttu-id="16715-128">Esse valor é retornado ao criar instâncias de classe se a classe já existir.</span><span class="sxs-lookup"><span data-stu-id="16715-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="16715-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="16715-129">0x80041006</span></span> | <span data-ttu-id="16715-130">Não há memória disponível suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="16715-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="16715-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="16715-131">0x80041005</span></span> | <span data-ttu-id="16715-132">Para instâncias: Indica que `pVal` aponta para um `VARIANT` tipo incorreto para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="16715-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="16715-133">Para definições de classe: A propriedade já existe na classe pai e o novo tipo COM é diferente do tipo COM antigo.</span><span class="sxs-lookup"><span data-stu-id="16715-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="16715-134">0</span><span class="sxs-lookup"><span data-stu-id="16715-134">0</span></span> | <span data-ttu-id="16715-135">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="16715-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="16715-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="16715-136">Remarks</span></span>

<span data-ttu-id="16715-137">Essa função encapsula uma chamada para o método [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="16715-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="16715-138">Essa função sempre substitui o valor da propriedade atual por um novo.</span><span class="sxs-lookup"><span data-stu-id="16715-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="16715-139">Se o [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) apontar para uma definição de classe `Put` , criará ou atualizará o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="16715-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="16715-140">Quando [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) aponta para uma instância CIM, `Put` o atualiza somente o valor da propriedade; `Put` não é possível criar um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="16715-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="16715-141">A `__CLASS` Propriedade do sistema só é gravável durante a criação da classe, quando não pode ser deixada em branco.</span><span class="sxs-lookup"><span data-stu-id="16715-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="16715-142">Todas as outras propriedades do sistema são somente leitura.</span><span class="sxs-lookup"><span data-stu-id="16715-142">All other system properties are read-only.</span></span>

<span data-ttu-id="16715-143">Um usuário não pode criar propriedades com nomes que comecem ou terminem com um sublinhado ("_").</span><span class="sxs-lookup"><span data-stu-id="16715-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="16715-144">Isso é reservado para classes e propriedades do sistema.</span><span class="sxs-lookup"><span data-stu-id="16715-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="16715-145">Se a propriedade definida pela `Put` função existir na classe pai, o valor padrão da propriedade será alterado, a menos que o tipo de propriedade não corresponda ao tipo de classe pai.</span><span class="sxs-lookup"><span data-stu-id="16715-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="16715-146">Se a propriedade não existir e não for uma incompatibilidade de tipos, a propriedade será criada.</span><span class="sxs-lookup"><span data-stu-id="16715-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="16715-147">Use o `vtType` parâmetro somente ao criar novas propriedades em uma definição de classe CIM `pVal` e `null` é ou aponta para `VARIANT` um de `VT_NULL`tipo.</span><span class="sxs-lookup"><span data-stu-id="16715-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="16715-148">Nesse caso, o `vType` parâmetro especifica o tipo CIM da propriedade.</span><span class="sxs-lookup"><span data-stu-id="16715-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="16715-149">Em todos os outros casos `vtType` , deve ser 0.</span><span class="sxs-lookup"><span data-stu-id="16715-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="16715-150">`vtType`também deverá ser 0 se o objeto subjacente for uma instância (mesmo se `Val` for `null`) porque o tipo da propriedade é fixo e não pode ser alterado.</span><span class="sxs-lookup"><span data-stu-id="16715-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="16715-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16715-151">Example</span></span>

<span data-ttu-id="16715-152">Para obter um exemplo, consulte o método [IWbemClassObject::P UT](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="16715-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="16715-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16715-153">Requirements</span></span>

<span data-ttu-id="16715-154">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16715-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="16715-155">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="16715-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="16715-156">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="16715-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="16715-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16715-157">See also</span></span>

- [<span data-ttu-id="16715-158">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="16715-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
