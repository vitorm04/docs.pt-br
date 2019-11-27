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
ms.openlocfilehash: 0c9f667edf30feb23e1cdaa28950503283fce42e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445230"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="b22bc-102">Método IMetaDataImport2::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="b22bc-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="b22bc-103">Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.</span><span class="sxs-lookup"><span data-stu-id="b22bc-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b22bc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b22bc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b22bc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b22bc-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="b22bc-106">fora Uma matriz para armazenar a cadeia de caracteres que especifica a versão.</span><span class="sxs-lookup"><span data-stu-id="b22bc-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="b22bc-107">no O tamanho, em caracteres largos, da matriz de `pwzBuf`.</span><span class="sxs-lookup"><span data-stu-id="b22bc-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="b22bc-108">fora O número de caracteres largos, incluindo um terminador nulo, retornado na matriz de `pwzBuf`.</span><span class="sxs-lookup"><span data-stu-id="b22bc-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b22bc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b22bc-109">Remarks</span></span>  
 <span data-ttu-id="b22bc-110">O método `GetVersionString` Obtém a versão interna do escopo de metadados atual.</span><span class="sxs-lookup"><span data-stu-id="b22bc-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="b22bc-111">Se o escopo nunca tiver sido salvo, ele não terá uma versão interna e uma cadeia de caracteres vazia será retornada.</span><span class="sxs-lookup"><span data-stu-id="b22bc-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b22bc-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b22bc-112">Requirements</span></span>  
 <span data-ttu-id="b22bc-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b22bc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b22bc-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b22bc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b22bc-115">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b22bc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b22bc-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b22bc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b22bc-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b22bc-117">See also</span></span>

- [<span data-ttu-id="b22bc-118">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b22bc-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="b22bc-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b22bc-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
