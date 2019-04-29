---
title: Método GetAssemblyRefHash
ms.date: 03/30/2017
api_name:
- IALink.GetAssemblyRefHash
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetAssemblyRefHash
helpviewer_keywords:
- GetAssemblyRefHash method
ms.assetid: 091a18bd-e901-46f6-b999-74d71c8a7c41
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fa8d42f9e849db6a02f6c62b37e04cf5dee016e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789851"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="9066f-102">Método GetAssemblyRefHash</span><span class="sxs-lookup"><span data-stu-id="9066f-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="9066f-103">Recupera um blob de hash para um determinado assembly.</span><span class="sxs-lookup"><span data-stu-id="9066f-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9066f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9066f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9066f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9066f-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="9066f-106">ID do assembly ao qual o hash se referem.</span><span class="sxs-lookup"><span data-stu-id="9066f-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="9066f-107">Recebe o blob de hash resultante.</span><span class="sxs-lookup"><span data-stu-id="9066f-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="9066f-108">Recebe o tamanho, em bytes, do blob de hash.</span><span class="sxs-lookup"><span data-stu-id="9066f-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9066f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9066f-109">Return Value</span></span>  
 <span data-ttu-id="9066f-110">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="9066f-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9066f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9066f-111">Requirements</span></span>  
 <span data-ttu-id="9066f-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="9066f-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9066f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9066f-113">See also</span></span>

- [<span data-ttu-id="9066f-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9066f-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9066f-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9066f-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9066f-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9066f-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
