---
title: "Função CreateHistoryReader"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateHistoryReader
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateHistoryReader
helpviewer_keywords: CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f4b09f592a27b7d3d25b2dbe13be7e261023bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="4adf6-102">Função CreateHistoryReader</span><span class="sxs-lookup"><span data-stu-id="4adf6-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="4adf6-103">Cria um leitor de histórico para o arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="4adf6-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4adf6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4adf6-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4adf6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4adf6-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="4adf6-106">[in] O caminho do arquivo.</span><span class="sxs-lookup"><span data-stu-id="4adf6-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="4adf6-107">[out] Após a conclusão bem-sucedida, contém um ponteiro para o leitor de histórico.</span><span class="sxs-lookup"><span data-stu-id="4adf6-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4adf6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4adf6-108">Return Value</span></span>  
 <span data-ttu-id="4adf6-109">Esse método retorna códigos de erro padrão COM conforme definido no Winerror. H, além dos valores descritos na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="4adf6-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="4adf6-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="4adf6-110">Return code</span></span>|<span data-ttu-id="4adf6-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="4adf6-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4adf6-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4adf6-112">S_OK</span></span>|<span data-ttu-id="4adf6-113">Indica que o método foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="4adf6-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="4adf6-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4adf6-114">E_INVALIDARG</span></span>|<span data-ttu-id="4adf6-115">Indica que `wzFilePath` ou `ppHistoryReader` são definidos como uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="4adf6-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4adf6-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4adf6-116">Requirements</span></span>  
 <span data-ttu-id="4adf6-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4adf6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4adf6-118">**Biblioteca:** Fusion</span><span class="sxs-lookup"><span data-stu-id="4adf6-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="4adf6-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4adf6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adf6-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4adf6-120">See Also</span></span>  
 [<span data-ttu-id="4adf6-121">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="4adf6-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
