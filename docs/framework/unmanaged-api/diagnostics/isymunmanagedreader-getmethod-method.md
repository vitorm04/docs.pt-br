---
title: Método ISymUnmanagedReader::GetMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 864acb07797676c825afe62321b0d65e37938fa6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615001"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="4f1ca-102">Método ISymUnmanagedReader::GetMethod</span><span class="sxs-lookup"><span data-stu-id="4f1ca-102">ISymUnmanagedReader::GetMethod Method</span></span>
<span data-ttu-id="4f1ca-103">Obtém um método de leitor de símbolo, dado um token de método.</span><span class="sxs-lookup"><span data-stu-id="4f1ca-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f1ca-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f1ca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f1ca-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4f1ca-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="4f1ca-106">no O token do método.</span><span class="sxs-lookup"><span data-stu-id="4f1ca-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="4f1ca-107">fora Um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="4f1ca-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f1ca-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4f1ca-108">Return Value</span></span>  
 <span data-ttu-id="4f1ca-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4f1ca-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f1ca-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f1ca-110">Requirements</span></span>  
 <span data-ttu-id="4f1ca-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4f1ca-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1ca-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f1ca-112">See also</span></span>

- [<span data-ttu-id="4f1ca-113">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="4f1ca-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
