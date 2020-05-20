---
title: Método ISymUnmanagedReader::GetMethodByVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 60fbccabd21fb8bee118689a524efa9031bb2124
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614988"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="23c46-102">Método ISymUnmanagedReader::GetMethodByVersion</span><span class="sxs-lookup"><span data-stu-id="23c46-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="23c46-103">Obtém um método de leitor de símbolo, dado um token de método e um número de versão de edição e cópia.</span><span class="sxs-lookup"><span data-stu-id="23c46-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="23c46-104">Os números de versão começam em 1 e são incrementados cada vez que o método é alterado como resultado de uma operação de edição e cópia.</span><span class="sxs-lookup"><span data-stu-id="23c46-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23c46-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23c46-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23c46-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="23c46-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="23c46-107">no O token do método.</span><span class="sxs-lookup"><span data-stu-id="23c46-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="23c46-108">no A versão do método.</span><span class="sxs-lookup"><span data-stu-id="23c46-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="23c46-109">fora Um ponteiro para a interface retornada.</span><span class="sxs-lookup"><span data-stu-id="23c46-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23c46-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="23c46-110">Return Value</span></span>  
 <span data-ttu-id="23c46-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="23c46-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23c46-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="23c46-112">Requirements</span></span>  
 <span data-ttu-id="23c46-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="23c46-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c46-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="23c46-114">See also</span></span>

- [<span data-ttu-id="23c46-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="23c46-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
