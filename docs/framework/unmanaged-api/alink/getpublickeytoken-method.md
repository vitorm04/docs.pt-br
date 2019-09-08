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
ms.openlocfilehash: 158ecc036d56e2ad9a3fa650677c04ebcbfd7696
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777220"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="81a8e-102">Método GetPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="81a8e-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="81a8e-103">Recupera o token de chave pública para um determinado contêiner de chave ou keyfile.</span><span class="sxs-lookup"><span data-stu-id="81a8e-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a8e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81a8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="81a8e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="81a8e-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="81a8e-106">Nome do arquivo da chave.</span><span class="sxs-lookup"><span data-stu-id="81a8e-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="81a8e-107">Nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="81a8e-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="81a8e-108">Endereço em que o token de chave deve ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="81a8e-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="81a8e-109">Especifica o tamanho, em bytes, do buffer indicado por `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="81a8e-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="81a8e-110">No retorno, contém o número real de bytes usados.</span><span class="sxs-lookup"><span data-stu-id="81a8e-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81a8e-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="81a8e-111">Return Value</span></span>  
 <span data-ttu-id="81a8e-112">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="81a8e-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a8e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81a8e-113">Requirements</span></span>  
 <span data-ttu-id="81a8e-114">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="81a8e-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a8e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81a8e-115">See also</span></span>

- [<span data-ttu-id="81a8e-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="81a8e-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="81a8e-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="81a8e-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="81a8e-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="81a8e-118">ALink API</span></span>](index.md)
