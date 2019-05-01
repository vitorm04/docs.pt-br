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
ms.openlocfilehash: a01b4203145f6ffee4e3a11a3526f0b83e3dc741
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042517"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="dac68-102">Método IMetaDataImport2::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="dac68-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="dac68-103">Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.</span><span class="sxs-lookup"><span data-stu-id="dac68-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac68-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dac68-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dac68-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dac68-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="dac68-106">[out] Uma matriz para armazenar a cadeia de caracteres que especifica a versão.</span><span class="sxs-lookup"><span data-stu-id="dac68-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="dac68-107">[in] O tamanho, em caracteres largos, da `pwzBuf` matriz.</span><span class="sxs-lookup"><span data-stu-id="dac68-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="dac68-108">[out] O número de caracteres largos, incluindo um terminador nulo, retornado no `pwzBuf` matriz.</span><span class="sxs-lookup"><span data-stu-id="dac68-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dac68-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="dac68-109">Remarks</span></span>  
 <span data-ttu-id="dac68-110">O `GetVersionString` método obtém a versão criada do escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="dac68-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="dac68-111">Se o escopo nunca tiver sido salvo, ele não terá uma versão criada para e uma cadeia de caracteres vazia será retornada.</span><span class="sxs-lookup"><span data-stu-id="dac68-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac68-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dac68-112">Requirements</span></span>  
 <span data-ttu-id="dac68-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dac68-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dac68-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dac68-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dac68-115">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="dac68-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dac68-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dac68-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac68-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dac68-117">See also</span></span>

- [<span data-ttu-id="dac68-118">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="dac68-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="dac68-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="dac68-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
