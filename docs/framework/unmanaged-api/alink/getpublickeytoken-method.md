---
title: Método GetPublicKeyToken
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 851ff82a539ce354d5507e829d8c461a0f2494ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729467"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="30562-102">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="30562-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="30562-103">Recupera o token de chave pública para um determinado arquivo de chave ou contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="30562-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30562-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30562-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30562-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30562-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="30562-106">Nome do arquivo da chave.</span><span class="sxs-lookup"><span data-stu-id="30562-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="30562-107">Nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="30562-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="30562-108">Endereço no qual o token de chave deve ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="30562-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="30562-109">Especifica o tamanho, em bytes, do buffer indicado pelo `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="30562-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="30562-110">Após o retorno, contém o número real de bytes usados.</span><span class="sxs-lookup"><span data-stu-id="30562-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30562-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="30562-111">Return Value</span></span>  
 <span data-ttu-id="30562-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="30562-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30562-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30562-113">Requirements</span></span>  
 <span data-ttu-id="30562-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="30562-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30562-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30562-115">See also</span></span>
- [<span data-ttu-id="30562-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="30562-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="30562-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="30562-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="30562-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="30562-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
