---
title: Método IMetaDataImport::GetEventProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f2eec9fce1909f6a83190f5ba3e99162461bbc4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492145"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="b9966-102">Método IMetaDataImport::GetEventProps</span><span class="sxs-lookup"><span data-stu-id="b9966-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="b9966-103">Obtém informações de metadados para o evento representado pelo token de evento especificado, incluindo o tipo de declaração, adicionar e remover métodos para representantes e os sinalizadores e outros dados associados.</span><span class="sxs-lookup"><span data-stu-id="b9966-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9966-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b9966-104">Syntax</span></span>  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9966-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b9966-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="b9966-106">[in] O token de metadados de evento que representa o evento para obter metadados.</span><span class="sxs-lookup"><span data-stu-id="b9966-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b9966-107">[out] Um ponteiro para o token de TypeDef que representa a classe que declara o evento.</span><span class="sxs-lookup"><span data-stu-id="b9966-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="b9966-108">[out] O nome do evento referenciado pelo `ev`.</span><span class="sxs-lookup"><span data-stu-id="b9966-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="b9966-109">[in] O comprimento solicitado em caracteres largos da `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b9966-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="b9966-110">[out] O comprimento retornado em caracteres largos da `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b9966-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="b9966-111">[out] Um ponteiro para um TypeRef ou TypeDef metadados token que representa o <xref:System.Delegate> tipo do evento.</span><span class="sxs-lookup"><span data-stu-id="b9966-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="b9966-112">[out] Um ponteiro para o token de metadados que representa o método que adiciona manipuladores para o evento.</span><span class="sxs-lookup"><span data-stu-id="b9966-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="b9966-113">[out] Um ponteiro para o token de metadados que representa o método que remove os manipuladores para o evento.</span><span class="sxs-lookup"><span data-stu-id="b9966-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="b9966-114">[out] Um ponteiro para o token de metadados que representa o método que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="b9966-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="b9966-115">[out] Uma matriz de ponteiros de token para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="b9966-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b9966-116">[in] O tamanho máximo da `rmdOtherMethod` matriz.</span><span class="sxs-lookup"><span data-stu-id="b9966-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="b9966-117">[out] O número de tokens retornado no `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b9966-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9966-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b9966-118">Requirements</span></span>  
 <span data-ttu-id="b9966-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9966-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9966-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b9966-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9966-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b9966-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9966-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9966-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9966-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9966-123">See also</span></span>
- [<span data-ttu-id="b9966-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b9966-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b9966-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b9966-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
