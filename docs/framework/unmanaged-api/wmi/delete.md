---
title: Excluir função (referência de API não gerenciada)
description: A função Delete exclui a propriedade especificada e todos os seus qualificadores de uma definição de classe do CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1a26db7785a8a378fa541308ecc6aee30fa87ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049278"
---
# <a name="delete-function"></a><span data-ttu-id="14f07-103">Função Delete</span><span class="sxs-lookup"><span data-stu-id="14f07-103">Delete function</span></span>

<span data-ttu-id="14f07-104">Exclui a propriedade especificada e todos os seus qualificadores de uma definição de classe do CIM.</span><span class="sxs-lookup"><span data-stu-id="14f07-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="14f07-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14f07-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="14f07-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14f07-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="14f07-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="14f07-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="14f07-108">[in] Um ponteiro para um [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instância.</span><span class="sxs-lookup"><span data-stu-id="14f07-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="14f07-109">[in] O nome da propriedade a ser excluída.</span><span class="sxs-lookup"><span data-stu-id="14f07-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="14f07-110">`wszName` deve ser um ponteiro para um válido `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="14f07-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="14f07-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="14f07-111">Return value</span></span>

<span data-ttu-id="14f07-112">Os seguintes valores retornados por essa função são definidos na *WbemCli.h* arquivo de cabeçalho, ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="14f07-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="14f07-113">Constante</span><span class="sxs-lookup"><span data-stu-id="14f07-113">Constant</span></span>  |<span data-ttu-id="14f07-114">Valor</span><span class="sxs-lookup"><span data-stu-id="14f07-114">Value</span></span>  |<span data-ttu-id="14f07-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="14f07-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="14f07-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="14f07-116">0x80041001</span></span> | <span data-ttu-id="14f07-117">Ocorreu um erro não especificado.</span><span class="sxs-lookup"><span data-stu-id="14f07-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="14f07-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="14f07-118">0x80041016</span></span> | <span data-ttu-id="14f07-119">A propriedade não pode ser excluída.</span><span class="sxs-lookup"><span data-stu-id="14f07-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="14f07-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="14f07-120">0x80041008</span></span> | <span data-ttu-id="14f07-121">`wszName` é inválido.</span><span class="sxs-lookup"><span data-stu-id="14f07-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="14f07-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="14f07-122">0x80041002</span></span> | <span data-ttu-id="14f07-123">A propriedade especificada não existe.</span><span class="sxs-lookup"><span data-stu-id="14f07-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="14f07-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="14f07-124">0x80041006</span></span> | <span data-ttu-id="14f07-125">Não há memória suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="14f07-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="14f07-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="14f07-126">0x8004101c</span></span> | <span data-ttu-id="14f07-127">A propriedade é herdada de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="14f07-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="14f07-128">A propriedade é uma propriedade do sistema.</span><span class="sxs-lookup"><span data-stu-id="14f07-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="14f07-129">0</span><span class="sxs-lookup"><span data-stu-id="14f07-129">0</span></span> | <span data-ttu-id="14f07-130">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="14f07-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="14f07-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="14f07-131">0x80041030</span></span> | <span data-ttu-id="14f07-132">A função excluída de um valor padrão de substituição para a classe atual.</span><span class="sxs-lookup"><span data-stu-id="14f07-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="14f07-133">O valor padrão para essa propriedade na classe pai foi reativado.</span><span class="sxs-lookup"><span data-stu-id="14f07-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="14f07-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="14f07-134">Remarks</span></span>

<span data-ttu-id="14f07-135">Essa função encapsula uma chamada para o [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) método.</span><span class="sxs-lookup"><span data-stu-id="14f07-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="14f07-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14f07-136">Requirements</span></span>

<span data-ttu-id="14f07-137">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14f07-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="14f07-138">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="14f07-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="14f07-139">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="14f07-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="14f07-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14f07-140">See also</span></span>

- [<span data-ttu-id="14f07-141">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="14f07-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)