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
ms.openlocfilehash: 7c6adcbcfe64f63048078b4ccba6727a58531033
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008099"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="4936c-102">Método IMetaDataAssemblyEmit::SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="4936c-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="4936c-103">Modifica a estrutura de `Assembly` metadados especificada.</span><span class="sxs-lookup"><span data-stu-id="4936c-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4936c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4936c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="4936c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4936c-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="4936c-106">no O token de metadados que especifica a `Assembly` estrutura de metadados a ser modificada.</span><span class="sxs-lookup"><span data-stu-id="4936c-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="4936c-107">no Um ponteiro para a chave pública do Publicador do assembly.</span><span class="sxs-lookup"><span data-stu-id="4936c-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="4936c-108">no O tamanho em bytes de `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="4936c-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="4936c-109">no O identificador do algoritmo de hash usado para fazer o hash dos arquivos de assembly.</span><span class="sxs-lookup"><span data-stu-id="4936c-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="4936c-110">no O nome de texto legível por humanos do assembly.</span><span class="sxs-lookup"><span data-stu-id="4936c-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="4936c-111">no Um ponteiro para o ASSEMBLYMETADATA que contém informações de versão, plataforma e localidade para o assembly.</span><span class="sxs-lookup"><span data-stu-id="4936c-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="4936c-112">no Uma combinação de bits de valores [AssemblyFlags](assemblyflags-enumeration.md) que especifica vários atributos do assembly.</span><span class="sxs-lookup"><span data-stu-id="4936c-112">[in] A bitwise combination of [AssemblyFlags](assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4936c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="4936c-113">Remarks</span></span>  
 <span data-ttu-id="4936c-114">Para criar uma `Assembly` estrutura de metadados, use o método [IMetaDataAssemblyEmit::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4936c-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4936c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4936c-115">Requirements</span></span>  
 <span data-ttu-id="4936c-116">**Plataforma:** Consulte [requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4936c-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4936c-117">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4936c-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4936c-118">**Biblioteca:** Usado como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4936c-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4936c-119">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4936c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4936c-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="4936c-120">See also</span></span>

- [<span data-ttu-id="4936c-121">Interface IMetaDataAssemblyEmit</span><span class="sxs-lookup"><span data-stu-id="4936c-121">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
