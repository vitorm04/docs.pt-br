---
title: Função CreateHistoryReader
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e9c9866ee5ee3076d144dc732286ee008cd78c4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487230"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="ac319-102">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="ac319-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="ac319-103">Cria um leitor de histórico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ac319-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac319-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ac319-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac319-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ac319-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="ac319-106">[in] O caminho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="ac319-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="ac319-107">[out] Após a conclusão bem-sucedida, contém um ponteiro para o leitor de histórico.</span><span class="sxs-lookup"><span data-stu-id="ac319-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac319-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ac319-108">Return Value</span></span>  
 <span data-ttu-id="ac319-109">Esse método retorna códigos de erro padrão COM conforme definido em Winerror. H, além dos valores descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="ac319-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="ac319-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="ac319-110">Return code</span></span>|<span data-ttu-id="ac319-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ac319-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ac319-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ac319-112">S_OK</span></span>|<span data-ttu-id="ac319-113">Indica que o método concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="ac319-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="ac319-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ac319-114">E_INVALIDARG</span></span>|<span data-ttu-id="ac319-115">Indica que `wzFilePath` ou `ppHistoryReader` são definidos como uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="ac319-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac319-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ac319-116">Requirements</span></span>  
 <span data-ttu-id="ac319-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac319-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac319-118">**Biblioteca:** Fusion</span><span class="sxs-lookup"><span data-stu-id="ac319-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="ac319-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac319-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac319-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ac319-120">See also</span></span>
- [<span data-ttu-id="ac319-121">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="ac319-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
