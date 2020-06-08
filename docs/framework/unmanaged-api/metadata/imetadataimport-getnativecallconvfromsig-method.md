---
title: Método IMetaDataImport::GetNativeCallConvFromSig
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
ms.openlocfilehash: 44439eda62f85c32893b73f17bd057195cf6b2e1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503543"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="d9d43-102">Método IMetaDataImport::GetNativeCallConvFromSig</span><span class="sxs-lookup"><span data-stu-id="d9d43-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="d9d43-103">Obtém a Convenção de chamada nativa para o método representado pelo ponteiro de assinatura especificado.</span><span class="sxs-lookup"><span data-stu-id="d9d43-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9d43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9d43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9d43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d9d43-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="d9d43-106">no Um ponteiro para a assinatura de metadados do método para o qual retornar a Convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="d9d43-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d9d43-107">no O tamanho em bytes de `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="d9d43-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="d9d43-108">fora Um ponteiro para a Convenção de chamada nativa.</span><span class="sxs-lookup"><span data-stu-id="d9d43-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9d43-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d9d43-109">Requirements</span></span>  
 <span data-ttu-id="d9d43-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9d43-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d43-111">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d9d43-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9d43-112">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d9d43-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d9d43-113">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d43-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d43-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9d43-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="d9d43-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="d9d43-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d9d43-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="d9d43-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
