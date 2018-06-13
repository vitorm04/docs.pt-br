---
title: Método IMetaDataImport2::GetVersionString
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 112ddcf51a5637bb89df9479850c2a4a70d2e1d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448720"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="c7c74-102">Método IMetaDataImport2::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="c7c74-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="c7c74-103">Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.</span><span class="sxs-lookup"><span data-stu-id="c7c74-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7c74-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7c74-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7c74-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7c74-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="c7c74-106">[out] Uma matriz para armazenar a cadeia de caracteres que especifica a versão.</span><span class="sxs-lookup"><span data-stu-id="c7c74-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="c7c74-107">[in] O tamanho, em caracteres largos, do `pwzBuf` matriz.</span><span class="sxs-lookup"><span data-stu-id="c7c74-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="c7c74-108">[out] O número de caracteres largos, incluindo um terminador nulo, retornado no `pwzBuf` matriz.</span><span class="sxs-lookup"><span data-stu-id="c7c74-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7c74-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7c74-109">Remarks</span></span>  
 <span data-ttu-id="c7c74-110">O `GetVersionString` método obtém a versão criados para o escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="c7c74-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="c7c74-111">Se o escopo nunca tiver sido salvo, ele não terá uma versão criado para e retornará uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="c7c74-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7c74-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7c74-112">Requirements</span></span>  
 <span data-ttu-id="c7c74-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7c74-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7c74-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c7c74-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7c74-115">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c7c74-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7c74-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7c74-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c74-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7c74-117">See Also</span></span>  
 [<span data-ttu-id="c7c74-118">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="c7c74-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="c7c74-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="c7c74-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
