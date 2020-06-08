---
title: Método IMetaDataImport::GetParamForMethodIndex
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
ms.openlocfilehash: 21a83e404405ca9cfe301b76cb1e1591d69e747c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491115"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="f73c5-102">Método IMetaDataImport::GetParamForMethodIndex</span><span class="sxs-lookup"><span data-stu-id="f73c5-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="f73c5-103">Obtém o token que representa um parâmetro especificado do método representado pelo token MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="f73c5-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f73c5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f73c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f73c5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f73c5-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="f73c5-106">no Um token que representa o método para o qual retornar o token de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f73c5-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="f73c5-107">no A posição ordinal na lista de parâmetros na qual o parâmetro solicitado ocorre.</span><span class="sxs-lookup"><span data-stu-id="f73c5-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="f73c5-108">Os parâmetros são numerados a partir de um, com o valor de retorno do método na posição zero.</span><span class="sxs-lookup"><span data-stu-id="f73c5-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="f73c5-109">fora Um ponteiro para um token ParamDef que representa o parâmetro solicitado.</span><span class="sxs-lookup"><span data-stu-id="f73c5-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f73c5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f73c5-110">Requirements</span></span>  
 <span data-ttu-id="f73c5-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f73c5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f73c5-112">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f73c5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f73c5-113">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f73c5-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f73c5-114">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f73c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f73c5-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="f73c5-115">See also</span></span>

- [<span data-ttu-id="f73c5-116">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="f73c5-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f73c5-117">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="f73c5-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
