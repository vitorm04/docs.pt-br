---
title: Função CoInitializeEE
ms.date: 03/30/2017
api_name:
- CoInitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
ms.openlocfilehash: 57508a2df3a49c39d25347f2a3038442c37278da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616756"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="b1939-102">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="b1939-102">CoInitializeEE Function</span></span>
<span data-ttu-id="b1939-103">Garante que o mecanismo de execução de Common Language Runtime seja carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="b1939-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="b1939-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="b1939-104">This function is deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="b1939-105">Em vez disso, use o método [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b1939-105">Use the [ICLRRuntimeHost::Start](iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1939-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1939-106">Syntax</span></span>  
  
```cpp  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1939-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b1939-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="b1939-108">no Uma das constantes de enumeração [COINITIEE](../metadata/coinitiee-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="b1939-108">[in] One of the [COINITIEE](../metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1939-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b1939-109">Return Value</span></span>  
 <span data-ttu-id="b1939-110">Esse método retorna códigos de erro COM padrão, conforme definido em Winerror. h, e os valores na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b1939-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="b1939-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="b1939-111">Return code</span></span>|<span data-ttu-id="b1939-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1939-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="b1939-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1939-113">S_OK</span></span>|<span data-ttu-id="b1939-114">O mecanismo de execução foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="b1939-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="b1939-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b1939-115">S_FALSE</span></span>|<span data-ttu-id="b1939-116">O mecanismo de execução já está carregado.</span><span class="sxs-lookup"><span data-stu-id="b1939-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="b1939-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1939-117">E_FAIL</span></span>|<span data-ttu-id="b1939-118">Não foi possível carregar o mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="b1939-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1939-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1939-119">Remarks</span></span>  
 <span data-ttu-id="b1939-120">Esse método carregará o mecanismo de execução se ele não tiver sido carregado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="b1939-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1939-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b1939-121">Requirements</span></span>  
 <span data-ttu-id="b1939-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1939-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1939-123">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b1939-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1939-124">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1939-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1939-125">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1939-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1939-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="b1939-126">See also</span></span>

- [<span data-ttu-id="b1939-127">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="b1939-127">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
