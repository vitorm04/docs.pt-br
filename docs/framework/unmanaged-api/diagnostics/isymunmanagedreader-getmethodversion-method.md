---
title: Método ISymUnmanagedReader::GetMethodVersion
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: fcaf748413321f684336543e60f735af69894b51
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436002"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="4d18e-102">Método ISymUnmanagedReader::GetMethodVersion</span><span class="sxs-lookup"><span data-stu-id="4d18e-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="4d18e-103">Obtém a versão do método.</span><span class="sxs-lookup"><span data-stu-id="4d18e-103">Gets the method version.</span></span> <span data-ttu-id="4d18e-104">A versão do método começa em 1 e é incrementada toda vez que o método é recompilado.</span><span class="sxs-lookup"><span data-stu-id="4d18e-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="4d18e-105">A recompilação pode ocorrer sem alterações no método.</span><span class="sxs-lookup"><span data-stu-id="4d18e-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d18e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d18e-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d18e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4d18e-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="4d18e-108">no O método para o qual obter a versão.</span><span class="sxs-lookup"><span data-stu-id="4d18e-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="4d18e-109">fora Um ponteiro para uma variável que recebe a versão do método.</span><span class="sxs-lookup"><span data-stu-id="4d18e-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d18e-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4d18e-110">Return Value</span></span>  
 <span data-ttu-id="4d18e-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="4d18e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d18e-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4d18e-112">Requirements</span></span>  
 <span data-ttu-id="4d18e-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4d18e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d18e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d18e-114">See also</span></span>

- [<span data-ttu-id="4d18e-115">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="4d18e-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
