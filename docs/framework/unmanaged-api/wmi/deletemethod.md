---
title: Função DeleteMethod (referência a API não gerenciada)
description: A função DeleteMethod exclui o método especificado de uma definição de classe CIM.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4059555d74c0b0f151332ddcf9faedecf238e795
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174986"
---
# <a name="deletemethod-function"></a><span data-ttu-id="9bd0b-103">Função DeleteMethod</span><span class="sxs-lookup"><span data-stu-id="9bd0b-103">DeleteMethod function</span></span>
<span data-ttu-id="9bd0b-104">Exclui o método especificado de uma definição de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="9bd0b-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9bd0b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bd0b-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="9bd0b-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bd0b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9bd0b-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="9bd0b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9bd0b-108">[em] Um ponteiro para uma instância [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="9bd0b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="9bd0b-109">[em] O nome do método para remover da tabela de classe.</span><span class="sxs-lookup"><span data-stu-id="9bd0b-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="9bd0b-110">`wszName`deve ser um ponteiro `LPCWSTR`para um válido .</span><span class="sxs-lookup"><span data-stu-id="9bd0b-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="9bd0b-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9bd0b-111">Return value</span></span>

<span data-ttu-id="9bd0b-112">Os seguintes valores retornados por esta função são definidos no arquivo de cabeçalho *WbemCli.h,* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="9bd0b-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9bd0b-113">Constante</span><span class="sxs-lookup"><span data-stu-id="9bd0b-113">Constant</span></span>  |<span data-ttu-id="9bd0b-114">Valor</span><span class="sxs-lookup"><span data-stu-id="9bd0b-114">Value</span></span>  |<span data-ttu-id="9bd0b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bd0b-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="9bd0b-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="9bd0b-116">0x80041002</span></span> | <span data-ttu-id="9bd0b-117">O método especificado não existe.</span><span class="sxs-lookup"><span data-stu-id="9bd0b-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="9bd0b-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="9bd0b-118">0x80041006</span></span> | <span data-ttu-id="9bd0b-119">Não há memória suficiente para concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="9bd0b-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9bd0b-120">0</span><span class="sxs-lookup"><span data-stu-id="9bd0b-120">0</span></span> | <span data-ttu-id="9bd0b-121">A chamada de função foi bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="9bd0b-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="9bd0b-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd0b-122">Remarks</span></span>

<span data-ttu-id="9bd0b-123">Esta função envolve uma chamada para o método [IWbemClassObject::DeleteMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod)</span><span class="sxs-lookup"><span data-stu-id="9bd0b-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="9bd0b-124">A exclusão do método não é suportada para ponteiros [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) que apontam para instâncias CIM.</span><span class="sxs-lookup"><span data-stu-id="9bd0b-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="9bd0b-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bd0b-125">Requirements</span></span>  
 <span data-ttu-id="9bd0b-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd0b-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd0b-127">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9bd0b-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9bd0b-128">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd0b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd0b-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="9bd0b-129">See also</span></span>

- [<span data-ttu-id="9bd0b-130">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="9bd0b-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
