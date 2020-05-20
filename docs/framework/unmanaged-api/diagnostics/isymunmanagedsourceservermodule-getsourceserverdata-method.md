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
ms.openlocfilehash: 9a3a6c07a9cace0ac9834cdb05925a301285204c
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615313"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="a9b38-102">Método ISymUnmanagedSourceServerModule::GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="a9b38-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="a9b38-103">Retorna os dados do servidor de origem para o módulo.</span><span class="sxs-lookup"><span data-stu-id="a9b38-103">Returns the source server data for the module.</span></span> <span data-ttu-id="a9b38-104">O chamador deve liberar recursos usando o `CoTaskMemFree` .</span><span class="sxs-lookup"><span data-stu-id="a9b38-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9b38-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9b38-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9b38-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9b38-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="a9b38-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em bytes, dos dados do servidor de origem.</span><span class="sxs-lookup"><span data-stu-id="a9b38-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="a9b38-108">fora Um ponteiro para o `pDataByteCount` valor retornado.</span><span class="sxs-lookup"><span data-stu-id="a9b38-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9b38-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a9b38-109">Return Value</span></span>  
 <span data-ttu-id="a9b38-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a9b38-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9b38-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a9b38-111">Requirements</span></span>  
 <span data-ttu-id="a9b38-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a9b38-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9b38-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="a9b38-113">See also</span></span>

- [<span data-ttu-id="a9b38-114">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="a9b38-114">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)
