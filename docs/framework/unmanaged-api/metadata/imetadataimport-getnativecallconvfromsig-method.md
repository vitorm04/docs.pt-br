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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 752dcf90f790d6403c37fcee377c35656b655b36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491059"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="50cab-102">Método IMetaDataImport::GetNativeCallConvFromSig</span><span class="sxs-lookup"><span data-stu-id="50cab-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="50cab-103">Obtém o nativo convenção de chamada para o método que é representado pelo ponteiro de assinatura especificada.</span><span class="sxs-lookup"><span data-stu-id="50cab-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50cab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50cab-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50cab-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="50cab-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="50cab-106">[in] Um ponteiro para a assinatura de metadados do método para retornar para a convenção de chamada.</span><span class="sxs-lookup"><span data-stu-id="50cab-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="50cab-107">[in] O tamanho em bytes do `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="50cab-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="50cab-108">[out] Um ponteiro para a convenção de chamada nativa.</span><span class="sxs-lookup"><span data-stu-id="50cab-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50cab-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50cab-109">Requirements</span></span>  
 <span data-ttu-id="50cab-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50cab-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50cab-111">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="50cab-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="50cab-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="50cab-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="50cab-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50cab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50cab-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50cab-114">See also</span></span>
- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="50cab-115">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="50cab-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="50cab-116">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="50cab-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
