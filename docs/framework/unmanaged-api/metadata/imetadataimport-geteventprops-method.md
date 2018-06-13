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
ms.openlocfilehash: 6ac1ecb73257782888c963082953ed243177a86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448798"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="093f7-102">Método IMetaDataImport::GetEventProps</span><span class="sxs-lookup"><span data-stu-id="093f7-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="093f7-103">Obtém informações de metadados para o evento representado pelo token de evento especificado, incluindo o tipo de declaração, adicionar e remover métodos para delegados e os sinalizadores e outros dados associados.</span><span class="sxs-lookup"><span data-stu-id="093f7-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="093f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="093f7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="093f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="093f7-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="093f7-106">[in] O token de metadados de evento que representa o evento para obter metadados.</span><span class="sxs-lookup"><span data-stu-id="093f7-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="093f7-107">[out] Um ponteiro para o token de TypeDef que representa a classe que declara o evento.</span><span class="sxs-lookup"><span data-stu-id="093f7-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="093f7-108">[out] O nome do evento referenciado por `ev`.</span><span class="sxs-lookup"><span data-stu-id="093f7-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="093f7-109">[in] O tamanho solicitado em caracteres largos de `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="093f7-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="093f7-110">[out] O comprimento retornado em caracteres largos de `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="093f7-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="093f7-111">[out] Um ponteiro para um TypeRef ou TypeDef metadados token que representa o <xref:System.Delegate> tipo do evento.</span><span class="sxs-lookup"><span data-stu-id="093f7-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="093f7-112">[out] Um ponteiro para o token de metadados que representa o método que adiciona manipuladores para o evento.</span><span class="sxs-lookup"><span data-stu-id="093f7-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="093f7-113">[out] Um ponteiro para o token de metadados que representa o método que remove os manipuladores para o evento.</span><span class="sxs-lookup"><span data-stu-id="093f7-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="093f7-114">[out] Um ponteiro para o token de metadados que representa o método que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="093f7-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="093f7-115">[out] Uma matriz de ponteiros de token para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="093f7-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="093f7-116">[in] O tamanho máximo da `rmdOtherMethod` matriz.</span><span class="sxs-lookup"><span data-stu-id="093f7-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="093f7-117">[out] O número de tokens retornados em `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="093f7-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="093f7-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="093f7-118">Requirements</span></span>  
 <span data-ttu-id="093f7-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="093f7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="093f7-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="093f7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="093f7-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="093f7-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="093f7-122">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="093f7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="093f7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="093f7-123">See Also</span></span>  
 [<span data-ttu-id="093f7-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="093f7-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="093f7-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="093f7-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
