---
title: "Método ISymUnmanagedReader::GetSymAttribute"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetSymAttribute
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f57d2c4541945d90b1695850311928884fdc9cc5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="d71e0-102">Método ISymUnmanagedReader::GetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="d71e0-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>
<span data-ttu-id="d71e0-103">Obtém um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="d71e0-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="d71e0-104">Ao contrário de atributos personalizados de metadados, os atributos personalizados são mantidos no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="d71e0-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71e0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d71e0-105">Syntax</span></span>  
  
```  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d71e0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d71e0-106">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="d71e0-107">[in] O token de metadados para o objeto para o qual o atributo é solicitado.</span><span class="sxs-lookup"><span data-stu-id="d71e0-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="d71e0-108">[in] Um ponteiro para a variável que indica o atributo para recuperar.</span><span class="sxs-lookup"><span data-stu-id="d71e0-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="d71e0-109">[in] O tamanho do `buffer` matriz.</span><span class="sxs-lookup"><span data-stu-id="d71e0-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="d71e0-110">[out] Um ponteiro para a variável que recebe o comprimento dos dados de atributo.</span><span class="sxs-lookup"><span data-stu-id="d71e0-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="d71e0-111">[out] Um ponteiro para a variável que recebe os dados de atributo.</span><span class="sxs-lookup"><span data-stu-id="d71e0-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d71e0-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d71e0-112">Return Value</span></span>  
 <span data-ttu-id="d71e0-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d71e0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code..</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d71e0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d71e0-114">Requirements</span></span>  
 <span data-ttu-id="d71e0-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d71e0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71e0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d71e0-116">See Also</span></span>  
 [<span data-ttu-id="d71e0-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="d71e0-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
