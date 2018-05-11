---
title: Método IMetaDataAssemblyEmit::SetAssemblyProps
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f8132296035e9ddcdcad76d93ed05358beb0b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="7bf50-102">Método IMetaDataAssemblyEmit::SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="7bf50-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="7bf50-103">Modifica especificado `Assembly` estrutura de metadados.</span><span class="sxs-lookup"><span data-stu-id="7bf50-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf50-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bf50-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bf50-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bf50-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="7bf50-106">[in] O token de metadados que especifica o `Assembly` estrutura de metadados a ser modificado.</span><span class="sxs-lookup"><span data-stu-id="7bf50-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="7bf50-107">[in] Um ponteiro para a chave pública do publicador do assembly.</span><span class="sxs-lookup"><span data-stu-id="7bf50-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="7bf50-108">[in] O tamanho em bytes do `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="7bf50-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="7bf50-109">[in] O identificador para o algoritmo de hash usado para os arquivos de assembly de hash.</span><span class="sxs-lookup"><span data-stu-id="7bf50-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="7bf50-110">[in] O nome de texto legível do assembly.</span><span class="sxs-lookup"><span data-stu-id="7bf50-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="7bf50-111">[in] Um ponteiro para o ASSEMBLYMETADATA que contém informações de localidade, plataforma e versão do assembly.</span><span class="sxs-lookup"><span data-stu-id="7bf50-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="7bf50-112">[in] Uma combinação bit a bit de [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) valores que especificam vários atributos do assembly.</span><span class="sxs-lookup"><span data-stu-id="7bf50-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bf50-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bf50-113">Remarks</span></span>  
 <span data-ttu-id="7bf50-114">Para criar um `Assembly` estrutura de metadados, use o [: Defineassembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="7bf50-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf50-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bf50-115">Requirements</span></span>  
 <span data-ttu-id="7bf50-116">**Plataforma:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf50-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf50-117">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7bf50-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7bf50-118">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7bf50-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7bf50-119">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf50-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf50-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bf50-120">See Also</span></span>  
 [<span data-ttu-id="7bf50-121">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="7bf50-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
