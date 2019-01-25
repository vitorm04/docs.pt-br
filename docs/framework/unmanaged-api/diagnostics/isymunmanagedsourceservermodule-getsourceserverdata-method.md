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
ms.openlocfilehash: 71251af116fc8d634b822e1daa49d90e91fec6f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648817"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="22f2e-102">Método ISymUnmanagedSourceServerModule::GetSourceServerData</span><span class="sxs-lookup"><span data-stu-id="22f2e-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="22f2e-103">Retorna os dados do servidor de origem para o módulo.</span><span class="sxs-lookup"><span data-stu-id="22f2e-103">Returns the source server data for the module.</span></span> <span data-ttu-id="22f2e-104">O chamador deve liberar recursos por meio `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="22f2e-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f2e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22f2e-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22f2e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22f2e-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="22f2e-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em bytes, dos dados do servidor de origem.</span><span class="sxs-lookup"><span data-stu-id="22f2e-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="22f2e-108">[out] Um ponteiro para retornado `pDataByteCount` valor.</span><span class="sxs-lookup"><span data-stu-id="22f2e-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22f2e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="22f2e-109">Return Value</span></span>  
 <span data-ttu-id="22f2e-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="22f2e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22f2e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22f2e-111">Requirements</span></span>  
 <span data-ttu-id="22f2e-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="22f2e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22f2e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22f2e-113">See also</span></span>
- [<span data-ttu-id="22f2e-114">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="22f2e-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
