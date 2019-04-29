---
title: Método ISymUnmanagedSourceServerModule::GetSourceServerData
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea8052152b08732906c707648f361bba4d83a276
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761553"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="004b6-102">Método ISymUnmanagedSourceServerModule::GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="004b6-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="004b6-103">Retorna os dados do servidor de origem para o módulo.</span><span class="sxs-lookup"><span data-stu-id="004b6-103">Returns the source server data for the module.</span></span> <span data-ttu-id="004b6-104">O chamador deve liberar recursos por meio `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="004b6-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="004b6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="004b6-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="004b6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="004b6-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="004b6-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em bytes, dos dados do servidor de origem.</span><span class="sxs-lookup"><span data-stu-id="004b6-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="004b6-108">[out] Um ponteiro para retornado `pDataByteCount` valor.</span><span class="sxs-lookup"><span data-stu-id="004b6-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="004b6-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="004b6-109">Return Value</span></span>  
 <span data-ttu-id="004b6-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="004b6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="004b6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="004b6-111">Requirements</span></span>  
 <span data-ttu-id="004b6-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="004b6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="004b6-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="004b6-113">See also</span></span>

- [<span data-ttu-id="004b6-114">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="004b6-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
