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
ms.openlocfilehash: c68f43ce2f79ee6e4ec44ce4b2f0dbfb1c1185fa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433879"
---
# <a name="getassemblyrefhash-method"></a><span data-ttu-id="01cff-102">Método GetAssemblyRefHash</span><span class="sxs-lookup"><span data-stu-id="01cff-102">GetAssemblyRefHash Method</span></span>
<span data-ttu-id="01cff-103">Recupera um blob de hash para um determinado assembly.</span><span class="sxs-lookup"><span data-stu-id="01cff-103">Retrieves a hash blob for a given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01cff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="01cff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefHash(  
    mdToken FileToken,  
    const void** ppvHash,  
    DWORD* pcbHash  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="01cff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="01cff-105">Parameters</span></span>  
 `FileToken`  
 <span data-ttu-id="01cff-106">ID do assembly ao qual o hash fará referência.</span><span class="sxs-lookup"><span data-stu-id="01cff-106">ID of assembly to which the hash will refer.</span></span>  
  
 `ppvHash`  
 <span data-ttu-id="01cff-107">Recebe o blob de hash resultante.</span><span class="sxs-lookup"><span data-stu-id="01cff-107">Receives the resulting hash blob.</span></span>  
  
 `pcbHash`  
 <span data-ttu-id="01cff-108">Recebe o tamanho, em bytes, do blob de hash.</span><span class="sxs-lookup"><span data-stu-id="01cff-108">Receives size, in bytes, of hash blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01cff-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="01cff-109">Return Value</span></span>  
 <span data-ttu-id="01cff-110">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="01cff-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01cff-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="01cff-111">Requirements</span></span>  
 <span data-ttu-id="01cff-112">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="01cff-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01cff-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01cff-113">See also</span></span>

- [<span data-ttu-id="01cff-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="01cff-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="01cff-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="01cff-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="01cff-116">API do ALink</span><span class="sxs-lookup"><span data-stu-id="01cff-116">ALink API</span></span>](index.md)
