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
ms.openlocfilehash: ccf60d067af356dda1870a2fb1dcca21966f16a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401480"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="34cb9-102">Método GetAssemblyRefHash</span><span class="sxs-lookup"><span data-stu-id="34cb9-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="34cb9-103">Recupera um blob de hash para um determinado assembly.</span><span class="sxs-lookup"><span data-stu-id="34cb9-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34cb9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="34cb9-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34cb9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="34cb9-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="34cb9-106">ID do assembly ao qual o hash fará referência.</span><span class="sxs-lookup"><span data-stu-id="34cb9-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="34cb9-107">Recebe o blob de hash resultante.</span><span class="sxs-lookup"><span data-stu-id="34cb9-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="34cb9-108">Recebe o tamanho, em bytes, do blob de hash.</span><span class="sxs-lookup"><span data-stu-id="34cb9-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34cb9-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="34cb9-109">Return Value</span></span>  
 <span data-ttu-id="34cb9-110">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="34cb9-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34cb9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="34cb9-111">Requirements</span></span>  
 <span data-ttu-id="34cb9-112">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="34cb9-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34cb9-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34cb9-113">See Also</span></span>  
 [<span data-ttu-id="34cb9-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="34cb9-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="34cb9-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="34cb9-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="34cb9-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="34cb9-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
