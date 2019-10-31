---
title: Função StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095008"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="782b4-102">Função StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="782b4-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="782b4-103">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="782b4-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="782b4-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="782b4-104">This function has been deprecated.</span></span> <span data-ttu-id="782b4-105">Em vez disso, use o método [ICLRStrongName:: StrongNameGetBlob](../hosting/iclrstrongname-strongnamegetblob-method.md) .</span><span class="sxs-lookup"><span data-stu-id="782b4-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="782b4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="782b4-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="782b4-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="782b4-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="782b4-108">no Um caminho válido para o arquivo executável a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="782b4-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="782b4-109">no O buffer no qual carregar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="782b4-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="782b4-110">[entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="782b4-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="782b4-111">No retorno, o tamanho real, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="782b4-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="782b4-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="782b4-112">Return Value</span></span>  
 <span data-ttu-id="782b4-113">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="782b4-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="782b4-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="782b4-114">Remarks</span></span>  
 <span data-ttu-id="782b4-115">Se a função `StrongNameGetBlob` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="782b4-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="782b4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="782b4-116">Requirements</span></span>  
 <span data-ttu-id="782b4-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="782b4-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="782b4-118">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="782b4-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="782b4-119">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="782b4-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="782b4-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="782b4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782b4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="782b4-121">See also</span></span>

- [<span data-ttu-id="782b4-122">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="782b4-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="782b4-123">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="782b4-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="782b4-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="782b4-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
