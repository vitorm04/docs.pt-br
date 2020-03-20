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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177264"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="e73c6-102">Método IMetaDataImport::GetEventProps</span><span class="sxs-lookup"><span data-stu-id="e73c6-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="e73c6-103">Obtém informações de metadados para o evento representado pelo token de evento especificado, incluindo o tipo de declaração, os métodos de adicionar e remover para delegados e quaisquer sinalizadores e outros dados associados.</span><span class="sxs-lookup"><span data-stu-id="e73c6-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e73c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e73c6-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="e73c6-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="e73c6-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="e73c6-106">[em] O token de metadados do evento representando o evento para obter metadados para.</span><span class="sxs-lookup"><span data-stu-id="e73c6-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="e73c6-107">[fora] Um ponteiro para o token TypeDef representando a classe que declara o evento.</span><span class="sxs-lookup"><span data-stu-id="e73c6-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="e73c6-108">[fora] O nome do evento `ev`referenciado por .</span><span class="sxs-lookup"><span data-stu-id="e73c6-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="e73c6-109">[em] O comprimento solicitado em `szEvent`caracteres amplos de .</span><span class="sxs-lookup"><span data-stu-id="e73c6-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="e73c6-110">[fora] O comprimento retornado em `szEvent`caracteres largos de .</span><span class="sxs-lookup"><span data-stu-id="e73c6-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="e73c6-111">[fora] Um ponteiro para um token de metadados TypeRef ou TypeDef representando o <xref:System.Delegate> tipo do evento.</span><span class="sxs-lookup"><span data-stu-id="e73c6-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="e73c6-112">[fora] Um ponteiro para o token de metadados representando o método que adiciona manipuladores para o evento.</span><span class="sxs-lookup"><span data-stu-id="e73c6-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="e73c6-113">[fora] Um ponteiro para o token de metadados representando o método que remove manipuladores para o evento.</span><span class="sxs-lookup"><span data-stu-id="e73c6-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="e73c6-114">[fora] Um ponteiro para o token de metadados representando o método que levanta o evento.</span><span class="sxs-lookup"><span data-stu-id="e73c6-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="e73c6-115">[fora] Uma matriz de ponteiros de token para outros métodos associados ao evento.</span><span class="sxs-lookup"><span data-stu-id="e73c6-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e73c6-116">[em] O tamanho máximo `rmdOtherMethod` da matriz.</span><span class="sxs-lookup"><span data-stu-id="e73c6-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="e73c6-117">[fora] O número de tokens `rmdOtherMethod`retornou em .</span><span class="sxs-lookup"><span data-stu-id="e73c6-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e73c6-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e73c6-118">Requirements</span></span>  
 <span data-ttu-id="e73c6-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e73c6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e73c6-120">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e73c6-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e73c6-121">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e73c6-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e73c6-122">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e73c6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73c6-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="e73c6-123">See also</span></span>

- [<span data-ttu-id="e73c6-124">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="e73c6-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e73c6-125">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="e73c6-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
