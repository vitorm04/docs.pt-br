---
title: "Método GetPublicKeyToken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 230c98e85bd0aa3bd2f368965b6f7ac028e43df4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="3f741-102">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="3f741-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="3f741-103">Recupera o token de chave pública para um determinado arquivo de chave ou contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="3f741-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f741-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3f741-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f741-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3f741-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="3f741-106">Nome do arquivo da chave.</span><span class="sxs-lookup"><span data-stu-id="3f741-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="3f741-107">Nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="3f741-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="3f741-108">Endereço onde o token de chave é a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="3f741-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="3f741-109">Especifica o tamanho, em bytes, do buffer indicado pelo `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="3f741-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="3f741-110">No retorno, contém o número real de bytes usados.</span><span class="sxs-lookup"><span data-stu-id="3f741-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f741-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3f741-111">Return Value</span></span>  
 <span data-ttu-id="3f741-112">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="3f741-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f741-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f741-113">Requirements</span></span>  
 <span data-ttu-id="3f741-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="3f741-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f741-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f741-115">See Also</span></span>  
 [<span data-ttu-id="3f741-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="3f741-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3f741-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="3f741-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3f741-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="3f741-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
