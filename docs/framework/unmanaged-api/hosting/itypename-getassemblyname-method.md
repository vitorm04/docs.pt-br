---
title: Método ITypeName::GetAssemblyName
ms.date: 03/30/2017
api_name:
- ITypeName.GetAssemblyName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetAssemblyName
helpviewer_keywords:
- ITypeName::GetAssemblyName method [.NET Framework hosting]
- GetAssemblyName method [.NET Framework hosting]
ms.assetid: 97801d99-f5f1-4a30-882f-959827093fac
topic_type:
- apiref
ms.openlocfilehash: 0c8f540e5d835b4874cc55b789804d0ce30f208d
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842199"
---
# <a name="itypenamegetassemblyname-method"></a><span data-ttu-id="93b34-102">Método ITypeName::GetAssemblyName</span><span class="sxs-lookup"><span data-stu-id="93b34-102">ITypeName::GetAssemblyName Method</span></span>
<span data-ttu-id="93b34-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="93b34-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b34-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93b34-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyName (  
    [out, retval] BSTR* rgbszAssemblyNames  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="93b34-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93b34-105">Requirements</span></span>  
 <span data-ttu-id="93b34-106">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93b34-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b34-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="93b34-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93b34-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="93b34-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93b34-109">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b34-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b34-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93b34-110">See also</span></span>

- [<span data-ttu-id="93b34-111">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="93b34-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
