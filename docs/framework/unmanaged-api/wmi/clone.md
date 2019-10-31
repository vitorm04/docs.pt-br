---
title: Função de clonagem (referência de API não gerenciada)
description: A função Clone retorna um novo objeto que é um clone completo do atual.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c8e7781a3efe7679ef2e05747862911db88bcc5f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141621"
---
# <a name="clone-function"></a><span data-ttu-id="ccf08-103">Função Clone</span><span class="sxs-lookup"><span data-stu-id="ccf08-103">Clone function</span></span>
<span data-ttu-id="ccf08-104">Retorna um novo objeto que é uma cópia completa do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="ccf08-104">Returns a new object that is a complete clone of the current object.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ccf08-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ccf08-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a><span data-ttu-id="ccf08-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ccf08-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ccf08-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="ccf08-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ccf08-108">no Um ponteiro para uma instância de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="ccf08-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="ccf08-109">fora Um novo objeto que é uma solitário completa de `ptr`.</span><span class="sxs-lookup"><span data-stu-id="ccf08-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="ccf08-110">Esse argumento não poderá ser `null` se receber a cópia do objeto atual.</span><span class="sxs-lookup"><span data-stu-id="ccf08-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="ccf08-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ccf08-111">Return value</span></span>

<span data-ttu-id="ccf08-112">Os valores a seguir retornados por essa função são definidos no arquivo de cabeçalho *WbemCli. h* ou você pode defini-los como constantes em seu código:</span><span class="sxs-lookup"><span data-stu-id="ccf08-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ccf08-113">Constante</span><span class="sxs-lookup"><span data-stu-id="ccf08-113">Constant</span></span>  |<span data-ttu-id="ccf08-114">Valor</span><span class="sxs-lookup"><span data-stu-id="ccf08-114">Value</span></span>  |<span data-ttu-id="ccf08-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccf08-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="ccf08-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ccf08-116">0x80041001</span></span> | <span data-ttu-id="ccf08-117">Houve uma falha geral.</span><span class="sxs-lookup"><span data-stu-id="ccf08-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ccf08-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ccf08-118">0x80041008</span></span> | <span data-ttu-id="ccf08-119">`null` foi especificado como um parâmetro e não é válido nesse uso.</span><span class="sxs-lookup"><span data-stu-id="ccf08-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ccf08-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ccf08-120">0x80041006</span></span> | <span data-ttu-id="ccf08-121">Não há memória suficiente disponível para clonar o objeto.</span><span class="sxs-lookup"><span data-stu-id="ccf08-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ccf08-122">0</span><span class="sxs-lookup"><span data-stu-id="ccf08-122">0</span></span> | <span data-ttu-id="ccf08-123">A chamada de função foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ccf08-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ccf08-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="ccf08-124">Remarks</span></span>

<span data-ttu-id="ccf08-125">Essa função encapsula uma chamada para o método [IWbemClassObject:: clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="ccf08-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="ccf08-126">O objeto clonado é um objeto COM que tem uma contagem de referência de 1.</span><span class="sxs-lookup"><span data-stu-id="ccf08-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="ccf08-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ccf08-127">Requirements</span></span>  
 <span data-ttu-id="ccf08-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccf08-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf08-129">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ccf08-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ccf08-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf08-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf08-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccf08-131">See also</span></span>

- [<span data-ttu-id="ccf08-132">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="ccf08-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
